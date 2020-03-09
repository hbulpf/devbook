
# swagger 介绍

[swagger官网](https://swagger.io/)

## [swagger](https://swagger.io/) 的各个功能模块

1. [Swagger Editor](https://editor.swagger.io): 类似于markendown编辑器的编辑Swagger描述文件的编辑器，该编辑支持实时预览描述文件的更新效果。也提供了在线编辑器和本地部署编辑器两种方式。可以通过[源码](https://github.com/swagger-api/swagger-editor)进行安装。

  Swagger Yaml 的语法规范可以参考[Swagger Editor](http://editor.swagger.io/#/)

1. [Swagger Codegen](./swagger-code-gen.md): 通过Codegen 可以将描述文件生成html格式和cwiki形式的接口文档，同时也能生成多钟语言的服务端和客户端的代码。支持通过jar包，docker，node等方式在本地化执行生成。也可以在后面的Swagger Editor中在线生成。

1. [Swagger UI](https://swagger.io/tools/swagger-ui/):提供了一个可视化的UI页面展示描述文件。接口的调用方、测试、项目经理等都可以在该页面中对相关接口进行查阅和做一些简单的接口请求。该项目支持在线导入描述文件和本地部署UI项目。


1. [Swagger Inspector](https://swagger.io/tools/swagger-inspector/): 和postman差不多，是一个可以对接口进行测试的在线版的postman。比在Swagger UI里面做接口请求，会返回更多的信息，也会保存你请求的实际请求参数等数据。

1. [Swagger Hub](https://swagger.io/tools/swaggerhub/)：集成了上面所有项目的各个功能，你可以以项目和版本为单位，将你的描述文件上传到Swagger Hub中。在Swagger Hub中可以完成上面项目的所有工作，需要注册账号，分免费版和收费版。

### swagger 各功能模块的开源仓库
1. swagger-editor . https://github.com/swagger-api/swagger-editor
1. swagger-ui . https://github.com/swagger-api/swagger-ui
1. swagger-codegen . https://github.com/swagger-api/swagger-codegen
1. swagger-core . https://github.com/swagger-api/swagger-core

### 其他
1. Springfox Swagger: Spring 基于swagger规范，可以将基于SpringMVC和Spring Boot项目的项目代码，自动生成JSON格式的描述文件。本身不是属于Swagger官网提供的，在这里列出来做个说明，方便后面作一个使用的展开。

### [Springfox Swagger Demo 代码](https://github.com/RunAtWorld/swagger-demo)

## Swagger Editor 的使用


## 参考
1. Swagger介绍及使用 . https://www.jianshu.com/p/349e130e40d5
1. 在线API文档工具swagger . https://blog.csdn.net/sej520/article/details/84915999
1. swagger-codegen生成java客户端代码 . https://blog.csdn.net/wangjunjun2008/article/details/53200437
1. swagger-editor的介绍与使用 . https://www.cnblogs.com/shamo89/p/7680941.html
1. Swagger Codegen简介 . https://www.cnblogs.com/shamo89/p/7680771.html
