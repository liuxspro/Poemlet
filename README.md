# 小诗词

一个诗词展示网站，配合fanfou bot 使用。每次刷新随机展示一首诗词，动态路由可锁定具体诗词用于社交分享。

## 项目结构

```text
/
├── public/
│   └── favicon-128.png
├── src/
│   ├── assets/
│   │   └── background.svg
│   ├── components/
│   │   ├── Footer.astro       # 页脚
│   │   ├── Header.astro       # 左上角诗词类型标签
│   │   ├── Poem.astro         # 页面布局（背景图、header、内容区、footer）
│   │   └── PoemDisplay.astro  # 诗词内容区布局与样式
│   ├── layouts/
│   │   └── Layout.astro       # 全局 HTML 结构
│   └── pages/
│       ├── index.astro        # 首页，随机展示诗词
│       └── poem/
│           └── [id].astro     # 动态路由，按 ID 展示指定诗词（SSR）
└── package.json
```

## 路由

| 路由 | 渲染方式 | 说明 |
|---|---|---|
| `/` | 静态（客户端随机取诗） | 每次刷新展示随机诗词 |
| `/poem/:id` | SSR | 按 ID 展示指定诗词，完整 HTML 输出 |

## 数据来源

诗词数据来自 [诗泉 API](https://poetry.palemoky.com/api)。

## Fanfou bot

配套 bot 通过 `/poems/random` 获取随机诗，发送时附上 `/poem/{id}` 链接，用户点击可看到同一首诗。

## 开发命令

| 命令 | 说明 |
|---|---|
| `pnpm install` | 安装依赖 |
| `pnpm dev` | 启动开发服务器，默认 `localhost:4321` |
| `pnpm build` | 构建生产版本 |
| `pnpm preview` | 本地预览构建结果 |

## 部署

本项目使用 Vercel 部署，SSR 路由通过 `@astrojs/vercel` 适配为 Serverless Function。
