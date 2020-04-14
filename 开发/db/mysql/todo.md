
### 非法字符校验

检验用户名不能包含非法字符表达式

```
SELECT
  COUNT(*) cnt
FROM
  t_user t
WHERE t_user.username  REGEXP '[`~!@#$^&*()=|{}\':;\',\[\].<>/?~！@#￥……&*（）——|{}【】‘；：”“。，、？[:space:]]';
```
