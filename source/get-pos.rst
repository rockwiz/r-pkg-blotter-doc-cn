getPos
======

描述
    获取截止某个日期的所有头寸信息

用法
::

    getPos(Portfolio, Symbol, Date, Columns=c("Pos.Qty", "Pos.Avg.Cost"), n=1)

参数
    :Portfolio: 标识一个包含交易事务的组合对象的字符串
    :Symbol: 组合中的一种证券的标识符
    :Date: 最近期头寸的时间戳
    :Columns: 从组合的交易事务槽口（txn slot）中返回哪些列
    :n: 返回的期数，缺省为1

说明
    注意： This could get much more complicated from here, particularly when it’s conditional on symbol, etc.

返回值
    一个xts对象的一行中与头寸相关的所有数据元素
