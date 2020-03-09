# 安装 GitBook

1. [安装 nodejs](../../dev/webui/nodejs_install.md)

1. 安装 gitbook-cli
    ```
    npm install gitbook-cli -g
    ```

    安装成功后，执行 `gitbook -V` 查看版本信息。此命令会默认同时安装 GitBook。

1. 初始化 GitBook 文件夹，会生成两个必要的文件 README.md 和 SUMMARY.md

    ```
    gitbook init
    ```

1. 启动 GitBook 服务, GitBook 默认启动一个 4000 端口用于预览。
    ```
    gitbook serve
    ```
    
    以上访问 http://localhost:4000 可看到效果。
    另一种预览方式，运行 `gitbook build` 命令会在书籍的文件夹中生成一个 _book 文件夹, 里面的内容即为生成的 html 文件,这可以只生成网页而不开启服务器。

    如需指定端口
    ```
    gitbook serve --port=8081
    ```
# GitBook 文件说明

+ SUMMARY.md : 定制书籍的章节结构和顺序。
+ README.md : 书的介绍文字，如前言、简介，在章节中也可做为章节的简介。
+ book.json : 存放配置信息

## SUMMARY.md

一个SUMMARY.md 的范例

```
// SUMMARY.md

# Summary
* [Introduction](README.md)
* Part I
    * [从命令行进行测试](Chapter1/CommandLine.md)
    * [Monkey](Chapter1/Monkey.md)
    * [monkeyrunner 参考](Chapter1/MonkeyrunnerReference.md)
        * [概览](Chapter1/MonkeyrunnerSummary.md)
        * [MonkeyDevice](Chapter1/MonkeyDevice.md)
        * [MonkeyImage](Chapter1/MonkeyImage.md)
* Part II
    * [Introduction](Chapter2/c1.md)
    * [Introduction](Chapter2/c2.md)
```

## README.md
书的首页，主要是介绍性的文字，如前言、简介。

## book.json
book.json 用于存放配置信息。

```
{
    "title": "dev manual",
    "author": "RunAtWorld",
    "description": "it is for learning.",
    "language": "zh-hans",
    "gitbook": "3.2.3",
    "styles": {
        "website": "./styles/website.css"
    },
    "structure": {
        "readme": "README.md"
    },
    "links": {
        "sidebar": {
            "开发手册": "https://runatworld.gitbook.io"
        }
    },
    "plugins": [
        "sharing",
        "splitter",
        "expandable-chapters-small",
        "anchors",
        "github",
        "github-buttons",
        "donate",
        "sharing-plus",
        "anchor-navigation-ex",
        "favicon"
    ],
    "pluginsConfig": {
        "github": {
            "url": "https://github.com/RunAtWorld"
        },
        "github-buttons": {
            "buttons": [{
                "user": "RunAtWorld",
                "repo": "runatworld.github.io",
                "type": "star",
                "size": "small",
                "count": true
                }
            ]
        },
        "donate": {
            "alipay": "./source/images/donate.png",
            "title": "",
            "button": "赞赏",
            "alipayText": "支付宝"
        },
        "sharing": {
            "douban": false,
            "facebook": false,
            "google": false,
            "hatenaBookmark": false,
            "instapaper": false,
            "line": false,
            "linkedin": false,
            "messenger": false,
            "pocket": false,
            "qq": false,
            "qzone": false,
            "stumbleupon": false,
            "twitter": false,
            "viber": false,
            "vk": false,
            "weibo": false,
            "whatsapp": false,
            "all": [
                "google", "facebook", "weibo", "twitter",
                "qq", "qzone", "linkedin", "pocket"
            ]
        },
        "anchor-navigation-ex": {
            "showLevel": false
        },
        "favicon":{
            "shortcut": "./source/images/favicon.jpg",
            "bookmark": "./source/images/favicon.jpg",
            "appleTouch": "./source/images/apple-touch-icon.jpg",
            "appleTouchMore": {
                "120x120": "./source/images/apple-touch-icon.jpg",
                "180x180": "./source/images/apple-touch-icon.jpg"
            }
        }
    }
}
```

+ title: 本书标题
+ author: 本书作者
+ description: 本书描述
+ language: 本书语言，中文设置 "zh-hans" 即可
+ gitbook: 指定使用的 GitBook 版本
+ styles: 自定义页面样式
+ structure: 指定 Readme、Summary、Glossary 和 Languages 对应的文件名
+ links: 在左侧导航栏添加链接信息
+ plugins: 配置使用的插件
+ pluginsConfig: 配置插件的属性


# GitBook 插件
GitBook 有 插件官网，默认带有 5 个插件，highlight、search、sharing、font-settings、livereload，如果要去除自带的插件， 可以在插件名称前面加 -，比如：
```
"plugins": [
    "-search"
]
```

如果要配置使用的插件可以在 `book.json` 文件中加入即可，比如添加 `plugin-github`，在 book.json 中加入配置如下：

```
{
    "plugins": [ "github" ],
    "pluginsConfig": {
        "github": {
            "url": "https://github.com/your/repo"
        }
    }
}
```
然后在终端输入

```
gitbook install
```

以上命令相当于 `gitbook install ./`

如果要指定插件的版本可以使用 `plugin@0.3.1` ，因为一些插件可能不会随着 GitBook 版本的升级而升级。

## 各种用途插件

1. 折叠目录 

    增加 折叠目录 的插件，需要在 book.json 内增加下面代码:
    ```
    {
        "plugins": ["expandable-chapters-small"],
        "pluginsConfig": {
            "expandable-chapters-small":{}
        }
    }
    ```
[了解更多插件](http://gitbook.zhangjikai.com/plugins.html)

# 与 github 关联


# 参考
1. [gitbook 官网](https://docs.gitbook.com/v2-changes/important-differences)
2. [GitBook 插件](http://gitbook.zhangjikai.com/plugins.html)
3. [Gitbook 的使用和常用插件](https://zhaoda.net/2015/11/09/gitbook-plugins)
4. [一个基于gitbook快速写电子书的模版，支持html、pdf、docx、epub、mobi](https://github.com/yanhaijing/gitbook-boilerplate)
5. [用github做出第一本书](https://blog.csdn.net/hk2291976/article/details/51173850)
6. [知乎GitBook 使用教程](https://www.jianshu.com/p/421cc442f06c)


