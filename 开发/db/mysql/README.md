### 时间比较

- 转成时间戳
    - `unix_timestamp(time1)`  将字符型的时间，转成unix时间戳
- 格式化
    - `Date(time1)` 将 datetime 转成 date
    - `MONTH(time1)`
    - `Year(time1)`
    - `Month(time1)`
- 哪一天
    - `DAYOFWEEK(time1)` , `WEEKDAY(time1)` 0 = 星期一
    - `DAYOFMONTH(time1)`
    - `DAYOFYEAR(time1)`
    - `DAYNAME(time1)` ， `MONTHNAME(time1)` 
- 季度
    - `QUARTER(time1)`
- 日期比较
    - `>` `<` `=` 如 `SELECT NOW() > '2019-09-21 15:59:59';`
    - `between ... and ...` 如 `SELECT NOW() BETWEEN '2019-09-21 15:59:59' AND '2019-10-21 15:59:59' AS res;`
    - `DATEDIFF(time1,time2)` 如 `SELECT DATEDIFF(NOW(),'2019-09-21 15:59:59') > 0;`
- 日期计算
    - 减 `DATE_SUB(CURDATE(),INTERVAL 3 MONTH)`
    - 加 `DATE_ADD(CURDATE(),INTERVAL 3 MONTH)`
- 计算两日期时间之间相差的天数,秒数,分钟数,周数,小时数
    - `TIMESTAMPDIFF(unit,datetime_expr1,datetime_expr2)`
        ```
        FRAC_SECOND   表示间隔是毫秒
        SECOND   秒
        MINUTE   分钟
        HOUR   小时
        DAY   天
        WEEK   星期
        MONTH   月
        QUARTER   季度
        YEAR   年
        ```
    - 计算两日期之间相差多少周 
        ```sql
        select timestampdiff(WEEK,'2011-09-30','2015-05-04');
        ```
    - 计算两日期之间相差多少天 
        ```sql
        select timestampdiff(day,'2011-09-30','2015-05-04');`
        ```
    - 计算两日期/时间之间相差的分钟数　
        ```sql
        select timestampdiff(MINUTE,'2011-09-30','2015-05-04');
        -- 或
        SELECT　SEC_TO_TIME(UNIX_TIMESTAMP(end_time) -　UNIX_TIMESTAMP(start_time));
        ```