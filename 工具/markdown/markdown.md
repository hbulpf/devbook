# Markdown 简明语法手册

标签： Markdown 语法手册

---

### 1. 斜体和粗体

使用 * 和 ** 表示斜体和粗体。

示例：

这是 *斜体*，这是 **粗体**。

### 2. 分级标题

使用 === 表示一级标题，使用 --- 表示二级标题。

示例：

```
这是一个一级标题
============================

这是一个二级标题
--------------------------------------------------

### 这是一个三级标题
```

你也可以选择在行首加井号表示不同级别的标题 (H1-H6)，例如：# H1, ## H2, ### H3，#### H4。

### 3. 外链接

使用 \[描述](链接地址) 为文字增加外链接。

示例：

这是去往 [本人博客](http://ghosertblog.github.com) 的链接。

### 4. 无序列表

使用 *，+，- 表示无序列表。

示例：

- 无序列表项 一
- 无序列表项 二
- 无序列表项 三

### 5. 有序列表

使用数字和点表示有序列表。

示例：

1. 有序列表项 一
2. 有序列表项 二
3. 有序列表项 三

### 6. 文字引用

使用 > 表示文字引用。

示例：

> 野火烧不尽，春风吹又生。

### 7. 行内代码块

使用 \`代码` 表示行内代码块。

示例：

让我们聊聊 `html`。

### 8.  代码块

使用 四个缩进空格 表示代码块。

示例：

    这是一个代码块，此行左侧有四个不可见的空格。

### 9.  插入图像

使用 \!\[描述](图片链接地址) 插入图像。

示例：

![我的头像](data:image/png;base64,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)


也可以使用html 的 img 标签
```
<img src="https://github.com/kubernetes/kubernetes/raw/master/logo/logo.png" width="100">
```
<img src="https://github.com/kubernetes/kubernetes/raw/master/logo/logo.png" width="100">

# Cmd Markdown 高阶语法手册

### 1. 内容目录

在段落中填写 `[TOC]` 以显示全文内容的目录结构。

[TOC]

### 2. 标签分类

在编辑区任意行的列首位置输入以下代码给文稿标签：

标签： 数学 英语 Markdown

或者

Tags： 数学 英语 Markdown

### 3. 删除线

使用 ~~ 表示删除线。

~~这是一段错误的文本。~~

### 4. 注脚

使用 [^keyword] 表示注脚。

这是一个注脚[^footnote]的样例。

这是第二个注脚[^footnote2]的样例。

### 5. LaTeX 公式

`$` 表示行内公式： 

质能守恒方程可以用一个很简洁的方程式 $E=mc^2$ 来表达。

`$$` 表示整行公式：

$$\sum_{i=1}^n a_i=0$$

$$f(x_1,x_x,\ldots,x_n) = x_1^2 + x_2^2 + \cdots + x_n^2 $$

$$\sum^{j-1}_{k=0}{\widehat{\gamma}_{kj} z_k}$$

访问 [MathJax](http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference) 参考更多使用方法。

如果无法渲染出公式，使用以下两种方式最简单:

1. 使用 [typora](https://www.typora.io/)
2. 使用 [vscode ](https://code.visualstudio.com/) +  [Markdown Preview Enhanced插件](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced )

### 6. 加强的代码块

支持四十一种编程语言的语法高亮的显示，行号显示。

非代码示例：

```
$ sudo apt-get install vim-gnome
```

Python 示例：

```python
@requires_authorization
def somefunc(param1='', param2=0):
    '''A docstring'''
    if param1 > param2: # interesting
        print 'Greater'
    return (param2 - param1 + 1) or None

class SomeClass:
    pass

>>> message = '''interpreter
... prompt'''
```

JavaScript 示例：

``` javascript
/**
* nth element in the fibonacci series.
* @param n >= 0
* @return the nth element, >= 0.
*/
function fib(n) {
  var a = 1, b = 1;
  var tmp;
  while (--n >= 0) {
    tmp = a;
    a += b;
    b = tmp;
  }
  return a;
}

document.write(fib(10));
```

### 7. 流程图

#### 示例

```flow
st=>start: Start:>https://www.zybuluo.com
io=>inputoutput: verification
op=>operation: Your Operation
cond=>condition: Yes or No?
sub=>subroutine: Your Subroutine
e=>end

st->io->op->cond
cond(yes)->e
cond(no)->sub->io
```

#### 更多语法参考：[流程图语法参考](http://adrai.github.io/flowchart.js/)

### 8. 序列图

#### 示例 1

```seq
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
```

#### 示例 2

```seq
Title: Here is a title
A->B: Normal line
B-->C: Dashed line
C->>D: Open arrow
D-->>A: Dashed open arrow
```

#### 更多语法参考：[序列图语法参考](http://bramp.github.io/js-sequence-diagrams/)

### 9. 甘特图

甘特图内在思想简单。基本是一条线条图，横轴表示时间，纵轴表示活动（项目），线条表示在整个期间上计划和实际的活动完成情况。它直观地表明任务计划在什么时候进行，及实际进展与计划要求的对比。

```gantt
    title 项目开发流程
    section 项目确定
        需求分析       :a1, 2016-06-22, 3d
        可行性报告     :after a1, 5d
        概念验证       : 5d
    section 项目实施
        概要设计      :2016-07-05  , 5d
        详细设计      :2016-07-08, 10d
        编码          :2016-07-15, 10d
        测试          :2016-07-22, 5d
    section 发布验收
        发布: 2d
        验收: 3d
```

#### 更多语法参考：[甘特图语法参考](https://knsv.github.io/mermaid/#/gantt)

### 10. Mermaid 流程图

```graphLR
    A[Hard edge] -->|Link text| B(Round edge)
    B --> C{Decision}
    C -->|One| D[Result one]
    C -->|Two| E[Result two]
```

#### 更多语法参考：[Mermaid 流程图语法参考](https://knsv.github.io/mermaid/#/flowchart)

### 11. Mermaid 序列图

```sequence
    Alice->John: Hello John, how are you?
    loop every minute
        John-->Alice: Great!
    end
```

#### 更多语法参考：[Mermaid 序列图语法参考](https://knsv.github.io/mermaid/#/sequenceDiagram)

### 12. 表格支持

| 项目        | 价格   |  数量  |
| --------   | -----:  | :----:  |
| 计算机     | \$1600 |   5     |
| 手机        |   \$12   |   12   |
| 管线        |    \$1    |  234  |


### 13. 定义型列表

名词 1
:   定义 1（左侧有一个可见的冒号和四个不可见的空格）

代码块 2
:   这是代码块的定义（左侧有一个可见的冒号和四个不可见的空格）

        代码块（左侧有八个不可见的空格）

### 14. Html 标签

本站支持在 Markdown 语法中嵌套 Html 标签，譬如，你可以用 Html 写一个纵跨两行的表格：

    <table>
        <tr>
            <th rowspan="2">值班人员</th>
            <th>星期一</th>
            <th>星期二</th>
            <th>星期三</th>
        </tr>
        <tr>
            <td>李强</td>
            <td>张明</td>
            <td>王平</td>
        </tr>
    </table>


<table>
    <tr>
        <th rowspan="2">值班人员</th>
        <th>星期一</th>
        <th>星期二</th>
        <th>星期三</th>
    </tr>
    <tr>
        <td>李强</td>
        <td>张明</td>
        <td>王平</td>
    </tr>
</table>

### 15. 内嵌图标

本站的图标系统对外开放，在文档中输入

    <i class="icon-weibo"></i>

即显示微博的图标： <i class="icon-weibo icon-2x"></i>

替换 上述 `i 标签` 内的 `icon-weibo` 以显示不同的图标，例如：

    <i class="icon-renren"></i>

即显示人人的图标： <i class="icon-renren icon-2x"></i>

更多的图标和玩法可以参看 [font-awesome](http://fortawesome.github.io/Font-Awesome/3.2.1/icons/) 官方网站。

### 16. 待办事宜 Todo 列表

使用带有 [ ] 或 [x] （未完成或已完成）项的列表语法撰写一个待办事宜列表，并且支持子列表嵌套以及混用Markdown语法，例如：

    - [ ] **Cmd Markdown 开发**
        - [ ] 改进 Cmd 渲染算法，使用局部渲染技术提高渲染效率
        - [ ] 支持以 PDF 格式导出文稿
        - [x] 新增Todo列表功能 [语法参考](https://github.com/blog/1375-task-lists-in-gfm-issues-pulls-comments)
        - [x] 改进 LaTex 功能
            - [x] 修复 LaTex 公式渲染问题
            - [x] 新增 LaTex 公式编号功能 [语法参考](http://docs.mathjax.org/en/latest/tex.html#tex-eq-numbers)
    - [ ] **七月旅行准备**
        - [ ] 准备邮轮上需要携带的物品
        - [ ] 浏览日本免税店的物品
        - [x] 购买蓝宝石公主号七月一日的船票

对应显示如下待办事宜 Todo 列表：
        
- [ ] **Cmd Markdown 开发**
    - [ ] 改进 Cmd 渲染算法，使用局部渲染技术提高渲染效率
    - [ ] 支持以 PDF 格式导出文稿
    - [x] 新增Todo列表功能 [语法参考](https://github.com/blog/1375-task-lists-in-gfm-issues-pulls-comments)
    - [x] 改进 LaTex 功能
        - [x] 修复 LaTex 公式渲染问题
        - [x] 新增 LaTex 公式编号功能 [语法参考](http://docs.mathjax.org/en/latest/tex.html#tex-eq-numbers)
- [ ] **七月旅行准备**
    - [ ] 准备邮轮上需要携带的物品
    - [ ] 浏览日本免税店的物品
    - [x] 购买蓝宝石公主号七月一日的船票
        
---
[^footnote]: 这是一个 *注脚* 的 **文本**。

[^footnote2]: 这是另一个 *注脚* 的 **文本**。

# markdown 工具
1. [Cmd 技术渲染的沙箱页面，在线编写自己的文档](https://www.zybuluo.com/mdeditor "作业部落旗下 Cmd 在线 Markdown 编辑阅读器")

# 参考
1. [Markdown 语法手册](https://www.zybuluo.com/EncyKe/note/120103#fnref:footnote)
