# SDLC 网页图解

原始 PNG 仍保存在文章目录中，网页改用 `sdlc-figure` 渲染中文 HTML / SVG。
样式位于 `assets/css/sdlc-figures.css`，四种图共用一份样式，每页只加载一次。
可选的 `anchor` 参数用于设置页面内跳转目标，例如 `anchor="figure-1"`。

```text
{{< sdlc-figure kind="bottleneck" label="图 1" title="瓶颈已转移" caption="这里填写图注。" >}}

{{< sdlc-figure kind="loop" label="图 2" title="直线与闭环" >}}

{{< sdlc-figure kind="audit" title="提交的产物，串起审计线索" >}}

{{< sdlc-figure kind="dependencies" label="图 3" title="实战剧本依赖关系图" >}}
```

## 维护位置

- `layouts/partials/sdlc/bottleneck.html`：阶段耗时对比。仅表达相对变化，不表示精确工时比例。
- `layouts/partials/sdlc/loop.html`：传统流程与 AI 闭环。
- `layouts/partials/sdlc/audit.html`：产物与审计链提示。
- `layouts/partials/sdlc/dependencies.html`：依赖图的节点和连线数据。

依赖图保留原图的 12 个节点、5 个可直接起步的节点、13 条前置依赖和 4 条辅助关系。
SVG 连线与图下可展开的文字清单由同一份数据生成，修改时请同步核对原图。

## 可读性

- 侧栏正文继承博客字号，桌面约为 18px，不再使用原来的 `1.05rem`（约 10.5px）。
- 图解支持博客的两种深色主题属性。
- 依赖图在宽屏上可以适度超出正文宽度，最多 1200px。
- 复杂图在窄屏上保留可读尺寸，提供局部横向滚动和可展开的文字依赖清单。
- 图表滚动区可以用键盘聚焦，不会让整篇文章产生横向滚动。
- 简单图和审计提示会自动适应窄屏，不会作为图片弹出放大。
