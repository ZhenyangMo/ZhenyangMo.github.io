# 文末资料索引

在 Markdown 中使用 `resource-index` 包裹资料索引，每个分类使用一个 `resource-column`。
电脑上分类按两栏排列，640px 及以下切为单栏，样式自动跟随博客的深色模式。

```text
## 参考资源与致谢

以下文档可供继续阅读。

{{< resource-index acknowledgment="这里填写原文致谢。" >}}

{{< resource-column title="组织配置与基础管控" >}}

- [为组织配置 Claude Code](https://code.claude.com/docs/en/admin-setup)

  管理员配置决策指南，建议从这里开始。

- [设置参考与优先级](https://code.claude.com/docs/en/settings)

  涵盖各类设置项及其优先级。

{{< /resource-column >}}

{{< resource-column title="企业部署、监控与安全" >}}

- [企业网络配置](https://code.claude.com/docs/en/network-config)

  查看网络配置说明。

{{< /resource-column >}}

{{< /resource-index >}}
```

每个列表项的第一段是链接标题，第二段是简短说明，两段之间保留空行。
说明行前保留两个空格，使其属于同一个列表项。

- `resource-column` 的 `title` 是分类名称。
- `resource-index` 的 `acknowledgment` 是可选的原文致谢，省略后不显示致谢区。
- 可继续添加分类；每行最多两栏，手机每行一栏。
- 样式集中在 `assets/css/resource-index.css`，每页只加载一次。
- 页面会沿用中文标题，不另外显示长网址；链接在当前标签页打开，避免意外弹窗。

使用 `hugo server -D` 可以预览草稿，使用 `hugo -D` 可以检查构建。
