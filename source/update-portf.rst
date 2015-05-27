updatePortf
===========
描述
    遍历每支证券，为每个可用期间价格计算损益

用法
::

    updatePortf(Portfolio, Symbols, Dates, Prices, ...)

参数
    :Portfolio: TODO
    :Symbols: TODO
    :Dates: TODO
    :Prices: TODO
    :dots: 任何其它要传递的参数

说明
    | 输入组合：一个包含交易事务的组合对象
    | 证券：组合中证券的标识符
    | 日期：计算证券账户的日期，这些日期必须出现在价格流中
    | 输出：将头寸信息和损益（P&L）赋值到环境中

