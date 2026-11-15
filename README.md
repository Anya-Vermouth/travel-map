# 行走中国，足迹留痕

> 这是一个旅游/日常记录器。如果你想记录生活，又因为太 I 而不敢发朋友圈；如果你想清晰地看到自己的旅游地图——这是一个非常好用的网站，在这里记录你的河山大好吧！（数据仅储存在你的设备里）

**在线体验**：<https://anya-vermouth.github.io/travel-map/>

在网页上点亮去过的省份，按城市记录景点、随笔、心情和照片；鼠标悬停（或手机点按）省份 1 秒，就能看到自己的旅行地图。

## 功能

- 完整中国地图（含南海诸岛与九段线），去过的省份按心情点亮
- 省份 A–Z 首字母导航、悬停 1 秒详情、点击联动表单
- 城市级增删改：日期、景点、随笔、心情、多张照片
- 照片粘贴自动压缩（最长边 800px / JPEG 质量 0.7）、轮播与全屏 Lightbox
- 同一省份出现多种心情时显示橙色；默认心情为紫色
- 数据只保存在浏览器 localStorage，可导出 / 导入 JSON 备份

## 数据与隐私

- 每个访客的数据只存在自己的浏览器里，不上传、不需要账号。
- 清除浏览器数据会丢失记录，建议用「导出足迹」定期备份。
- 换设备时用「导出 / 导入」迁移。

## 本地运行

直接双击 `index.html`，或在本目录运行：

```bash
python -m http.server 8000
```

地图与 ECharts 从公网 CDN 加载，需要联网。

## 部署

纯静态单文件页面，可部署到 GitHub Pages / Netlify / Vercel / Cloudflare Pages。
本仓库使用 GitHub Pages：仓库 **Settings → Pages → Deploy from a branch → main / root**。

## 技术

ECharts 5 · 阿里云 DataV GeoJSON · 原生 HTML / CSS / JS · localStorage
