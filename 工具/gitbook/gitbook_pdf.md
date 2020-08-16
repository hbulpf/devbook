# gitbook 生成 pdf 

## 方式1

输出为PDF文件，需要先安装`gitbook pdf`

```bash
$ npm install gitbook-pdf -g
```

> 如果在安装gitbook-pdf时，觉得下载`phantomjs`包太慢的话，你可以到`phantomjs`的官方网站上去下载。
>
> http://phantomjs.org/
>
> 这个包的安装方式，参考其官网的说明文档。

然后，用下面的命令就可以生成PDF文件了。

```bash
$ gitbook pdf {book_name}
```

如果，你已经在编写的gitbook当前目录，也可以使用相对路径。

```bash
$ gitbook pdf .
```

然后，你就会发现，你的目录中多了一个名为`book.pdf`的文件。

## 方式2

构建生成html

```
$ gitbook build . ../_book
```

生成pdf, epub, mobi文件，依赖[calibre](https://calibre-ebook.com/)里的ebook-convert
```
$ gitbook pdf . ./gitbook-boilerplate.pdf
$ gitbook epub . ./gitbook-boilerplate.epub
$ gitbook mobi . ./gitbook-boilerplate.mobi
```

生成一个markdown文件，需要node环境
```
$ npm run build:markdown
```

生成docx格式，依赖生成的统一markdown文件，依赖[pandoc](https://pandoc.org/)环境

```
$ pandoc gitbook-boilerplate.md -o gitbook-boilerplate.docx
```

# 参考
1. [输出PDF](https://tonydeng.github.io/gitbook-zh/gitbook-howtouse/output/pdfandebook.html)
