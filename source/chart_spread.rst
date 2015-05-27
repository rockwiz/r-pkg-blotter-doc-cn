chart.Spread
============

描述
    给交易事务序列、头寸和损益Charts the transaction series, positions, and P&L of a spread against prices

用法
::

    chart.Spread(Account, Portfolio, Spread, Symbols, Dates, ...)

参数
    :Account: 标识账户的字符串
    :Portfolio: 标识要画图的组合的字符串
    :Symbols: string identifying the underlying symbols to chart for positions
    :Spread: identifier of a spread instrument
    :Dates: 日期范围，目前未使用
    :...: 任何其它要传递的参数（典型是要传递给chart_Series的参数）
