# 文档站

基于 [Docusaurus](https://docusaurus.io/) 构建的中英文文档网站。

## 安装

```bash
npm install
```

## 开发（热重载）

Docusaurus 一次只能运行一个语言环境：

```bash
# 开发英文文档（默认）
npm run dev

# 开发中文翻译（先停掉英文，再运行）
npm run dev:zh
```

## 查看完整中英文效果

```bash
npm run build && npm run serve
```

这会构建所有语言的静态文件并在 `http://localhost:3000` 启动服务，右上角可切换语言。

## 目录结构

```
docs/
├── docs/                        # 英文文档（默认语言）
│   ├── intro.md
│   ├── guides/
│   └── api/
├── i18n/
│   └── zh-CN/                   # 中文翻译
│       └── docusaurus-plugin-content-docs/current/
│           ├── intro.md
│           ├── guides/
│           └── api/
├── build/                       # 构建产物
├── docusaurus.config.ts         # 站点配置
└── sidebars.ts                  # 侧边栏配置
```

## 部署

```bash
npm run build
```

将 `build` 目录部署到任意静态托管服务即可。
