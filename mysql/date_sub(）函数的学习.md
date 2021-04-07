获取当前日期：select curdate() 

获取当前日期前一天：select date_sub(curdate(),interval 1 day)

获取当前日期后一天：select date_sub(curdate(),interval -1 day)

 

在判断当中的使用：

在判断当中也是一样的使用哈，例想要从表中查A，条件是time大于等于昨天，time小于等于今天：

select A from 表 where time >=date_sub(curdate(),interval 1 day) AND time <= curdate





## MySQL计算日期的函数DATE_SUB(d,INTERVAL expr type)

DATE_SUB(d,INTERVAL expr type)函数返回起始日期d减去一个时间段后的日期。

expr是一个表达式，用来指定从起始日期添加或减去的时间间隔值。

expr是一个字符串。对于负值的时间间隔，它可以用一个负号“-”开头。

expr表达式与后面的间隔类型type对应。

MySQL中的日期间隔类型如下表所示：

| 类型(type值)  | 含义     | expr表达式的形式         |
| :------------ | :------- | :----------------------- |
| YEAR          | 年       | YY                       |
| MONTH         | 月       | MM                       |
| DAY           | 日       | DD                       |
| HOUR          | 时       | hh                       |
| MINUTE        | 分       | mm                       |
| SECOND        | 秒       | ss                       |
| YEAR_MONTH    | 年和月   | YY和MM之间用任意符号隔开 |
| DAY_HOUR      | 日和小时 | DD和hh之间用任意符号隔开 |
| DAY_MINUTE    | 日和分钟 | DD和mm之间用任意符号隔开 |
| DAY_SECOND    | 日和秒钟 | DD和ss之间用任意符号隔开 |
| HOUR_MINUTE   | 时和分   | hh和mm之间用任意符号隔开 |
| HOUR_SECOND   | 时和秒   | hh和ss之间用任意符号隔开 |
| MINUTE_SECOND | 分和秒   | mm和ss之间用任意符号隔开 |

------

## 实例1

使用DATE_SUB()函数执行日期减操作。SQL语句如下：

```
mysql>SELECT DATE_SUB('2014-10-11 12:00:00',INTERVAL 1 SECOND) AS col1,
    ->DATE_SUB('2014-10-11 23:59:59',INTERVAL '1 1' YEAR_MONTH) AS col2;
```

## 提示

DATE_SUB(d,INTERVAL expr type)函数在指定修改的时间段时，也可以指定负值，负值代表相减，减去一个负值，得到的是对日期的相加，即返回以后的日期和时间。

DATE_SUB(d,INTERVAL expr type)函数中的type必须在上表中。而且，type必须是上表中的某一项，不能是其中几项的组合。因此，使用该函数时，一定要注意type的选择。

DATE_SUB(d,INTERVAL expr type)函数和SUBDATE(d,INTERVAL expr type)函数的作用相同。