# 5分钟搞定Hexo

## 快速搭建

```undefined
npm install hexo-cli -g
hexo init blog
cd blog
npm install
hexo server // 本地运行,也可换成hexo s
```

本地访问  http://localhost:4000/ 

## 快速发布

### 创建文章

``` bash
$ hexo new "My New Post"
```

```
// [layout] 为布局，可选项为 `post`、`page`、`draft`，这将决定文章所在文件路径。
hexo new [layout] <title>
```
更多参考  [Writing](https://hexo.io/zh-cn/docs/writing.html)

### 启动服务

``` bash
$ hexo server
```

如果您想要更改端口，在执行时使用 -p 选项指定其他端口：
```
$ hexo server -p 5000
```

更多参考  [Server](https://hexo.io/zh-cn/docs/server)

### 生成静态文件

``` bash
$ hexo generate
```

更多参考  [Generating](https://hexo.io/zh-cn/docs/generating.html)

## 实用技能

### 更换主题皮肤

更换主题流程：下载主题 -> 配置主题，以 `xoxo` 为例

```bash
# 下载到themes文件夹下
git clone https://github.com/KevinOfNeu/hexo-theme-xoxo xoxo

# 修改 _config.yml 配置
theme: xoxo
```

### 部署到github

在项目根目录下找到 `_congif.yml`，找到 `deploy` 字段并填写完整.

```bash
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: <你的仓库地址> # https://github.com/TJ-XiaJiaHao/TJ-XiaJiaHao.github.io
  branch: master
```

我们需要额外的一个工具来帮助我们推到仓库上，那就是 `hexo-deployer-git`。搞它！

```javascript
npm install hexo-deployer-git --save
```

执行下面两个命令，就可以把项目部署到 `github` 上。

```undefined
hexo clean
hexo deploy
```

更多参考 [hexo官方部署](https://hexo.io/zh-cn/docs/one-command-deployment)

### 部署优化

每次都要执行 `hexo clean` 和 `hexo deploy`，不如写个新的脚本

```javascript
// package.json
"dev": "hexo s",
"build": "hexo clean & hexo deploy"
```

部署命令

```javascript
npm run build
```

### 接入评论系统 - valine

https://valine.js.org/quickstart.html


## 主题
### [ils](https://github.com/XPoet/hexo-theme-ils)

```
npm install hexo-generator-index-pin-top
npm install hexo-generator-searchdb
npm i --save hexo-wordcount
```

# 参考
1. [hexo官网](https://hexo.io/)