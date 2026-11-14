# Contributing to QRding（扣叮）
感谢你对 QRding 项目感兴趣！欢迎提交 Issue、PR 来改进项目。

> 项目仓库包含两个独立版本：
> - `qrding-vue`：Vue3+Element Plus 增强版
> - `qrding-html`：原生HTML静态极简版

## 📋 贡献前须知
1. QRding 是**纯前端私有化二维码生成工具**，所有二维码运算在浏览器本地执行，**不增加后端服务**。
2. 本项目目标：内网离线私有化使用，不引入数据库、服务端API。
3. 代码协议：MIT License，提交代码即代表你同意代码以MIT协议开源。

## 🐛 提交 Issue
你可以新建 Issue 用于：
- Bug反馈（记得写明版本：qrding-vue 或 qrding-html；浏览器；复现步骤）
- 新功能建议
- 文档优化、错别字修正

> 请不要提交：需要引入后端、数据库、远程服务接口的需求，不在本项目范围内（该能力可使用同生态「码叮」）

## 🔧 本地开发环境
### qrding-vue
```bash
cd qrding-vue
npm install
npm run dev #本地调试
npm run build #构建静态产物
