
## 2. qrding/CHANGELOG.md
```markdown
# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
