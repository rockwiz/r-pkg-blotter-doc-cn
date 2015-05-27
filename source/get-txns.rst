getTxns
=======

描述
    获取交易事务和它们的属性。

用法
::

    getTxns(Portfolio, Symbol, Dates)

参数
    :Portfolio: 一个包含交易事务的组合对象的字符串标识符
    :Symbol: 组合中的一种证券的标识符
    :Dates: 一个ISO 8601日期或一个xts日期范围，如"2007-01::2008-04-15"

说明
    查找并返回指定组合中的证券和日期的交易事务和属性。

    本函数提供一种容易的方式存取Portfolio 对象中包含的交易数值。有关Portfolio对象结构的详细描述，参见initPortf。

返回值
    给定时期内证券形成的交易事务的xts时间序列

参考
    initPortf
