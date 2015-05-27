calcPortfWgt
============

描述
    计算给定组合内头寸的组合权重。

用法
::

    calcPortfWgt(Portfolio, Symbols, Dates, denominator=c("Gross.Value", "Net.Value", "Long.Value", "Short.Value"), Account)

参数
    :Portfolio: 指向由initPortf结构化的组合对象的组合名称
    :Symbols: 组合中的一种证券的标识符
    :Dates: 计算日期，格式为xts范围
    :denominator: TODO
    :Account: TODO

说明
    根据它们的使用，组合权重的计算可能不一样。

返回值
    行为按日期的权重，列为证券名称的xts时间序列对象。
