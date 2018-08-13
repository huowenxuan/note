# CASE表达式
条件分支

```sql
CASE WHEN <求值表达式> THEN <表达式>
     WHEN <求值表达式> THEN <表达式>
     WHEN <求值表达式> THEN <表达式>
     ...
     ELSE <表达式>
END
```

求值表达式返回真值（TRUE/FALSE/UNKNOWN），是由谓词写出来的表达式。从第一个WHEN求值开始执行，如果为TRUE，就返回THEN中的表达式，如果不为真，就跳到下一个WHEN，如果都不为真，返回ELSE的表达式（ELSE可省略）

## 用法

```sql
SELECT name,
       CASE WHEN name = '衣服'
            THEN 'A'
            WHEN name = '裤子'
            THEN 'B'
            ELSE NULL
        END AS ab_name
FROM tb1;
```