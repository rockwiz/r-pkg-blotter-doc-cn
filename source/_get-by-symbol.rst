.getBySymbol
============
描述
    获取组合中的每个头寸计算后的属性

用法
::

    .getBySymbol(Portfolio, Attribute, Dates, Symbols, native=FALSE)

参数
    :Portfolio: 一个包含交易事务的组合对象
    :Attribute: 为每个证券设定的列名称
    :Dates: 日期子集，为xts风格的ISO 8601字符串
    :Symbols: 代码
    :native: TODO

说明
    从posPL 表中获取组合中每个头寸的计算后的属性，装配进symbol-by-time用于图形或计算

    条目典型包括以下：'Pos.Qty', 'Pos.Value', 'Txn.Value', 'Realized.PL', 'Unrealized.PL', 或 'Trading.PL'

返回值
    按证券（代码）的普通xts对象
