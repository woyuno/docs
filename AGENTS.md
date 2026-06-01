# AGENTS.md - 项目开发说明

## 项目概述

基于 Docusaurus 3.10 的中英文文档网站。

## 技术栈

- Docusaurus 3.10.1
- TypeScript
- React 19
- Node.js 20+

## 目录结构

```
docs/
├── docs/                        # 英文文档（默认语言 en）
│   ├── intro.md                 # 介绍
│   ├── guides/                  # 指南
│   │   ├── _category_.json
│   │   ├── getting-started.md
│   │   └── configuration.md
│   └── api/                     # API
│       ├── _category_.json
│       ├── overview.md
│       └── endpoints.md
├── i18n/
│   └── zh-CN/                   # 中文翻译
│       └── docusaurus-plugin-content-docs/current/
│           ├── intro.md
│           ├── guides/
│           └── api/
├── build/                       # 构建产物
├── src/
│   └── pages/
│       └── index.tsx            # 首页
├── docusaurus.config.ts         # 站点配置（含 i18n）
├── sidebars.ts                  # 侧边栏配置
├── package.json
└── README.md
```

## 可用命令

| 命令 | 说明 |
|------|------|
| `npm run dev` | 开发模式 - 英文（热重载） |
| `npm run dev:zh` | 开发模式 - 中文（热重载） |
| `npm run build` | 构建所有语言的静态文件 |
| `npm run serve` | 启动生产服务器 |
| `npm run build && npm run serve` | 构建并查看完整效果 |

## i18n 配置说明

- 默认语言：`en`（英文）
- 第二语言：`zh-CN`（简体中文）
- 开发时一次只能运行一个语言环境
- 构建时会自动生成所有语言的静态文件

### 新增中文翻译

在 `i18n/zh-CN/docusaurus-plugin-content-docs/current/` 下创建与 `docs/` 结构一致的文件即可。

### 翻译导航栏/页脚

编辑 `i18n/zh-CN/docusaurus-theme-classic/navbar.json` 和 `footer.json`。

## 服务管理

当前服务通过 screen 管理：

```bash
screen -ls                          # 查看所有 screen 会话
screen -r docusaurus-serve          # 进入会话（Ctrl+A D 退出）
kill $(lsof -t -i:3000)             # 停止服务
```
