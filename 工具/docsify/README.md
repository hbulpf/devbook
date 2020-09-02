# 使用 docsify

使用方法参考 [docsify官方文档](https://docsify.js.org/)

首页 index.html 参考下面

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <link rel="icon" type="image/x-ico" href="_media/icon.ico">
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
  <meta name="description" content="Description">
  <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/lib/themes/vue.css">
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/disqus.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/docsify-pagination/dist/docsify-pagination.min.js"></script>
</head>
<body>
  <div id="app"></div>
  <script>
    window.$docsify = {
      el: '#app',
      name: '成长',
      repo: ',
      loadSidebar: true,
      subMaxLevel: 2,
      loadNavbar: true,
      coverpage: true,
      auto2top: true,
      disqus: 'shortname',
      nameLink: '/',
      count:{
        countable:true,
        fontsize:'0.9em',
        color:'rgb(90,90,90)',
        language:'chinese'
      },
      search: {
        placeholder: '搜索',
        noData: '找不到结果!'
      }
    }
  </script>
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/emoji.min.js"></script>
  <script src="//unpkg.com/docsify-count/dist/countable.js"></script>
</body>
</html>
```