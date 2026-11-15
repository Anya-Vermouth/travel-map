# 行走中国，足迹留痕 · 部署与分享说明

这是一个**纯静态单文件网页**（`index.html`）：不需要服务器、不需要数据库、不需要账号。
所有人的足迹都只保存在**自己浏览器的 localStorage** 里，彼此独立，不会上传到任何地方。

---

## 一、最快上线：Netlify Drop（约 1 分钟）

1. 打开 <https://app.netlify.com/drop>
2. 把本项目的 **`site` 文件夹**（或 `travel-footprints-site.zip`）直接拖进页面
3. 按提示用 GitHub / 邮箱登录（用于长期保留这个站点）
4. 得到一个 `https://xxxx.netlify.app` 网址，发给朋友即可

朋友打开网址后，会看到默认的北京示例，可以直接开始记录自己的行程。

---

## 二、其他发布方式

### Vercel

本机装好 Node.js 后，在 `site` 目录执行：

```bash
npx vercel
```

按提示登录、一路回车；正式发布用：

```bash
npx vercel --prod
```

得到 `https://xxxx.vercel.app`。

### GitHub Pages

1. 新建一个 **public** 仓库
2. 上传 `site/index.html`（文件名必须保持 `index.html`）
3. 仓库 **Settings → Pages → Build and deployment**
   - Source 选 `Deploy from a branch`
   - Branch 选 `main`，目录选 `/ (root)`，保存
4. 几分钟后访问 `https://<你的用户名>.github.io/<仓库名>/`

### Cloudflare Pages

1. 登录 <https://dash.cloudflare.com/>
2. **Workers & Pages → Pages → Upload assets**
3. 拖入 `site` 文件夹，得到 `https://xxxx.pages.dev`

---

## 三、临时分享（同一 Wi-Fi，无需部署）

在 `site` 目录执行：

```bash
python -m http.server 8000
```

然后在同一局域网内，让朋友访问 `http://<你的电脑 IP>:8000`。
（Windows 需要允许 Python 通过防火墙；电脑关机后链接失效。）

---

## 四、数据说明（重要）

- 每个访客的足迹只存在**自己浏览器的 localStorage**，互不可见，也不会同步到服务器。
- 换手机/电脑：用页面底部的 **导出足迹** 下载 JSON，在新设备上 **导入足迹** 即可。
- 清除浏览器数据会丢失记录，建议定期导出备份。
- 页面底部还有 **复制页面链接**（部署到公网后可用）和 **恢复示例**。
- 想让「多人共用一张地图 / 账号登录 / 跨设备自动同步」，需要加后端（例如 Supabase、Firebase）。
  当前版本刻意保持纯前端、无账号，打开即用、数据私有。

---

## 五、更新页面

修改 `index.html` 后，重新把 `site` 文件夹拖到 Netlify Drop（或重新 `vercel --prod`、重新上传）。
如果已经绑定同一站点，重新部署会覆盖旧版本，访客的 localStorage 数据不受影响。

---

## 六、这一版包含的功能

- 完整中国地图（含南海诸岛与九段线）
- 省份 A–Z 导航、悬停 1 秒展开、点击联动表单
- 城市级增删改、城市随笔、多图粘贴压缩、照片轮播
- 心情可选（默认紫色；单一心情按颜色；同一省份多种心情显示橙色）
- 全屏 Lightbox：左右切换、1/N 提示、键盘 ←/→/Esc
- 默认北京示例（天安门 / 人民英雄纪念碑两张实拍照片已内嵌）
- 分享与备份：导出 / 导入 / 复制链接 / 恢复示例
