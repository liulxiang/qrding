# QRding（扣叮）

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Release](https://img.shields.io/badge/release-v1.0.0-brightgreen.svg)](CHANGELOG.MD)
[![Docker](https://img.shields.io/badge/docker-ready-2496ED.svg?logo=docker&logoColor=white)](qrding-vue/Dockerfile)
[![Vue](https://img.shields.io/badge/Vue-3.x-42b883.svg?logo=vue.js&logoColor=white)](qrding-vue)
[![Backend](https://img.shields.io/badge/backend-none-lightgrey.svg)](#)

> 纯前端私有化二维码生成工具，提供两个版本：Vue增强版 / 原生HTML静态版
> 同生态配套项目：码叮（云端SaaS版），QRding面向内网离线私有化场景

简体中文 | [English](#english)

## 简介

QRding（扣叮）是**无后端、无数据库**的纯前端二维码生成工具。
二维码内容、渲染计算全部在浏览器本地执行，**不会上传任何内容到远端服务器**，适合企业内网、NAS、离线环境使用。

本仓库提供两套版本，按需选用：

1. **qrding-vue**：Vue3 + Element Plus 增强版
   功能完整，支持多模板、中心Logo嵌入、自定义颜色尺寸、纠错等级、本地历史记录、PNG/SVG导出；需要node构建，支持Docker部署。
2. **qrding-html**：原生HTML静态单文件版
   极简零构建版本，**无需npm、无需编译**，直接双击html打开即可运行；保留核心二维码生成功能，适合临时快速部署。

> 两套版本**均为纯前端**，不包含后端服务，数据全部保存在浏览器本地。

## ✨ 公共特性（两个版本共有）

- 🔒 隐私优先：浏览器本地计算，二维码内容不上传服务器，断网可用
- 🧩 多模板：普通文本、URL链接、WiFi配置、vCard电子名片
- 🎨 自定义参数：二维码尺寸、前景色/背景色、L/M/Q/H四级纠错
- 📥 导出PNG图片；Vue版额外支持SVG矢量图、Logo嵌入、本地历史记录

## 📂 版本区分

| 版本 | 技术栈 | 适用场景 | 额外能力 |
|---|---|---|---|
| qrding-vue | Vue3 + Element Plus | 私有化部署、内网NAS、需要完整UI | 上传中心Logo、localStorage历史、SVG导出 |
| qrding-html | HTML+原生JS | 临时使用、快速分发、低资源环境 | 单文件直接打开，零构建，体积极小 |

## 🚀 qrding-vue（Vue增强版）

### 本地开发

```bash
cd qrding-vue
npm install
npm run dev        # 启动本地开发服务
npm run build      # 打包静态产物到 dist/
npm run preview    # 本地预览打包结果
```

### Docker 部署

```bash
cd qrding-vue
docker build -t qrding-vue:1.0.0 .
docker run -d -p 8080:80 --name qrding qrding-vue:1.0.0
# 浏览器访问 http://localhost:8080
```

或使用 compose（目录内已提供 `docker-compose.yml`）：

```bash
cd qrding-vue
docker compose up -d
```

## 🌐 QRding-html（原生静态单文件版）

无需安装任何环境：

1. 下载 `QRding-html/index.html`
2. 双击用浏览器打开，或拖到浏览器窗口

如需容器分发，目录内同样提供 `Dockerfile` 与 `docker-compose.yml`（Nginx 静态托管）：

```bash
cd QRding-html
docker compose up -d
```

## 🐳 部署说明

- 两个版本的产物均为静态文件，可托管在 Nginx / Apache / NAS Web Station / 对象存储静态站点
- 无后端、无接口、无数据库依赖，不需要任何环境变量
- 生产环境建议开启 HTTPS（浏览器剪贴板、部分 Canvas 能力在非安全上下文受限）

## 📁 目录结构

```
qrding/
├── qrding-vue/          # Vue3 + Element Plus 增强版
│   ├── src/
│   │   ├── components/QrGenerator.vue
│   │   ├── App.vue
│   │   └── main.js
│   ├── Dockerfile
│   ├── docker-compose.yml
│   └── package.json
├── QRding-html/         # 单文件静态版
│   ├── index.html
│   ├── Dockerfile
│   └── docker-compose.yml
├── CHANGELOG.MD
├── CONTRIBUTING.MD
├── LICENSE
└── README.md
```

## 🔧 常见问题

**Q：二维码内容会被上传吗？**
不会。生成、渲染、导出全部在浏览器本地完成，断网也能用。

**Q：历史记录存在哪里？**
Vue 版保存在浏览器 `localStorage`（最多 20 条），清除浏览器缓存会丢失，不会同步到任何服务器。

**Q：两个版本怎么选？**
需要 Logo、历史记录、SVG 导出、完整 UI → 选 qrding-vue；只要临时生成、想零依赖分发一个文件 → 选 QRding-html。

## 🤝 贡献

欢迎提 Issue 与 PR，详见 [CONTRIBUTING.MD](CONTRIBUTING.MD)。版本变更见 [CHANGELOG.MD](CHANGELOG.MD)。

## 📄 许可证

本项目基于 [MIT License](LICENSE) 开源。

---

## English

# QRding

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Release](https://img.shields.io/badge/release-v1.0.0-brightgreen.svg)](CHANGELOG.MD)
[![Docker](https://img.shields.io/badge/docker-ready-2496ED.svg?logo=docker&logoColor=white)](qrding-vue/Dockerfile)

> A pure front-end, self-hosted QR code generator — Vue enhanced edition and a native single-file HTML edition.

QRding is a **backend-free, database-free** QR code generator. All content and rendering happen **locally in your browser**; nothing is uploaded to any server. Built for intranets, NAS devices and offline environments.

### Two editions

| Edition | Stack | Best for | Extra features |
|---|---|---|---|
| `qrding-vue` | Vue3 + Element Plus | Self-hosting, full UI | Center logo upload, localStorage history, SVG export |
| `QRding-html` | HTML + vanilla JS | Quick use, single-file distribution | Zero build, open the file and go |

### Features

- **Privacy first** — local computation, works offline
- **Templates** — plain text, URL, Wi-Fi, vCard
- **Customization** — size, foreground/background color, L/M/Q/H error correction
- **Export** — PNG in both editions; SVG, logo overlay and history in the Vue edition

### Quick start

```bash
# Vue edition
cd qrding-vue && npm install && npm run dev

# Docker (Vue edition)
cd qrding-vue && docker build -t qrding-vue:1.0.0 . && docker run -d -p 8080:80 qrding-vue

# HTML edition: just open QRding-html/index.html in a browser
```

### License

[MIT](LICENSE)
