# 对话示例卡片

在文章 Markdown 中使用 `incident-chat` 包裹对话，每条消息使用一个 `chat-message`。
不需要手写 HTML，也不需要另外引入样式；组件会按页面加载一次样式文件。

```text
{{< incident-chat label="图 4" title="事故频道中的第一响应者" channel="#inc-checkout" description="事故响应频道 · Claude 以独立身份加入" caption="请求、诊断、人工授权和修复结果，都保留在同一个地方。" >}}

{{< chat-message author="R. Mehta" avatar="RM" time="22:04" >}}
结账服务的错误率一直在上升，能看一下吗？
{{< /chat-message >}}

{{< chat-message author="Claude" role="assistant" time="22:07" >}}
已找到可能的原因，回滚流程也已经演练过。**需要我执行吗？**
{{< /chat-message >}}

{{< chat-message author="R. Mehta" avatar="RM" time="22:08" >}}
**执行吧。**
{{< /chat-message >}}

{{< chat-message author="Claude" role="assistant" time="22:12" >}}
已回滚，复盘已写入 `lessons/2026-06-checkout-cache.md`。
{{< /chat-message >}}

{{< /incident-chat >}}
```

## 可调整的内容

- `label`：图号，可以省略。
- `title`：卡片标题，默认“对话示例”。
- `channel`：频道名称，默认 `#incident`。
- `description`：频道说明，可以省略。
- `caption`：卡片下方的图注，可以省略。
- `author`：消息发送者，默认“成员”。
- `avatar`：人工发送者的头像文字，建议 1–2 个字符，默认“人”。
- `role="assistant"`：使用橙色智能体头像；省略则使用灰色人工头像。
- `time`：可选的消息时间，使用 `22:04` 这样的 24 小时格式。

消息正文支持 Markdown，包括加粗、行内代码、多段文字和链接。
每个 `chat-message` 必须直接嵌套在 `incident-chat` 中。

## 样式与预览

- 样式集中在 `assets/css/incident-chat.css`。
- 对话正文继承博客字体和字号，不会修改其他段落。
- 支持主题的 `data-dark-mode` 和 `icy-dark-mode` 深色模式。
- 手机窄屏会缩小卡片内边距；长文件名自动换行。

在博客目录运行 `hugo server -D`，即可预览包含该组件的草稿文章。
