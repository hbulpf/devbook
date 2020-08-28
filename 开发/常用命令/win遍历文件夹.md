# 批处理脚本遍历文件夹下的文件

### 1. 遍历指定文件夹下的文件

##### 1.1 命令解释

**命令： `for [参数] %%变量名 in （匹配符） do （执行的命令）`**

**切记：每个指令之间必须以空格隔开，in 与 ( 之间有空格，do 与 （ 间也有空格，否则命令会无法成功执行**

**ps**：本节只讲用批处理脚本执行 for 命令遍历文件夹的场景，因此以下分析每个指令意义时，不介绍其他含义

**[]**：表示此项指令为可选

**[参数]**：参数取值一共有四种： `/d, /r, /l, /f`，加上无参数，所以一共五种场景

- 无参：遍历当前路径的文件夹下的文件，但也可在`(匹配符)`中指定路径
- /d：遍历当前路径的文件夹下的文件夹，但也可在`(匹配符)`中指定路径
- /r [路径]：深度遍历指定路径下的所有文件，子目录中的文件也会被遍历到，如果没指定路径，默认当前路径
- /l ：当使用参数 /l 时，需结合`(匹配符)`一起使用，此时 `()` 括号内部的用法规则为：`(start, step, end)`，此时的 for 命令作用等同于 java 语言中的 for 语句
- /f ：用于解析文件中的内容，本节不做介绍

**%%变量名**：作用类似于 `for(int i = 0; ; )` 中的 `int i = 0`，有些区别点的就是，批处理的 for 循环遍历每一个子项时，`%%变量名` <=> 每个子项，即 `&&变量名` 已经是指向具体的每个子项了

**（匹配符）**：在 in 指令之后 () 括号里的内容可表示为通配符，用于按照指定的规则过滤文件夹下的文件，如 (*.txt) 表示遍历文件夹内所有以 .txt 结尾的文件

**(执行的命令)**：前面的指令就可以取到文件夹内指定的每个子项了，那么接下去要对每个子项如何操作，就在这里写，类似于 java 的 for 命令后的 {} 大括号的作用

##### 1.2 使用示例

- 无参：`for %%i in (*) do ( echo %%i )`

    ![for无参命令示例.png](imgs/1924341-6f5d5efdef6356b4.png)

    效果：遍历当前目录下的所有文件

- 无参指定路径：`for %%i in (c:\softwares\VisualBat\*.url) do ( echo %%i )`

    ![for无参指定路径命令示例.png](imgs/1924341-1ff92bc4da9354d4.png)

    效果：遍历在`(匹配符)`中指定路径下的以 .url 结尾的文件

- 带参数 /d：`for /d %%i in (*) do ( echo %%i )`

    ![for参数d命令示例.png](imgs/1924341-1a992c48a8a357e5.png)

    效果：遍历当前目录下所有的文件夹

- 带参数 /d 指定路径：`for /d %%i in (c:\softwares\VisualBat\*) do ( echo %%i )`

    ![for参数d指定路径命令示例.png](imgs/1924341-b4b2cda8fd31b14f.png)

    效果：遍历指定目录下的所有文件夹，%%i 指向每个子文件夹的绝对路径

- 带参数 /r ：`for /r %%i in (*.url) do ( echo %%i )`

    ![for参数r命令示例.png](imgs/1924341-b829be8b50aed33c.png)

    效果：深度遍历当前路径下所有以 .url 结尾的文件，因为是深度遍历，因此 %%i 指向文件的绝对路径

- 带参数 /r 指定路径：`for /r c:\softwares\VisualBat\ %%i in (*.url) do ( echo %%i )`

  效果：同上图

- 带参数 /l ：`for /l %%i in (1, 1, 5) do ( echo %%i )`

    ![for参数l命令示例.png](imgs/1924341-dce7e6c8948d1893.png)

    效果：等效于 java 中的 `for (int i = 1; i <= 5; i++)`语句，起始值，递增或递减，终止值都可自行设置

- 带参数 /d /r：`for /d /r %%i in (*) do ( echo %%i )`

    ![for参数dr命令示例.png](imgs/1924341-bc68f937b6a38e91.png)

    效果：参数可结合使用，/d 表示遍历文件夹，/r 表示深度遍历，因此以上命令作用为深度遍历当前目录下的所有文件夹，包括子目录中的文件夹

### 2. 临时变量的使用

##### 2.1 变量的基本用法

**命令：`set key=value`**

**切记：`key=value` 三者之间绝对不能出现空格，不能为了像遵守 java 风格擅自给添加上空格，这与 java 的 `int a = 1` 声明变量不同，切记**

**变量使用：%key%**

**示例**：

```
@echo off
set name=dasuAndroidTv
echo %name%
```

![set命令示例.png](imgs/1924341-3a3e2d4136a0a3b8.png)

效果：name 可当做临时变量使用，使用时需用 %% 将变量名括起来使用

**局限**：不允许在 for 命令中类似上步中声明变量并直接使用，如下：

```
@echo off
for /l %%i in (0,1,5) do (
    set name=dasuAndroidTv
    echo %name%
)
```

![set命令示例2.png](imgs/1924341-50009febcf368685.png)

效果：在 for 命令中声明临时变量，并直接通过 %key% 方式使用时会出现上图中的错误：ECHO 处于关闭状态，但如果 `set key=value` 临时变量的声明是放在 for 命令外部，for 命令内部只是使用的话，是可以的，如下：

```
@echo off
set name=dasuAndroidTv
for /l %%i in (0,1,5) do (
    echo %name%
)
```

![set命令示例3.png](imgs/1924341-29cdda5c69c0f7ab.png)

效果：在 for 命令外部声明临时变量，for 命令内部只是使用，这种方式是允许的

##### 2.2 变量在 for 命令中的用法

**提问：那么如果要在 for 命令中才声明临时变量，并使用的话，该如何做？**

**for 命令中临时变量的使用：**

1. **需启用变量延迟功能，命令：`setlocal enabledelayedexpansion`**
2. **for 命令中的临时变量使用时用 `!key!` 感汉号括起来的形式代替 `%key%`**
3. 理由：不清楚，google 来的解决方案，感兴趣想深入研究的自行搜索

**示例**：

```
@echo off
setlocal enabledelayedexpansion
set name=dasu
for /l %%i in (0, 1, 5) do (
    set name=dasuAndroidTv 
    echo !name!
    echo %name%
)
```

![set命令示例4.png](imgs/1924341-156580c1ace9f6c6.png)

效果：说得白一点，在 for 命令中通过 %name% 方式使用的临时变量，取的 name 这个临时变量的值会一直是它在 for 命令外赋值的内容，即使在 for 命令中通过 set 命令对这个变量又重新赋值，也不会生效。

那么，如果需要在 for 命令中通过 set 命令赋值后的临时变量能够马上拿来使用，需要两个步骤，一在文件开头启用变量延迟功能，命令：**`setlocal enabledelayedexpansion`**，二在 for 命令中通过 **`!name!`**方式来使用临时变量。

### 3. 字符串处理

##### 3.1 截取

**命令：`%key:~[start,num]%`**

**解释**：当 `%key%` 中出现了 `:~`，则表示要对 key 指向的这个字符串做截取操作，截取操作支持以下几种形式：

- 截取**指定位置开始的 n 个字符串**：`%key:~0,4%`，表示截取从下标 0 开始的之后 4 个字符
- 截取从**指定位置开始的整个字符串**：`%key:~4%`，表示截取从下标为 4 开始的整个字符串
- 截取**通过倒数方式指定开始位置的整个字符串**：`%key:~-2%`，表示截取从倒数第 2 个字符开始的整个字符串
- 截取**通过倒数方式指定位置开始之后的 n 个字符串**：`%key:-4,2%`，表示截取从倒数第 4 个字符开始的 2 个字符
- 正数倒数方式相结合：`%key:~2,-2%`，表示截取从下标 2 开始到倒数第 2 个之间的字符串

**示例**：

```
@echo off
rem (rem表示后面是注释的内容，类似于 java //)原始字符串
set name=dasuAndroidTv

rem 注释内容：表示截取从下标 0 开始的之后 4 个字符，输出 dasu
echo %name:~0,4%

rem 注释内容：表示截取从下标为 4 开始的整个字符串，输出 AndroidTv
echo %name:~4%  

rem 注释内容：表示截取从倒数第 2 个字符开始的整个字符串，输出 Tv
echo %name:~-2%

rem 注释内容：表示截取从倒数第 4 个字符开始的 2 个字符，输出 Android
echo %name:~4,-2%

rem 注释内容：表示截取从下标 2 开始到倒数第 2 个之间的字符串，输出 id
echo %name:~-4,2%
```

![字符串截取命令示例.png](imgs/1924341-f6b658833dc648fb.png)

##### 3.2 拼接

**命令：`%key1%%key2%`**

**解释**：将要拼接的那个字符串直接跟在被拼接的后面即可，不需要任何拼接操作符

**示例**：

```
@echo off
set name1=dasu
set name2=AndroidTv
echo %name1%%name2%  
rem 这里是注释内容：输出 dasuAndroidTv
```

![字符串截取命令示例2.png](imgs/1924341-72430aab40b696bb.png)

##### 3.3 替换

**命令：`%key:被替换字符串=替换的字符串%`**

**解释**：不解释了，直接看示例，很容易明白

**示例**：

```
@echo off
set name=whoAndroidTv
echo %name:who=dasu%
rem 这里是注释内容：输出 dasuAndroid
```

![字符串替换命令示例.png](imgs/1924341-9e759e6969d34134.png)

##### 3.4 文件特殊操作

如果是在 for 命令中遍历了某个文件夹下的文件，那么此时可以通过一些特殊命令来获取这个文件的各种信息，直接看示例：

```
@echo off
for %%i in (*.txt) do (
   echo %%i
   echo %%~fi
   echo %%~di
   echo %%~pi
   echo %%~ni
   echo %%~xi
   
   echo %%~ti
   echo %%~zi
)
```

![特殊命令示例.png](imgs/1924341-b2f30fecb4518db5.png)

解释： 在通过 for 命令遍历文件时，%%i 根据不同的 for 使用方式，内容也有所不同，具体见第 1 节。在上述这种用法下，%%i 指向了当前目录下每个文件名，完整的文件名。

那么，此时就可以通过一些特殊命令来取得文件的相关信息，比如：

- **%%~fi**：表示获取该文件的绝对路径信息
- **%%~di**：表示获取该文件所在的盘符
- **%%~pi**：表示获取该文件的路径，不包含盘符的信息
- **%%~ni**：表示获取该文件的文件名，不包含扩展名信息
- **%%~xi**：表示获取该文件的扩展名
- **%%~ti**：表示获取该文件的上次修改时间
- **%%~zi**：表示获取该文件的大小

### 4. 完整示例

最后，我们来个具体场景，将本篇所学的知识用上一遍，巩固一下。

场景：遍历指定路径目录下的所有 apk 文件，并通过一个 sign.jar 文件，分别对每个 apk 文件执行 java 命令来进行签名工作，sign.jar 接收两个参数，一个是需要签名的 apk，另外一个为输出的 apk，要求签名后的 apk 命名方式为将原文件名中的 unsign 替换成 google，并输出在跟 apk 同一个目录内即可。

![完整示例.png](imgs/1924341-a19e2d07e083c304.png)

apk 路径：c:\users\suxq\desktop\outputs

sign.jar 路径：c:\users\suxq\desktop

java 签名命令示例(要求 sign.jar 和 apk 文件都在同一路径下，即可用如下命令)：

```
java -jar sign.jar meizi_1_3_0_debug_unsign.apk meizi_1_3_0_debug_google.apk
```

**批处理脚本代码：**

```
@echo off
setlocal enabledelayedexpansion

set sign=c:\users\suxq\desktop\sign.jar
set apkPath=c:\users\suxq\desktop\outputs\

for %%i in (%apkPath%*.apk) do (
    set oldApk=%%~nxi
    set outApk=!oldApk:unsign=google!
    echo java -jar %sign% !oldApk! !outApk!
    rem 这里是注释内容：由于 apk 文件 和 sign.jar 文件都是虚拟的，因此真正执行时会报错，这里就只是将 java 整句命令输出，从整句命令就可以确认是否会正确执行，如果这些文件都是真的话。真的脚本应该将 echo 去掉
)
```

![完整示例2.png](imgs/1924341-b267d226fbc883ab.png)

# 参考
1. [批处理脚本遍历指定文件夹下的文件](https://www.cnblogs.com/liangblog/p/9835940.html)