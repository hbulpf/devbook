# excel 技巧


#### Q: 计算一列是否在另一列中

方法1
```
=VLOOKUP(C1,A:A,1,0)

C1，查找内容
A:A，查找区域，查找区域的第一列要与查找内容对应（假设有多列的话）
1，返回区域对应第几列的值。（从1开始）
TRUE，是否模糊查找，FALSE为精确查找
```

方法2
```
=if（countif（A:A，C1）>=1,C1,""）
```

其他方法
```
=IF(SUMPRODUCT(N(ISNUMBER(FIND($E$2:$E$8,A2)))),"有","无")
=IF(COUNTIF(A:A,"*"&B1&"*"),"出现","无") 下拉填充公式
```

#### Q: 求某个字符串最后一次出现的位置


求B2的字符串中 `-` 的最后位置

方法1：
```
=-LOOKUP(,-FIND("-",B2,ROW(B:B)))
```
方法2：
```
=LEN(B2)-LEN(TRIM(RIGHT(SUBSTITUTE(B2,"-",REPT(" ",LEN(B2))),LEN(B2))))
```
结果

```
aopalliance-repackaged-2.4.0	23
```

参考: [百度知道](https://zhidao.baidu.com/question/1545808660112949787.html)

#### 参考
1. [判断一个字符串中是否包含某些字符](https://blog.csdn.net/AIIB69/article/details/80907890)
2. [Excel常见函数用法](https://www.jianshu.com/p/ce782b18059f)