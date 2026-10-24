# 全球签证助手（Web 项目 · 全部代码）

306 个国家/地区签证政策查询：国家详情、全球签证地图（3D 地球仪 / 平面地图）、
模拟面签（中英文对照提问 + 中英双语音频）、入境卡填写、工具箱（AI 评估、行程单等）、我的档案。
外观三档切换：浅色（白色基底 + 液态玻璃）/ 深色 / 跟随设备。

## 目录结构

```
visa-assistant-web/
├── index.html            全部页面代码（HTML + CSS + JS 单文件）
├── icon.svg              应用图标 / 浏览器标签页图标
├── README.md             本文件
└── assets/
    ├── countries.json    306 个国家/地区政策数据
    ├── flags-atlas.webp  国旗图集
    ├── landmarks/        地标照片 306 张（每个国家/地区一张，*.webp）
    ├── photos/           热门目的地照片 4 张（美国/日本/法国/澳大利亚）
    └── audio/            模拟面签提问录音 114 段（57 英文 + 57 中文，*.mp3）
```

共 429 个文件。

## 运行方式

纯静态站点，无需构建、无后端。用任意静态服务器打开根目录即可，例如：

```
cd visa-assistant-web
python3 -m http.server 8000
```

然后浏览器访问 http://localhost:8000 。也可部署到 GitHub Pages、Netlify、Vercel 等任意静态托管。

## GitHub Pages 发布

仓库包含 GitHub Actions 发布流程。将代码推送到 `main` 后会自动发布；首次发布时，
在仓库 **Settings → Pages → Build and deployment → Source** 选择 **GitHub Actions**。
发布完成后可通过仓库的 Pages 地址直接访问。

注意：index.html 会读取 assets/countries.json，直接双击以 file:// 打开时浏览器可能拦截本地 JSON 读取，
请用上面的本地服务器方式运行。

## 说明

- 无服务器：档案、申请表、入境卡、目标进度、评估答案与面签成绩保存在浏览器本地存储
  （localStorage）中，刷新不丢失；「我的档案 → 数据管理」可导出 JSON 备份或清除全部数据。
  数据按网址隔离，卸载 App 或清除浏览器数据会一并清掉，清理前请先导出。
- 入境卡的护照图片识别在本机浏览器内完成（OCR 组件从 CDN 加载），图片不上传。
- 签证政策数据核对于 2026 年 10 月，出发前请在各国官方页面复核最新公告。
