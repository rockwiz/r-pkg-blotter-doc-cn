.updatePosPL
============

描述
    根据头寸数据和相应的收盘价数据计算头寸损益（P&L）

用法
::

    .updatePosPL(Portfolio, Symbol, Dates, Prices, ConMult, ...)

参数
    :Portfolio: 指向由initPortf结构化的组合对象的组合名称
    :Symbol: 组合中的一种证券的标识符
    :Dates: 日期的xts子集，如 "2007-01::2008-04-15"。 这些日期必须出现在价格流中
    :Prices: xts对象中的定期价格，其列名称与getPrice 兼容
    :ConMult: 如果需要，数值型合约乘数因子；如果定义了证券（亦即金融工具，instrument），则不需要
    :...: 任何其它要传递的参数

返回值
    头寸信息和损益的普通时间序列
