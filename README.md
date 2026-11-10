# 光影聚合 MovieHub

一个纯前端（HTML + CSS + 原生 JavaScript）的**影视信息导航页面**，无需构建、无需依赖，双击 `index.html` 即可运行。

> 本项目仅作页面练习与技术演示，不提供任何影视资源。请通过正版授权渠道观看。

## 功能

- **影片卡片墙**：响应式网格布局，随窗口宽度自动换行
- **分类筛选**：全部 / 纪录片 / 动画，点击切换，选中态高亮
- **关键词搜索**：输入片名回车即搜，实时过滤卡片
- **详情弹窗**：点击卡片弹出大图、类型标签、剧情简介
  - 三种关闭方式：点 `×`、点遮罩、按 `ESC`
  - 卡片与弹窗均标注 `可打开` 状态
- **空状态提示**：搜不到结果时显示"没有找到匹配的影片"

## 文件结构

```
MovieHub/
├── index.html      # 全部内容：结构 + 样式 + 逻辑（单文件）
├── .gitignore
└── README.md
```

## 快速开始

**方式一：直接打开**

双击 `index.html`，或拖进浏览器。

**方式二：VS Code Live Server（推荐，改代码自动刷新）**

1. 用 VS Code 打开本文件夹
2. 右键 `index.html` → `Open with Live Server`

## 技术要点

| 部分 | 说明 |
|---|---|
| 布局 | CSS Grid `repeat(auto-fill, minmax(170px, 1fr))` 自适应列数 |
| 筛选 | 读取卡片的 `data-type`，按分类切换 `display` |
| 搜索 | 读取 `data-name`，转小写后 `indexOf` 匹配 |
| 弹窗 | 数据集中在 `MOVIES` 对象里，`openDetail(name)` 动态填充 DOM |
| 样式 | 深色主题，主色 `#f5bd55`，卡片 hover 上浮 + 阴影 |

## 添加新影片

在 `index.html` 里做两件事：

1. 在 `.movies` 容器中加一张卡片：

```html
<div class="movie" data-type="电影" data-name="片名" onclick="openDetail('片名')">
  <div class="poster">🎬</div>
  <div class="movie-info">
    <h3>片名 <span class="badge">可打开</span></h3>
    <p>电影 · 类型</p>
    <p class="meta">2024 · 中国大陆 · 120 分钟</p>
  </div>
</div>
```

2. 在 `<script>` 的 `MOVIES` 对象里补上详情：

```js
"片名": {
  poster: "🎬",
  meta: ["电影", "类型", "2024", "中国大陆", "120 分钟"],
  desc: "剧情简介……",
  keyword: "片名 电影"
}
```

> 如果新增了新的 `data-type`，记得在 `.categories` 里加一个对应按钮。

## 浏览器支持

Chrome / Edge / Firefox / Safari 等现代浏览器（使用 `CSS Grid`、`NodeList.forEach`、`classList`）。

## 许可

仅用于学习与演示。影片名称、简介等信息版权归各自权利人所有。

## 在线预览

已通过 GitHub Pages 部署：**https://hac1314.github.io/MovieHub/**
