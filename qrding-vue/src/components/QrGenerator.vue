<template>
  <div class="qp-page">
    <header class="qp-head">
      <div class="qp-wrap">
        <div class="qp-brandline">
          <span class="qp-logo" aria-hidden="true">
            <img src="data:image/png;base64,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" alt="" width="40" height="40">
          </span>
          <h1>二维码美化</h1>
          <span class="qp-tag">纯前端 · 不上传</span>
        </div>
        <p class="qp-lede">
          换配色、改码点与码眼样式、加 Logo、加底部文字，全部在浏览器本地绘制；导出 PNG 与 SVG，断网可用。
        </p>
      </div>
    </header>

    <main class="qp-wrap qp-main">
      <div class="qp-col">
      <!-- 预览 -->
      <section class="qp-card qp-preview">
        <div class="qp-card-head">
          <span class="qp-card-title">实时预览</span>
          <span class="qp-meta" :class="{ warn: contrastWarn }">{{ meta }}</span>
        </div>
        <div class="qp-stage" :class="{ checker: transparentBg }">
          <canvas ref="canvasRef" class="qp-canvas"></canvas>
        </div>
        <div class="qp-actions">
          <el-button type="primary" :disabled="!ready" @click="downloadPng">下载 PNG</el-button>
          <el-button :disabled="!ready" @click="downloadSvg">导出 SVG</el-button>
          <el-button :disabled="!ready" @click="copyImage">复制图片</el-button>
        </div>
        <p class="qp-hint" v-if="contrastWarn">
          前景与背景对比度偏低，部分扫码器可能识别困难。
        </p>
        <p class="qp-hint" v-if="gapWarn">
          码点留缝 {{ Math.round((1 - opt.dotScale) * 100) }}%，密集内容可能漏读，建议把码点缩放调到 94% 以上。
        </p>
      </section>

      <!-- 样式模板 -->
      <section class="qp-card">
        <div class="qp-card-head">
          <span class="qp-card-title">我的样式模板</span>
          <button class="qp-link" type="button" :disabled="!ready" @click="saveTemplate">保存当前样式</button>
        </div>
        <div v-if="!templates.length" class="qp-empty">还没有模板，调好样式后点「保存当前样式」</div>
        <ul v-else class="qp-tpl-list">
          <li v-for="t in templates" :key="t.id">
            <span class="qp-tpl-dot" :style="{ background: t.preview }"></span>
            <span class="qp-tpl-name">{{ t.name }}</span>
            <button class="qp-link" type="button" @click="applyTemplate(t)">套用</button>
            <button class="qp-link danger" type="button" @click="removeTemplate(t.id)">删除</button>
          </li>
        </ul>
      </section>

      <!-- 历史 -->
      <section class="qp-card">
        <div class="qp-card-head">
          <span class="qp-card-title">最近生成</span>
          <button class="qp-link danger" type="button" @click="clearHistory">清空</button>
        </div>
        <div v-if="!history.length" class="qp-empty">还没有记录，生成一次就会留在这里</div>
        <ul v-else class="qp-tpl-list">
          <li v-for="(h, i) in history" :key="i">
            <span class="qp-tpl-name mono">{{ h.label }}</span>
            <button class="qp-link" type="button" @click="loadHistory(h)">载入</button>
          </li>
        </ul>
      </section>
      </div>

      <!-- 设置 -->
      <section class="qp-card qp-settings">
        <div class="qp-card-head">
          <span class="qp-card-title">内容与样式</span>
          <button class="qp-link" type="button" @click="resetStyle">重置样式</button>
        </div>

        <div class="qp-seg qp-type-seg">
          <button
            v-for="t in typeOptions"
            :key="t.value"
            type="button"
            :class="{ active: form.type === t.value }"
            @click="form.type = t.value"
          >{{ t.label }}</button>
        </div>

        <div v-if="form.type === 'text' || form.type === 'url'" class="qp-field">
          <label class="qp-label">
            内容
            <span class="qp-tip">{{ form.type === 'url' ? '网址会按原样编码' : '任意文字，支持中文' }}</span>
          </label>
          <el-input
            v-model="form.content"
            :type="form.type === 'text' ? 'textarea' : 'text'"
            :rows="4"
            :placeholder="form.type === 'url' ? 'https://example.com' : '设备编号 A-2207，扫码登记'"
          />
        </div>

        <template v-if="form.type === 'wifi'">
          <div class="qp-field">
            <label class="qp-label">网络名称 SSID</label>
            <el-input v-model="form.wifi.ssid" placeholder="Office-5G" />
          </div>
          <div class="qp-row2">
            <div class="qp-field">
              <label class="qp-label">密码</label>
              <el-input v-model="form.wifi.pwd" placeholder="留空表示无密码" />
            </div>
            <div class="qp-field">
              <label class="qp-label">加密方式</label>
              <el-select v-model="form.wifi.enc">
                <el-option label="WPA / WPA2" value="WPA" />
                <el-option label="WEP" value="WEP" />
                <el-option label="无密码" value="nopass" />
              </el-select>
            </div>
          </div>
          <el-checkbox v-model="form.wifi.hidden" label="隐藏网络（不广播 SSID）" />
        </template>

        <template v-if="form.type === 'vcard'">
          <div class="qp-row2">
            <div class="qp-field">
              <label class="qp-label">姓名</label>
              <el-input v-model="form.vcard.name" placeholder="张伟" />
            </div>
            <div class="qp-field">
              <label class="qp-label">公司</label>
              <el-input v-model="form.vcard.org" placeholder="码叮科技" />
            </div>
          </div>
          <div class="qp-row2">
            <div class="qp-field">
              <label class="qp-label">电话</label>
              <el-input v-model="form.vcard.tel" placeholder="13800000000" />
            </div>
            <div class="qp-field">
              <label class="qp-label">邮箱</label>
              <el-input v-model="form.vcard.email" placeholder="hi@example.com" />
            </div>
          </div>
          <div class="qp-field">
            <label class="qp-label">网址</label>
            <el-input v-model="form.vcard.url" placeholder="https://example.com" />
          </div>
        </template>

        <div class="qp-section">输出</div>
        <div class="qp-row2">
          <div class="qp-field">
            <label class="qp-label">纠错等级</label>
            <el-select v-model="opt.ecc">
              <el-option label="L 7%" value="L" />
              <el-option label="M 15%" value="M" />
              <el-option label="Q 25%" value="Q" />
              <el-option label="H 30%（放 Logo 建议）" value="H" />
            </el-select>
          </div>
          <div class="qp-field">
            <label class="qp-label">导出尺寸</label>
            <el-select v-model.number="opt.size">
              <el-option label="512 × 512" :value="512" />
              <el-option label="1024 × 1024" :value="1024" />
              <el-option label="1536 × 1536" :value="1536" />
            </el-select>
          </div>
        </div>

        <div class="qp-section">颜色</div>
        <div class="qp-row2">
          <div class="qp-field">
            <label class="qp-label">填充方式</label>
            <el-select v-model="opt.fillMode">
              <el-option label="纯色" value="solid" />
              <el-option label="渐变" value="gradient" />
            </el-select>
          </div>
          <div class="qp-field" v-if="opt.fillMode === 'gradient'">
            <label class="qp-label">渐变方向</label>
            <el-select v-model="opt.gradientDir">
              <el-option label="斜向" value="diagonal" />
              <el-option label="纵向" value="vertical" />
              <el-option label="横向" value="horizontal" />
              <el-option label="径向" value="radial" />
            </el-select>
          </div>
        </div>

        <div class="qp-swatches">
          <label class="qp-swatch">
            <el-color-picker v-model="opt.colorA" size="small" />
            <span>{{ opt.fillMode === 'gradient' ? '主色' : '前景' }}</span>
          </label>
          <label class="qp-swatch" v-if="opt.fillMode === 'gradient'">
            <el-color-picker v-model="opt.colorB" size="small" />
            <span>辅色</span>
          </label>
          <label class="qp-swatch">
            <el-color-picker v-model="opt.bgColor" size="small" :disabled="opt.transparentBg" />
            <span>{{ opt.transparentBg ? '背景透明' : '背景' }}</span>
          </label>
          <label class="qp-swatch" v-if="opt.customEyeColor">
            <el-color-picker v-model="opt.eyeColor" size="small" />
            <span>码眼色</span>
          </label>
        </div>

        <div class="qp-switches">
          <el-checkbox v-model="opt.transparentBg" label="背景透明" />
          <el-checkbox v-model="opt.customEyeColor" label="码眼独立配色" />
          <el-checkbox v-model="opt.invert" label="反色（浅码深底）" />
        </div>

        <div class="qp-section">形状</div>
        <div class="qp-field">
          <label class="qp-label">码点样式</label>
          <div class="qp-seg">
            <button
              v-for="o in dotOptions"
              :key="o.value"
              type="button"
              :class="{ active: opt.dotStyle === o.value }"
              @click="opt.dotStyle = o.value"
            >{{ o.label }}</button>
          </div>
        </div>
        <div class="qp-field">
          <label class="qp-label">码眼样式</label>
          <div class="qp-seg">
            <button
              v-for="o in eyeOptions"
              :key="o.value"
              type="button"
              :class="{ active: opt.eyeStyle === o.value }"
              @click="opt.eyeStyle = o.value"
            >{{ o.label }}</button>
          </div>
        </div>
        <div class="qp-row2">
          <div class="qp-field">
            <label class="qp-label">静区（留白）</label>
            <el-select v-model.number="opt.margin">
              <el-option v-for="m in [0, 1, 2, 3, 4, 6, 8]" :key="m" :label="`${m} 个模块`" :value="m" />
            </el-select>
          </div>
          <div class="qp-field">
            <label class="qp-label">码点缩放 <span class="qp-tip">{{ Math.round(opt.dotScale * 100) }}%</span></label>
            <el-slider v-model="opt.dotScale" :min="0.6" :max="1" :step="0.02" :show-tooltip="false" />
          </div>
        </div>

        <div class="qp-section">中心 Logo</div>
        <div class="qp-logo-row">
          <label class="qp-upload">
            <input type="file" accept="image/*" @change="onLogoPick" />
            <span>选择图片</span>
          </label>
          <button v-if="logoDataUrl" class="qp-link" type="button" @click="clearLogo">移除</button>
          <span class="qp-tip">{{ logoDataUrl ? '已添加 Logo' : 'PNG / JPG / WebP，建议正方形' }}</span>
        </div>
        <template v-if="logoDataUrl">
          <div class="qp-row2">
            <div class="qp-field">
              <label class="qp-label">Logo 大小 <span class="qp-tip">{{ Math.round(opt.logoRatio * 100) }}%</span></label>
              <el-slider v-model="opt.logoRatio" :min="0.1" :max="0.3" :step="0.01" :show-tooltip="false" />
            </div>
            <div class="qp-field">
              <label class="qp-label">底板</label>
              <el-checkbox v-model="opt.logoPlate" label="白色底板" />
            </div>
          </div>
        </template>

        <div class="qp-section">底部文字</div>
        <el-input v-model="opt.caption" maxlength="24" show-word-limit placeholder="例如：扫码关注码叮（留空则不显示）" />
      </section>
    </main>

    <footer class="qp-foot">
      <div class="qp-wrap">
        二维码在浏览器本地编码与绘制，内容与图片不上传服务器；历史与模板只存在本机 localStorage。
        Logo 建议不超过二维码面积的 30%，并保持 H 级纠错。
      </div>
    </footer>
  </div>
</template>

<script setup>
import { computed, onMounted, reactive, ref, watch, nextTick } from 'vue'
import QRCode from 'qrcode'
import { ElMessage } from 'element-plus'

/* ===== 内容模板 ===== */
const typeOptions = [
  { value: 'text', label: '文本' },
  { value: 'url', label: '网址' },
  { value: 'wifi', label: 'Wi-Fi' },
  { value: 'vcard', label: '名片' }
]

const form = reactive({
  type: 'url',
  content: 'https://qrding.cn/',
  wifi: { ssid: '', pwd: '', enc: 'WPA', hidden: false },
  vcard: { name: '', org: '', tel: '', email: '', url: '' }
})

const dotOptions = [
  { value: 'square', label: '方块' },
  { value: 'rounded', label: '圆角' },
  { value: 'circle', label: '圆点' },
  { value: 'diamond', label: '菱形' }
]
const eyeOptions = [
  { value: 'square', label: '方块' },
  { value: 'rounded', label: '圆角' },
  { value: 'circle', label: '圆形' }
]

/* ===== 样式参数 ===== */
const opt = reactive({
  ecc: 'M',
  size: 512,
  margin: 4,
  fillMode: 'solid',
  gradientDir: 'diagonal',
  colorA: '#0066ff',
  colorB: '#001a66',
  bgColor: '#ffffff',
  transparentBg: false,
  dotStyle: 'rounded',
  eyeStyle: 'rounded',
  dotScale: 0.96,
  customEyeColor: false,
  eyeColor: '#0f172a',
  invert: false,
  logoRatio: 0.16,
  logoPlate: true,
  caption: ''
})

const gapWarn = computed(
  () => ['square', 'rounded'].includes(opt.dotStyle) && opt.dotScale < 0.94
)

const canvasRef = ref(null)
const ready = ref(false)
const meta = ref('')
const contrastWarn = ref(false)
const logoImg = ref(null)
const logoDataUrl = ref('')

/* ===== 内容组装 ===== */
function escWifi(v) {
  return String(v).replace(/([\\;,:"])/g, '\\$1')
}

function buildText() {
  switch (form.type) {
    case 'text':
    case 'url':
      return String(form.content || '').trim()
    case 'wifi': {
      const ssid = String(form.wifi.ssid || '').trim()
      if (!ssid) return ''
      let out = `WIFI:T:${form.wifi.enc};S:${escWifi(ssid)};`
      if (form.wifi.enc !== 'nopass') out += `P:${escWifi(form.wifi.pwd)};`
      if (form.wifi.hidden) out += 'H:true;'
      return out + ';'
    }
    case 'vcard': {
      const name = String(form.vcard.name || '').trim()
      const tel = String(form.vcard.tel || '').trim()
      const email = String(form.vcard.email || '').trim()
      if (!name && !tel && !email) return ''
      const lines = ['BEGIN:VCARD', 'VERSION:3.0', `N:${name}`, `FN:${name}`]
      if (form.vcard.org) lines.push(`ORG:${String(form.vcard.org).trim()}`)
      if (tel) lines.push(`TEL;TYPE=CELL:${tel}`)
      if (email) lines.push(`EMAIL:${email}`)
      if (form.vcard.url) lines.push(`URL:${String(form.vcard.url).trim()}`)
      lines.push('END:VCARD')
      return lines.join('\r\n')
    }
    default:
      return ''
  }
}

/* ===== 颜色工具 ===== */
function hexToRgb(hex) {
  const v = String(hex || '').replace('#', '')
  const full = v.length === 3 ? v.split('').map((c) => c + c).join('') : v.padEnd(6, '0')
  return {
    r: parseInt(full.slice(0, 2), 16) || 0,
    g: parseInt(full.slice(2, 4), 16) || 0,
    b: parseInt(full.slice(4, 6), 16) || 0
  }
}

function luminance(hex) {
  const { r, g, b } = hexToRgb(hex)
  const f = (c) => {
    const v = c / 255
    return v <= 0.03928 ? v / 12.92 : Math.pow((v + 0.055) / 1.055, 2.4)
  }
  return 0.2126 * f(r) + 0.7152 * f(g) + 0.0722 * f(b)
}

function contrastRatio(a, b) {
  const l1 = luminance(a)
  const l2 = luminance(b)
  const hi = Math.max(l1, l2)
  const lo = Math.min(l1, l2)
  return (hi + 0.05) / (lo + 0.05)
}

function moduleColor() {
  // 反色时前景用背景色，等价于「浅码深底」
  return opt.invert ? opt.bgColor : opt.colorA
}

function bgPaint() {
  return opt.invert ? opt.colorA : opt.bgColor
}

/* ===== Canvas 绘制 ===== */
function buildFill(ctx, w, h) {
  if (opt.fillMode === 'solid') return moduleColor()
  const c1 = moduleColor()
  const c2 = opt.invert ? opt.colorA : opt.colorB
  if (opt.gradientDir === 'radial') {
    const g = ctx.createRadialGradient(w / 2, h / 2, 0, w / 2, h / 2, Math.max(w, h) / 1.4)
    g.addColorStop(0, c1)
    g.addColorStop(1, c2)
    return g
  }
  const coords =
    opt.gradientDir === 'vertical'
      ? [0, 0, 0, h]
      : opt.gradientDir === 'horizontal'
        ? [0, 0, w, 0]
        : [0, 0, w, h]
  const g = ctx.createLinearGradient(...coords)
  g.addColorStop(0, c1)
  g.addColorStop(1, c2)
  return g
}

function roundRect(ctx, x, y, w, h, r) {
  const radius = Math.min(r, w / 2, h / 2)
  ctx.beginPath()
  ctx.moveTo(x + radius, y)
  ctx.lineTo(x + w - radius, y)
  ctx.quadraticCurveTo(x + w, y, x + w, y + radius)
  ctx.lineTo(x + w, y + h - radius)
  ctx.quadraticCurveTo(x + w, y + h, x + w - radius, y + h)
  ctx.lineTo(x + radius, y + h)
  ctx.quadraticCurveTo(x, y + h, x, y + h - radius)
  ctx.lineTo(x, y + radius)
  ctx.quadraticCurveTo(x, y, x + radius, y)
  ctx.closePath()
}

function drawDot(ctx, cx, cy, m, fill) {
  // 圆点/菱形铺满整格，避免相邻点留缝导致扫码器漏读
  const s = m * (opt.dotStyle === 'circle' || opt.dotStyle === 'diamond' ? 1 : opt.dotScale)
  ctx.fillStyle = fill
  if (opt.dotStyle === 'square') {
    ctx.fillRect(cx - s / 2, cy - s / 2, s, s)
    return
  }
  if (opt.dotStyle === 'circle') {
    ctx.beginPath()
    ctx.arc(cx, cy, s / 2, 0, Math.PI * 2)
    ctx.fill()
    return
  }
  if (opt.dotStyle === 'diamond') {
    const r = (m / Math.SQRT2) * 1.02
    ctx.beginPath()
    ctx.moveTo(cx, cy - r)
    ctx.lineTo(cx + r, cy)
    ctx.lineTo(cx, cy + r)
    ctx.lineTo(cx - r, cy)
    ctx.closePath()
    ctx.fill()
    return
  }
  roundRect(ctx, cx - s / 2, cy - s / 2, s, s, s * 0.32)
  ctx.fill()
}

function drawEye(ctx, x, y, m, fill, bg) {
  const outer = 7 * m
  const inner = 5 * m
  const core = 3 * m
  const style = opt.eyeStyle

  const paint = (px, py, size, r, color) => {
    ctx.fillStyle = color
    if (style === 'circle') {
      ctx.beginPath()
      ctx.arc(px + size / 2, py + size / 2, size / 2, 0, Math.PI * 2)
      ctx.fill()
    } else if (style === 'rounded') {
      roundRect(ctx, px, py, size, size, r)
      ctx.fill()
    } else {
      ctx.fillRect(px, py, size, size)
    }
  }

  paint(x, y, outer, style === 'rounded' ? outer * 0.26 : 0, fill)

  const inX = x + m
  const inY = y + m
  if (bg) {
    paint(inX, inY, inner, style === 'rounded' ? inner * 0.22 : 0, bg)
  } else {
    ctx.save()
    ctx.globalCompositeOperation = 'destination-out'
    if (style === 'circle') {
      ctx.beginPath()
      ctx.arc(inX + inner / 2, inY + inner / 2, inner / 2, 0, Math.PI * 2)
      ctx.fill()
    } else if (style === 'rounded') {
      roundRect(ctx, inX, inY, inner, inner, inner * 0.22)
      ctx.fill()
    } else {
      ctx.fillRect(inX, inY, inner, inner)
    }
    ctx.restore()
  }

  paint(inX + m, inY + m, core, style === 'rounded' ? core * 0.28 : 0, fill)
}

/* ===== 主渲染 ===== */
let lastQr = null

function render() {
  const canvas = canvasRef.value
  if (!canvas) return
  const text = buildText()

  if (!text) {
    ready.value = false
    const S = opt.size
    canvas.width = S
    canvas.height = S
    const c0 = canvas.getContext('2d')
    c0.clearRect(0, 0, S, S)
    c0.fillStyle = bgPaint()
    c0.fillRect(0, 0, S, S)
    meta.value = '输入内容后自动生成'
    contrastWarn.value = false
    return
  }

  let qr
  try {
    qr = QRCode.create(text, { errorCorrectionLevel: opt.ecc })
  } catch (e) {
    ready.value = false
    lastQr = null
    meta.value = '内容超出当前纠错级别的容量上限，请缩短内容或降低纠错等级'
    return
  }

  lastQr = { qr, text }
  const n = qr.modules.size
  const pad = opt.margin
  const S = opt.size
  const m = S / (n + pad * 2)
  const capText = String(opt.caption || '').trim()
  const capH = capText ? Math.round(S * 0.11) : 0
  const H = S + capH

  canvas.width = S
  canvas.height = H
  const ctx = canvas.getContext('2d')
  ctx.clearRect(0, 0, S, H)

  const bg = opt.transparentBg ? null : bgPaint()
  if (bg) {
    ctx.fillStyle = bg
    ctx.fillRect(0, 0, S, H)
  }

  const fill = buildFill(ctx, S, S)
  const eyeFill = opt.customEyeColor ? opt.eyeColor : fill

  const isFinder = (x, y) =>
    (x < 7 && y < 7) || (x >= n - 7 && y < 7) || (x < 7 && y >= n - 7)

  for (let y = 0; y < n; y++) {
    for (let x = 0; x < n; x++) {
      if (!qr.modules.get(x, y)) continue
      if (isFinder(x, y)) continue
      drawDot(ctx, (pad + x) * m + m / 2, (pad + y) * m + m / 2, m, fill)
    }
  }

  const eyes = [
    [pad, pad],
    [pad + n - 7, pad],
    [pad, pad + n - 7]
  ]
  for (const [ex, ey] of eyes) {
    drawEye(ctx, ex * m, ey * m, m, eyeFill, bg)
  }

  // Logo
  const logo = logoImg.value
  if (logo) {
    const size = S * opt.logoRatio
    const lx = (S - size) / 2
    const ly = (S - size) / 2
    if (opt.logoPlate) {
      const padPx = size * 0.08
      ctx.fillStyle = opt.transparentBg ? '#ffffff' : bgPaint()
      roundRect(ctx, lx - padPx, ly - padPx, size + padPx * 2, size + padPx * 2, size * 0.16)
      ctx.fill()
    }
    ctx.drawImage(logo, lx, ly, size, size)
  }

  // 底部文字
  if (capText) {
    ctx.fillStyle = bg || '#ffffff'
    ctx.fillRect(0, S, S, capH)
    ctx.fillStyle = opt.customEyeColor ? opt.eyeColor : (opt.fillMode === 'solid' ? moduleColor() : opt.colorA)
    const fontSize = Math.round(capH * 0.52)
    ctx.font = `600 ${fontSize}px "PingFang SC", "Microsoft YaHei", sans-serif`
    ctx.textAlign = 'center'
    ctx.textBaseline = 'middle'
    ctx.fillText(capText, S / 2, S + capH / 2)
  }

  ready.value = true
  const ratio = contrastRatio(moduleColor(), opt.transparentBg ? '#ffffff' : bgPaint())
  contrastWarn.value = ratio < 3
  meta.value = `版本 ${qr.version} · ${n} × ${n} 模块 · 输出 ${S} × ${H} px · ${text.length} 字符`
}

/* ===== 防抖 ===== */
let timer = null
function scheduleRender() {
  clearTimeout(timer)
  timer = setTimeout(() => nextTick(render), 120)
}

watch(
  [
    () => form.type, () => form.content, () => form.wifi, () => form.vcard,
    () => opt.ecc, () => opt.size, () => opt.margin, () => opt.fillMode,
    () => opt.gradientDir, () => opt.colorA, () => opt.colorB, () => opt.bgColor,
    () => opt.transparentBg, () => opt.dotStyle, () => opt.eyeStyle, () => opt.dotScale,
    () => opt.customEyeColor, () => opt.eyeColor, () => opt.invert,
    () => opt.logoRatio, () => opt.logoPlate, () => opt.caption, logoDataUrl
  ],
  scheduleRender,
  { deep: true }
)

/* ===== Logo ===== */
function onLogoPick(e) {
  const file = e.target.files && e.target.files[0]
  if (!file) return
  if (file.size > 4 * 1024 * 1024) {
    ElMessage.error('Logo 图片请小于 4MB')
    e.target.value = ''
    return
  }
  const reader = new FileReader()
  reader.onload = () => {
    const img = new Image()
    img.onload = () => {
      logoImg.value = img
      logoDataUrl.value = String(reader.result)
    }
    img.onerror = () => ElMessage.error('Logo 解析失败')
    img.src = String(reader.result)
  }
  reader.readAsDataURL(file)
  e.target.value = ''
}

function clearLogo() {
  logoImg.value = null
  logoDataUrl.value = ''
}

/* ===== 导出 ===== */
function stamp() {
  const d = new Date()
  const z = (v) => String(v).padStart(2, '0')
  return `${d.getFullYear()}${z(d.getMonth() + 1)}${z(d.getDate())}-${z(d.getHours())}${z(d.getMinutes())}${z(d.getSeconds())}`
}

function downloadPng() {
  const canvas = canvasRef.value
  if (!canvas || !ready.value) {
    ElMessage.warning('请先输入内容')
    return
  }
  canvas.toBlob((blob) => {
    if (!blob) return
    const url = URL.createObjectURL(blob)
    const a = document.createElement('a')
    a.href = url
    a.download = `qrding-${stamp()}.png`
    a.click()
    URL.revokeObjectURL(url)
    ElMessage.success('PNG 已开始下载')
  }, 'image/png')
}

function copyImage() {
  const canvas = canvasRef.value
  if (!canvas || !ready.value) return
  if (!navigator.clipboard || !window.ClipboardItem) {
    ElMessage.warning('当前浏览器不支持复制图片，请改用下载')
    return
  }
  canvas.toBlob((blob) => {
    navigator.clipboard
      .write([new ClipboardItem({ 'image/png': blob })])
      .then(() => ElMessage.success('图片已复制到剪贴板'))
      .catch(() => ElMessage.error('复制被浏览器拒绝，请改用下载'))
  }, 'image/png')
}

/* ===== SVG 导出（与 Canvas 同一套样式语义） ===== */
function svgShape(style, x, y, size, fill, radiusFactor) {
  const num = (v) => Math.round(v * 100) / 100
  if (style === 'circle') {
    return `<circle cx="${num(x + size / 2)}" cy="${num(y + size / 2)}" r="${num(size / 2)}" fill="${fill}"/>`
  }
  if (style === 'rounded') {
    const r = num(size * (radiusFactor || 0.3))
    return `<rect x="${num(x)}" y="${num(y)}" width="${num(size)}" height="${num(size)}" rx="${r}" fill="${fill}"/>`
  }
  return `<rect x="${num(x)}" y="${num(y)}" width="${num(size)}" height="${num(size)}" fill="${fill}"/>`
}

function buildSvg() {
  if (!lastQr) return ''
  const { qr, text } = lastQr
  const n = qr.modules.size
  const pad = opt.margin
  const S = opt.size
  const m = S / (n + pad * 2)
  const capText = String(opt.caption || '').trim()
  const capH = capText ? Math.round(S * 0.11) : 0
  const H = S + capH
  const num = (v) => Math.round(v * 100) / 100

  const defs = []
  let fillRef
  if (opt.fillMode === 'gradient') {
    const c1 = moduleColor()
    const c2 = opt.invert ? opt.colorA : opt.colorB
    if (opt.gradientDir === 'radial') {
      defs.push(`<radialGradient id="g" cx="50%" cy="50%" r="70%"><stop offset="0%" stop-color="${c1}"/><stop offset="100%" stop-color="${c2}"/></radialGradient>`)
    } else {
      const coords =
        opt.gradientDir === 'vertical'
          ? 'x1="0" y1="0" x2="0" y2="1"'
          : opt.gradientDir === 'horizontal'
            ? 'x1="0" y1="0" x2="1" y2="0"'
            : 'x1="0" y1="0" x2="1" y2="1"'
      defs.push(`<linearGradient id="g" ${coords}><stop offset="0%" stop-color="${c1}"/><stop offset="100%" stop-color="${c2}"/></linearGradient>`)
    }
    fillRef = 'url(#g)'
  } else {
    fillRef = moduleColor()
  }

  const eyeFill = opt.customEyeColor ? opt.eyeColor : fillRef
  const bg = opt.transparentBg ? null : bgPaint()

  const isFinder = (x, y) =>
    (x < 7 && y < 7) || (x >= n - 7 && y < 7) || (x < 7 && y >= n - 7)

  let body = ''
  for (let y = 0; y < n; y++) {
    for (let x = 0; x < n; x++) {
      if (!qr.modules.get(x, y)) continue
      if (isFinder(x, y)) continue
      const cx = (pad + x) * m + m / 2
      const cy = (pad + y) * m + m / 2
      if (opt.dotStyle === 'diamond') {
        const r = (m / Math.SQRT2) * 1.02
        body += `<polygon points="${num(cx)},${num(cy - r)} ${num(cx + r)},${num(cy)} ${num(cx)},${num(cy + r)} ${num(cx - r)},${num(cy)}" fill="${fillRef}"/>`
      } else if (opt.dotStyle === 'circle') {
        body += `<circle cx="${num(cx)}" cy="${num(cy)}" r="${num(m / 2)}" fill="${fillRef}"/>`
      } else {
        const s = m * opt.dotScale
        body += svgShape(opt.dotStyle, cx - s / 2, cy - s / 2, s, fillRef, 0.32)
      }
    }
  }

  const eyes = [
    [pad, pad],
    [pad + n - 7, pad],
    [pad, pad + n - 7]
  ]
  eyes.forEach(([ex, ey], i) => {
    const outer = 7 * m
    const inner = 5 * m
    const core = 3 * m
    const style = opt.eyeStyle
    const rf = style === 'rounded' ? 0.26 : 0
    if (bg) {
      body += svgShape(style, ex * m, ey * m, outer, eyeFill, rf)
      body += svgShape(style, ex * m + m, ey * m + m, inner, bg, 0.22)
      body += svgShape(style, ex * m + 2 * m, ey * m + 2 * m, core, eyeFill, 0.28)
    } else {
      // 透明背景下用 mask 挖出码眼中间的空白，挖孔形状必须与码眼样式一致
      const hole = svgShape(style, ex * m + m, ey * m + m, inner, '#000', 0.22)
      defs.push(`<mask id="eye${i}"><rect x="${num(ex * m)}" y="${num(ey * m)}" width="${num(outer)}" height="${num(outer)}" fill="#fff"/>${hole}</mask>`)
      body += `<g mask="url(#eye${i})">${svgShape(style, ex * m, ey * m, outer, eyeFill, rf)}</g>`
      body += svgShape(style, ex * m + 2 * m, ey * m + 2 * m, core, eyeFill, 0.28)
    }
  })

  // Logo
  if (logoDataUrl.value) {
    const size = S * opt.logoRatio
    const lx = (S - size) / 2
    const ly = (S - size) / 2
    if (opt.logoPlate) {
      const padPx = size * 0.08
      body += `<rect x="${num(lx - padPx)}" y="${num(ly - padPx)}" width="${num(size + padPx * 2)}" height="${num(size + padPx * 2)}" rx="${num(size * 0.16)}" fill="${opt.transparentBg ? '#ffffff' : bgPaint()}"/>`
    }
    body += `<image x="${num(lx)}" y="${num(ly)}" width="${num(size)}" height="${num(size)}" href="${logoDataUrl.value}" preserveAspectRatio="xMidYMid slice"/>`
  }

  // 底部文字
  let caption = ''
  if (capText) {
    const fontSize = Math.round(capH * 0.52)
    const color = opt.customEyeColor ? opt.eyeColor : (opt.fillMode === 'solid' ? moduleColor() : opt.colorA)
    caption = `<rect x="0" y="${S}" width="${S}" height="${capH}" fill="${bg || '#ffffff'}"/>` +
      `<text x="${num(S / 2)}" y="${num(S + capH / 2)}" text-anchor="middle" dominant-baseline="middle" font-family="PingFang SC, Microsoft YaHei, sans-serif" font-weight="600" font-size="${fontSize}" fill="${color}">${capText.replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;')}</text>`
  }

  return `<?xml version="1.0" encoding="UTF-8"?>
<svg xmlns="http://www.w3.org/2000/svg" width="${S}" height="${H}" viewBox="0 0 ${S} ${H}">
${defs.length ? `<defs>${defs.join('')}</defs>` : ''}
${bg ? `<rect width="${S}" height="${H}" fill="${bg}"/>` : ''}
${body}${caption}
</svg>`
}

function downloadSvg() {
  const svg = buildSvg()
  if (!svg) {
    ElMessage.warning('请先输入内容')
    return
  }
  const blob = new Blob([svg], { type: 'image/svg+xml;charset=utf-8' })
  const url = URL.createObjectURL(blob)
  const a = document.createElement('a')
  a.href = url
  a.download = `qrding-${stamp()}.svg`
  a.click()
  URL.revokeObjectURL(url)
  ElMessage.success('SVG 已开始下载')
}

/* ===== 样式重置 ===== */
function resetStyle() {
  Object.assign(opt, {
    ecc: 'M',
    size: 512,
    margin: 4,
    fillMode: 'solid',
    gradientDir: 'diagonal',
    colorA: '#0066ff',
    colorB: '#001a66',
    bgColor: '#ffffff',
    transparentBg: false,
    dotStyle: 'rounded',
    eyeStyle: 'rounded',
    dotScale: 0.96,
    customEyeColor: false,
    eyeColor: '#0f172a',
    invert: false,
    logoRatio: 0.16,
    logoPlate: true,
    caption: ''
  })
  ElMessage.info('样式已重置')
}

/* ===== 模板 ===== */
const TPL_KEY = 'qrding_styles_v1'
const templates = ref([])

function readTemplates() {
  try {
    templates.value = JSON.parse(localStorage.getItem(TPL_KEY) || '[]')
  } catch (e) {
    templates.value = []
  }
}

function persistTemplates() {
  try {
    localStorage.setItem(TPL_KEY, JSON.stringify(templates.value))
  } catch (e) {
    ElMessage.warning('本地存储已满，模板未保存')
  }
}

function currentConfig() {
  return {
    ...JSON.parse(JSON.stringify(opt)),
    logo: logoDataUrl.value && logoDataUrl.value.length < 200000 ? logoDataUrl.value : ''
  }
}

function saveTemplate() {
  const text = buildText()
  if (!text) {
    ElMessage.warning('请先输入内容')
    return
  }
  const name = `样式 ${templates.value.length + 1}`
  const cfg = currentConfig()
  templates.value.unshift({
    id: 'tpl_' + Date.now(),
    name,
    preview: cfg.fillMode === 'gradient' ? `linear-gradient(135deg, ${cfg.colorA}, ${cfg.colorB})` : cfg.colorA,
    config: cfg,
    content: text
  })
  templates.value = templates.value.slice(0, 12)
  persistTemplates()
  ElMessage.success('已保存为模板')
}

function applyTemplate(t) {
  const c = t.config || {}
  Object.keys(opt).forEach((k) => {
    if (c[k] !== undefined) opt[k] = c[k]
  })
  if (c.logo) {
    const img = new Image()
    img.onload = () => {
      logoImg.value = img
      logoDataUrl.value = c.logo
    }
    img.src = c.logo
  } else {
    logoImg.value = null
    logoDataUrl.value = ''
  }
  if (t.content) form.content = t.content
  ElMessage.success(`已套用「${t.name}」`)
}

function removeTemplate(id) {
  templates.value = templates.value.filter((t) => t.id !== id)
  persistTemplates()
}

/* ===== 历史 ===== */
const HISTORY_KEY = 'qrding_history'
const history = ref([])

function readHistory() {
  try {
    const raw = localStorage.getItem(HISTORY_KEY)
    const list = raw ? JSON.parse(raw) : []
    history.value = list.map((h) => ({
      ...h,
      label: String(h.text || '').replace(/\s+/g, ' ').slice(0, 40)
    }))
  } catch (e) {
    history.value = []
  }
}

function remember(text) {
  if (!text) return
  const list = history.value.filter((h) => h.text !== text)
  list.unshift({ text, time: Date.now(), label: String(text).replace(/\s+/g, ' ').slice(0, 40) })
  history.value = list.slice(0, 20)
  try {
    localStorage.setItem(HISTORY_KEY, JSON.stringify(history.value.map(({ label, ...rest }) => rest)))
  } catch (e) {
    /* 忽略配额错误 */
  }
}

function loadHistory(h) {
  form.type = 'text'
  form.content = h.text
  ElMessage.success('已载入')
}

function clearHistory() {
  history.value = []
  localStorage.removeItem(HISTORY_KEY)
  ElMessage.success('历史已清空')
}

/* 生成成功后记一条历史 */
watch(ready, (v) => {
  if (v) remember(buildText())
})

/* ===== 启动 ===== */
onMounted(() => {
  document.title = '码叮 QRding · 二维码美化'
  readTemplates()
  readHistory()
  nextTick(render)
})
</script>

<style scoped>
.qp-page {
  --ink: #1b2027;
  --ink-2: #3d444d;
  --ink-3: #767f8a;
  --line: #dbe2ec;
  --paper: #f3f6fb;
  --white: #fff;
  --brand: #0066ff;
  --brand-dk: #0047b3;
  --ok: #00c853;
  /* Element Plus 主题色 */
  --el-color-primary: #0066ff;
  --el-color-primary-light-3: #4d94ff;
  --el-color-primary-light-5: #80b3ff;
  --el-color-primary-light-7: #b3d1ff;
  --el-color-primary-light-8: #cce0ff;
  --el-color-primary-light-9: #e6f0ff;
  --el-color-primary-dark-2: #0052cc;
  --el-border-radius-base: 6px;
  background: var(--paper);
  min-height: 100vh;
  color: var(--ink);
  font-family: "Noto Sans SC", "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", system-ui, sans-serif;
  padding-bottom: 40px;
}
.qp-wrap { max-width: 1120px; margin: 0 auto; padding-inline: 20px; }
.qp-head { padding: 26px 0 18px; border-bottom: 1px solid var(--line); background: var(--white); }
.qp-brandline { display: flex; align-items: center; gap: 10px; }
.qp-logo img { width: auto; height: 26px; display: block; }
.qp-brandline h1 { font-size: 20px; font-weight: 600; letter-spacing: .01em; margin: 0; }
.qp-tag {
  font-size: 11px; color: var(--ink-3); border: 1px solid var(--line);
  padding: 2px 7px; border-radius: 6px; font-family: ui-monospace, Menlo, monospace;
}
.qp-lede { margin: 8px 0 0; font-size: 13px; color: var(--ink-3); max-width: 60em; }

.qp-main {
  display: grid; grid-template-columns: minmax(0, 1fr) minmax(0, 1fr);
  gap: 18px; align-items: start; padding-top: 20px;
}
.qp-card {
  background: var(--white); border: 1px solid var(--line); border-radius: 4px; padding: 16px;
}
.qp-card-head {
  display: flex; align-items: center; justify-content: space-between;
  gap: 12px; margin-bottom: 12px; flex-wrap: wrap;
}
.qp-card-title { font-size: 13px; font-weight: 600; }
.qp-meta { font-size: 11.5px; color: var(--ink-3); font-family: ui-monospace, Menlo, monospace; }
.qp-meta.warn { color: var(--brand); }

.qp-col { display: flex; flex-direction: column; gap: 18px; align-self: start; position: sticky; top: 16px; }
.qp-stage {
  display: grid; place-items: center; padding: 16px; border: 1px solid var(--line);
  border-radius: 3px; background: #fbfbf9; min-height: 300px;
}
.qp-stage.checker {
  background-image:
    linear-gradient(45deg, #e7e9e2 25%, transparent 25%),
    linear-gradient(-45deg, #e7e9e2 25%, transparent 25%),
    linear-gradient(45deg, transparent 75%, #e7e9e2 75%),
    linear-gradient(-45deg, transparent 75%, #e7e9e2 75%);
  background-size: 16px 16px;
  background-position: 0 0, 0 8px, 8px -8px, -8px 0;
}
.qp-canvas { max-width: 100%; max-height: 380px; display: block; }
.qp-actions { display: flex; gap: 8px; margin-top: 14px; flex-wrap: wrap; }
.qp-actions :deep(.el-button) { margin: 0; }
.qp-hint { margin: 10px 0 0; font-size: 12px; color: var(--brand); }

.qp-settings { display: flex; flex-direction: column; gap: 12px; }
.qp-field { display: flex; flex-direction: column; gap: 5px; min-width: 0; }
.qp-label { font-size: 12px; color: var(--ink-3); }
.qp-tip { color: var(--ink-3); opacity: .8; }
.qp-row2 { display: grid; grid-template-columns: minmax(0, 1fr) minmax(0, 1fr); gap: 12px; }
.qp-section {
  display: flex; align-items: center; gap: 10px;
  font-size: 12px; font-weight: 600; color: var(--ink); margin-top: 2px;
}
.qp-section::after { content: ""; height: 1px; flex: 1; background: var(--line); }

.qp-seg {
  display: inline-flex; border: 1px solid var(--line); border-radius: 3px;
  overflow: hidden; width: 100%;
}
.qp-seg button {
  flex: 1; appearance: none; border: 0; border-right: 1px solid var(--line);
  background: #fafaf8; font-size: 12.5px; color: var(--ink-2);
  padding: 7px 4px; cursor: pointer; transition: background .15s ease, color .15s ease;
}
.qp-seg button:last-child { border-right: 0; }
.qp-seg button.active { background: var(--brand); color: #fff; border-color: var(--brand); }

.qp-swatches { display: flex; flex-wrap: wrap; gap: 12px 18px; align-items: center; }
.qp-swatch { display: inline-flex; align-items: center; gap: 6px; font-size: 12px; color: var(--ink-2); }
.qp-switches { display: flex; flex-wrap: wrap; gap: 8px 16px; }

.qp-logo-row { display: flex; align-items: center; gap: 12px; flex-wrap: wrap; }
.qp-upload {
  display: inline-flex; align-items: center; padding: 7px 14px;
  border: 1px dashed #c9cec4; border-radius: 3px; font-size: 12.5px;
  color: var(--ink-2); background: #fbfbf9; cursor: pointer;
}
.qp-upload input { display: none; }
.qp-upload:hover { border-color: var(--ink); color: var(--ink); }

.qp-link {
  appearance: none; background: none; border: 0; padding: 0;
  font-size: 12.5px; color: var(--ink-2); cursor: pointer; text-decoration: underline;
  text-decoration-color: var(--line); text-underline-offset: 3px;
}
.qp-link:hover { color: var(--ink); text-decoration-color: var(--ink); }
.qp-link:disabled { opacity: .45; cursor: not-allowed; }
.qp-link.danger { color: var(--brand); }

.qp-empty { font-size: 12.5px; color: var(--ink-3); padding: 10px 0; }
.qp-tpl-list { list-style: none; display: flex; flex-direction: column; gap: 10px; }
.qp-tpl-list li {
  display: flex; align-items: center; gap: 10px; font-size: 12.5px;
  border-bottom: 1px dashed var(--line); padding-bottom: 8px;
}
.qp-tpl-list li:last-child { border-bottom: 0; padding-bottom: 0; }
.qp-tpl-dot { width: 14px; height: 14px; border-radius: 3px; flex: none; border: 1px solid rgba(0,0,0,.08); }
.qp-tpl-name { flex: 1; min-width: 0; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
.qp-tpl-name.mono { font-family: ui-monospace, Menlo, monospace; font-size: 11.5px; }

.qp-foot { margin-top: 24px; font-size: 12px; color: var(--ink-3); line-height: 1.7; }

@media (max-width: 900px) {
  .qp-main { grid-template-columns: minmax(0, 1fr); }
  .qp-col { position: static; }
  .qp-canvas { max-height: 320px; }
}
@media (max-width: 560px) {
  .qp-row2 { grid-template-columns: minmax(0, 1fr); }
  .qp-brandline h1 { font-size: 18px; }
}
</style>
