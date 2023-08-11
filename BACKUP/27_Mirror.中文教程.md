# [Mirror 中文教程](https://github.com/haoz0x139/myblog/issues/27)

1. 下载 `Mirror` 的最新版本 [地址](https://github.com/LoeiFy/Mirror/raw/master/release/mirror.zip)

2. 获取你的 `hash` [地址](https://github.com/LoeiFy/Mirror/wiki/%E8%8E%B7%E5%8F%96-hash)

3. 修改 `index.html`


```html
...

<script>
window.config = {
  organization: false, // 默认是 false，如果你的项目是属于 GitHub 组织 的，请设置为 true
  order: 'UPDATED_AT', // 文章排序，以 创建时间 或者 更新时间，可选值 'UPDATED_AT'，'CREATED_AT'
  title: 'Mirror', // 博客标题
  user: 'LoeiFy', // GitHub 用户名，必须
  repository: 'Recordum', // GitHub 项目名，指定文章内容来源 issues，必须
  authors: 'LoeiFy,author1', // 博客作者，以 ',' 分割，GitHub 用户名默认包含在内
  ignores: '17,13', // 文章忽略的 issues ID
  host: '', // 博客的主域名，不填自动获取，请注意这个值会影响 hash 的值
  hash: '', // 必须
  perpage: 5, // 分页
}
</script>

...
```

保存 `index.html`， 然后将所有文件 push 到 `gh-pages` 分支或者 `master` 分支的 `docs` 目录