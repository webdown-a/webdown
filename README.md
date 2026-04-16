# WebDown Extension + License Server

中文 | [English](#english)

## 中文

WebDown 是一个网页资源下载扩展，支持页面资源抓取、下载任务控制（开始/暂停/继续/取消）、授权与试用管理、公告下发与后台管理。

### 主要功能
- 下载控制：开始、暂停、继续、取消
- 资源抓取增强：支持 `webRequest` 捕获、`noscript` 解析、根路径重写
- 授权系统：激活/刷新/状态/试用
- 运行配置：扩展从后端拉取 `/config/public`
- 公告系统：支持中英文和换行内容
- 管理后台：`/admin` 登录页（`x-admin-token`）+ 首页管理

### 目录结构
- `background.js`：扩展后台核心逻辑
- `popup.html` / `popup.js`：弹窗 UI 与交互
- `src/`：解析器、编排器、常量与通用模块
- `dist/`：扩展构建产物
- `license-server/`：授权与后台服务

### 接口基址
- `https://extension.hepingan.top/webdown-license`

授权相关接口：
- `POST /licenses/activate`
- `POST /licenses/refresh`
- `POST /licenses/status`
- `POST /licenses/trial/start`

运行配置：
- `GET /config/public`

### 本地构建
```bash
npm install
npm run build
```

### 后端运行（systemd）
服务名：`webdown-license.service`

环境变量文件：`/etc/default/webdown-license`
关键项：
- `LICENSE_SERVER_PORT`
- `LICENSE_SERVER_DB`
- `LICENSE_ADMIN_TOKEN`
- `LICENSE_TRIAL_DAYS_DEFAULT`

---

## English

WebDown is a web resource downloader extension with task controls (start/pause/resume/cancel), licensing/trial support, announcement delivery, and an admin panel.

### Key Features
- Download controls: start, pause, resume, cancel
- Improved capture: `webRequest` merge, `noscript` parsing, root-relative rewrite
- License flows: activate / refresh / status / trial
- Runtime config: extension loads `/config/public`
- Announcement: bilingual (ZH/EN) with multiline content
- Admin panel: `/admin` login with `x-admin-token`

### Project Layout
- `background.js`: core background workflow
- `popup.html` / `popup.js`: popup UI
- `src/`: parser, orchestrator, constants
- `dist/`: built extension assets
- `license-server/`: backend service

### API Base
- `https://extension.hepingan.top/webdown-license`

License APIs:
- `POST /licenses/activate`
- `POST /licenses/refresh`
- `POST /licenses/status`
- `POST /licenses/trial/start`

Runtime config:
- `GET /config/public`

### Build
```bash
npm install
npm run build
```

### Backend (systemd)
Service: `webdown-license.service`

Environment file: `/etc/default/webdown-license`
Main variables:
- `LICENSE_SERVER_PORT`
- `LICENSE_SERVER_DB`
- `LICENSE_ADMIN_TOKEN`
- `LICENSE_TRIAL_DAYS_DEFAULT`
