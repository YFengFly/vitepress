# 从 VuePress 迁移

## 配置

### 侧边栏

侧边栏不再从 frontmatter 中自动获取。 你可以[自行阅读 frontmatter](https://github.com/vuejs/vitepress/issues/572#issuecomment-1170116225) 来动态填充侧边栏。 [其他的工具方法]（https://github.com/vuejs/vitepress/issues/96）将来可能会提供。

## Markdown

### 图片

与 VuePress 不同，在使用静态图片时，VitePress 会根据你的配置自动处理这些 [`base`](./asset-handling#base-url)。

因此，现在你可以在没有 `img` 标签的情况下渲染图像。

```diff
- <img :src="$withBase('/foo.png')" alt="foo">
+ ![foo](/foo.png)
```

::: warning 警告
对于动态图像，您仍然需要 `withBase`，如 [基本 URL 指南](./asset-handling#base-url) 中所示。
:::

使用 `<img.*withBase\('(.*)'\).*alt="([^"]*)".*>` 正则表达式查找并替换为 `![$2]($1)` 用 `![](...)` 语法替换所有图像。

---

更多请继续关注...
