<template>
  <el-container style="max-width:900px;margin:30px auto;padding:0 16px">
    <el-page-header content="扣叮 QRding｜纯前端二维码生成器" />
    <el-row :gutter="20" style="margin-top:20px">
      <!-- 左侧表单 -->
      <el-col :span="14">
        <el-card shadow="hover">
          <el-form label-width="100px">
            <el-form-item label="模板类型">
              <el-select v-model="form.type" @change="onChangeTemplate">
                <el-option label="普通文本" value="text"/>
                <el-option label="URL链接" value="url"/>
                <el-option label="WiFi信息" value="wifi"/>
                <el-option label="vCard联系人" value="vcard"/>
              </el-select>
            </el-form-item>

            <!-- 文本/URL -->
            <el-form-item label="内容" v-if="form.type === 'text' || form.type === 'url'">
              <el-input v-model="form.content" :type="form.type==='text'?'textarea':'input'" rows="3" placeholder="输入二维码内容"/>
            </el-form-item>

            <!-- WiFi -->
            <template v-if="form.type === 'wifi'">
              <el-form-item label="WiFi名称">
                <el-input v-model="form.wifi.ssid" placeholder="WiFi SSID"/>
              </el-form-item>
              <el-form-item label="WiFi密码">
                <el-input v-model="form.wifi.pwd"/>
              </el-form-item>
            </template>

            <!-- vCard -->
            <template v-if="form.type === 'vcard'">
              <el-form-item label="姓名">
                <el-input v-model="form.vcard.name"/>
              </el-form-item>
              <el-form-item label="电话">
                <el-input v-model="form.vcard.tel"/>
              </el-form-item>
              <el-form-item label="邮箱">
                <el-input v-model="form.vcard.email"/>
              </el-form-item>
            </template>

            <el-divider />

            <!-- 样式参数 -->
            <el-form-item label="尺寸(px)">
              <el-input-number v-model.number="option.width" :min="100" :max="1000"/>
            </el-form-item>
            <el-form-item label="纠错级别">
              <el-select v-model="option.level">
                <el-option label="L 低纠错" value="L"/>
                <el-option label="M" value="M"/>
                <el-option label="Q" value="Q"/>
                <el-option label="H 高纠错(推荐放Logo)" value="H"/>
              </el-select>
            </el-form-item>
            <el-form-item label="前景色">
              <el-color-picker v-model="option.color"/>
            </el-form-item>
            <el-form-item label="背景色">
              <el-color-picker v-model="option.bgColor"/>
            </el-form-item>

            <!-- Logo上传 -->
            <el-form-item label="中心Logo">
              <el-upload
                :auto-upload="false"
                :file-list="logoFileList"
                list-type="picture-card"
                :limit="1"
                :on-change="handleLogoChange"
                :on-remove="handleLogoRemove"
              >
                <el-icon><Plus /></el-icon>
              </el-upload>
              <div style="color:#999;font-size:12px">建议PNG透明图，高纠错H模式</div>
            </el-form-item>

            <el-form-item>
              <el-button type="primary" @click="generateQr">生成二维码</el-button>
              <el-button @click="clearAll">清空</el-button>
            </el-form-item>
          </el-form>
        </el-card>
      </el-col>

      <!-- 右侧预览 & 下载 -->
      <el-col :span="10">
        <el-card shadow="hover">
          <template #header>
            <div>预览</div>
          </template>
          <div style="text-align:center">
            <canvas ref="qrCanvasRef" v-if="qrDataUrl" style="max-width:100%"></canvas>
            <div v-else style="padding:40px 0;color:#999">生成后在此预览</div>
          </div>
          <el-divider />
          <el-space wrap>
            <el-button type="success" @click="downloadPng" icon="Download">下载PNG</el-button>
            <el-button type="info" @click="downloadSvg" icon="Document">导出SVG</el-button>
          </el-space>
        </el-card>

        <!-- 本地历史记录 -->
        <el-card shadow="hover" style="margin-top:20px">
          <template #header>
            <div style="display:flex;justify-content:space-between">
              <span>本地历史记录</span>
              <el-button size="small" type="danger" @click="clearHistory">清空全部</el-button>
            </div>
          </template>
          <el-scrollbar height="240px">
            <el-list :data="historyList">
              <el-list-item v-for="(item,idx) in historyList" :key="idx">
                <div style="display:flex;justify-content:space-between;align-items:center">
                  <span style="font-size:13px;word-break:break-all">{{item.text}}</span>
                  <el-button size="small" @click="loadHistory(item)">载入</el-button>
                </div>
              </el-list-item>
              <el-empty v-if="historyList.length===0" description="暂无历史"/>
            </el-list>
          </el-scrollbar>
        </el-card>
      </el-col>
    </el-row>
  </el-container>
</template>

<script setup>
import { ref, reactive, onMounted } from 'vue'
import QRCode from 'qrcode'
import { ElMessage } from 'element-plus'
import { Plus, Download, Document } from '@element-plus/icons-vue'

const qrCanvasRef = ref(null)
const qrDataUrl = ref('')
const logoImg = ref(null)
const logoFileList = ref([])

const form = reactive({
  type: 'url',
  content: '',
  wifi: { ssid: '', pwd: '' },
  vcard: { name: '', tel: '', email: '' }
})

const option = reactive({
  width: 360,
  level: 'H',
  color: '#000000',
  bgColor: '#ffffff'
})

// 历史记录 localStorage
const historyList = ref([])
const STORAGE_KEY = 'qrding_history'

// 读取本地历史
const loadHistoryStorage = () => {
  const raw = localStorage.getItem(STORAGE_KEY)
  if(raw) historyList.value = JSON.parse(raw)
}
// 保存历史
const saveHistoryStorage = () => {
  localStorage.setItem(STORAGE_KEY, JSON.stringify(historyList.value))
}
// 新增一条历史
const addHistoryItem = (text) => {
  const exist = historyList.value.find(x=>x.text === text)
  if(!exist){
    historyList.value.unshift({ text, time: Date.now() })
    if(historyList.value.length > 20) historyList.value.pop()
    saveHistoryStorage()
  }
}
// 载入历史记录到表单
const loadHistory = (item) => {
  form.content = item.text
  ElMessage.success('已载入')
}
// 清空历史
const clearHistory = () => {
  historyList.value = []
  localStorage.removeItem(STORAGE_KEY)
  ElMessage.success('历史已清空')
}

// 切换模板清空二维码
const onChangeTemplate = () => {
  qrDataUrl.value = ''
}

// 组装QR标准文本
function buildQrText(){
  switch(form.type){
    case 'url':
    case 'text':
      return form.content
    case 'wifi':
      return `WIFI:S:${form.wifi.ssid};P:${form.wifi.pwd};;`
    case 'vcard':
      return `BEGIN:VCARD
VERSION:3.0
N:${form.vcard.name}
TEL:${form.vcard.tel}
EMAIL:${form.vcard.email}
END:VCARD`
    default: return ''
  }
}

// Logo上传处理
const handleLogoChange = (file) => {
  const reader = new FileReader()
  reader.onload = e => {
    const img = new Image()
    img.src = e.target.result
    logoImg.value = img
  }
  reader.readAsDataURL(file.raw)
}
const handleLogoRemove = () => {
  logoImg.value = null
}

// 生成二维码（带Logo叠加Canvas）
const generateQr = async () => {
  const text = buildQrText()
  if(!text) return ElMessage.warning('二维码内容不能为空')
  try{
    const canvas = qrCanvasRef.value
    await QRCode.toCanvas(canvas, text, {
      width: option.width,
      margin:2,
      errorCorrectionLevel: option.level,
      color:{
        dark: option.color,
        light: option.bgColor
      }
    })
    // 叠加中心Logo
    if(logoImg.value){
      const ctx = canvas.getContext('2d')
      const logoSize = option.width * 0.22
      const x = (option.width - logoSize)/2
      const y = (option.width - logoSize)/2
      ctx.drawImage(logoImg.value, x, y, logoSize, logoSize)
    }
    qrDataUrl.value = canvas.toDataURL('image/png')
    addHistoryItem(text)
    ElMessage.success('生成成功')
  }catch(err){
    console.error(err)
    ElMessage.error('生成失败')
  }
}

// 下载PNG
const downloadPng = () => {
  if(!qrDataUrl.value) return ElMessage.warning('请先生成二维码')
  const a = document.createElement('a')
  a.href = qrDataUrl.value
  a.download = 'qrding.png'
  a.click()
}

// 导出SVG
const downloadSvg = async () => {
  const text = buildQrText()
  if(!text) return ElMessage.warning('请先生成二维码')
  const svgStr = await QRCode.toString(text, {
    type:'svg',
    width: option.width,
    errorCorrectionLevel: option.level,
    color:{ dark: option.color, light: option.bgColor }
  })
  const blob = new Blob([svgStr], {type:'image/svg+xml'})
  const url = URL.createObjectURL(blob)
  const a = document.createElement('a')
  a.href = url
  a.download = 'qrding.svg'
  a.click()
  URL.revokeObjectURL(url)
}

const clearAll = () => {
  form.content = ''
  form.wifi.ssid = ''
  form.wifi.pwd = ''
  form.vcard.name = ''
  form.vcard.tel = ''
  form.vcard.email = ''
  qrDataUrl.value = ''
  logoImg.value = null
  logoFileList.value = []
}

onMounted(()=>{
  loadHistoryStorage()
})
</script>
