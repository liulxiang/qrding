
## 2. qrding/CHANGELOG.md
```markdown
# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [v1.1.0] - 2026-11-14
### Added — qrding-vue 二维码美化升级
- 填充：纯色 / 渐变（斜向、纵向、横向、径向四方向），主色+辅色可调
- 背景：自定义颜色 / 透明背景（棋盘格预览，PNG 保留透明通道）
- 码点形状：方块 / 圆角 / 圆点 / 菱形；码点缩放 60%–100%
- 码眼形状：方块 / 圆角 / 圆形，支持码眼独立配色
- 静区可调（0/1/2/3/4/6/8 个模块）；反色模式（浅码深底）
- 中心 Logo：上传后按比例叠加，可调大小（10%–30%）与白色底板
- 底部文字：最多 24 字，输出高度自动增加
- 导出尺寸 512 / 1024 / 1536 px；PNG 下载、SVG 导出（形状与渐变同步）、复制图片
- 样式模板：本地保存/套用/删除；历史记录保留最近 20 条
- 输入即生成（180ms 防抖），预览显示版本 / 模块数 / 输出尺寸 / 字符数
- 可扫性提示：前景背景对比度偏低、码点留缝过大时在预览下方给出建议
### Changed
- 内容模板补全 Wi-Fi 加密方式/隐藏网络、vCard 公司/网址字段，Wi-Fi 特殊字符按规范转义
- 默认码点缩放取 96%（实测 92% 在密集码下会被严格解码器判为不可读）
- Element Plus 界面重做：预览与样式两列、移动端单列，样式模板与历史并入左栏
### Fixed
- 修复 `el-list` / `el-list-item` 不存在导致的列表不渲染
- 修复 canvas 在 `v-if` 内导致首次生成取不到节点
- 修复 SVG 透明底码眼挖孔为方孔（应随码眼样式变圆孔）

## [v1.0.0] - 2026-11-14
### Added
- 🎉 仓库初始化，提供双版本：`qrding-vue` + `qrding-html`
- qrding-vue（Vue3 + Element Plus）
  - 4种模板：普通文本 / URL / WiFi / vCard电子名片
  - 二维码自定义：尺寸、前景色、背景色、L/M/Q/H四级纠错
  - 中心Logo上传并叠加绘制（Canvas）
  - localStorage 本地历史记录（最多保存20条）
  - 支持导出 PNG图片 + SVG矢量图
  - Element Plus UI、消息提示、载入/清空历史
  - Dockerfile + docker-compose 容器化部署
- qrding-html（原生静态HTML单文件版）
  - 同4套二维码模板
  - 尺寸、颜色、纠错级别自定义
  - PNG图片下载导出
  - 单文件零构建，直接浏览器打开
  - Nginx静态Docker部署
### Notes
- 两个版本全部为纯前端，**无后端，数据不上传服务器**
- 历史记录仅保存在浏览器 localStorage，清除缓存会丢失

## [Unreleased] 计划待开发
- 暗色主题支持（两个版本）
- 二维码码眼圆角美化
- 批量生成二维码功能（vue版优先）
- 复制图片到剪贴板
- 导入/导出本地历史记录JSON备份
