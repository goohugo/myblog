# [使用存储过程非常慢，但是执行SQL很快的解决方案](https://github.com/haoz0x139/myblog/issues/32)

# 前言
最近，在工作中发现，两个问题:

1. 应用程序调用存储过程很慢，但是在查询分析器中把SQL语句拿出来执行存储过程就很快。
2. 在查询分析器中执行存储过程很慢，但是把存储过程中的内容拿出来执行很快

# 问题的分析与解决
## 问题1 产生原因

在应用程序中(或者在查询分析器中)调用存储过程的时候，存储过程的执行计划是被缓存了，就算参数不同，还是按照老的执行计划查询，效率也会不同。

## 问题1 解决方法

直接在存储过程定义参数的最后，添加**WITH RECOMPILE** 就会被强行重新编译执行存储过程

如下图代码所示：
```
ALTER PROCEDURE PRO_NAME
(
   @PARA1 VARCHAR(100)
) WITH  RECOMPILE
```

## 问题2 产生原因

在执行存储过程中出现了参数嗅探

## 问题2 解决方法

如果存储过程调用的比较频繁可使用**OPTION (OPTIMIZE FOR UNKNOWN)**，如果不是，可使用**OPTION (RECOMPILE)**。

因为业务需要，存储过程需要频繁使用，所以，使用了**OPTION (OPTIMIZE FOR UNKNOWN)** 处理。

具体使用代码示例如下：
```
ALTER PROCEDURE PRO_NAME
(
   @PARA1 VARCHAR(100)
) WITH  RECOMPILE
AS
BEGIN
   SELECT * FROM TABLE_NAME WHERE FIELD_NAME=@PARA1 OPTION (OPTIMIZE FOR UNKNOWN)
END
```
以上，亲测有效~