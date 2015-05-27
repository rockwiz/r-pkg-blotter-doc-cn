chart.Posn
==========

描述
    将相对市场数据的交易、一段时间的头寸、累计损益绘制成图。

用法
::

    chart.Posn(Portfolio, Symbol, Dates, ...)

参数
    :Portfolio: 标识要画图的组合
    :Symbol: 标识要画图的证券
    :Dates: xts ISO 8601风格子集
    :...: 任何要传递给chart_Series的参数

说明
    生成一个时间序列的三面板图，顶部是价格和交易事务、中间为由此产生的头寸、最底下是累计损益线图。
