chart.Reconcile
===============

描述
    将相对于市场数据的交易、一段时间的头寸和累计损益（PPLdiff）绘制成图。PPLdiff 是“累计的”，因此该面板将显示理论与实际组合间差异的累计总和。

用法
::

    chart.Reconcile(theoPort, actualPort, Symbol, Dates, ..., PLdiff=c("cumulative", "episodic"), data=c(FALSE, "View", "return"))

参数
    :theoPort: 标识要绘图的理论组合的字符串
    :actualPort: 标识要绘图的实际组合的字符串
    :Symbol: 标识要绘图的证券的字符串
    :Dates: xts ISO 8601风格子集
    :...: 任何要传递给chart_Series的参数
    :PLdiff: “cumulative”或“episodic”，参见说明部分
    :data: 与计算数据相关，参见说明部分

说明
    生成一个时间序列的三面板或四面板图，顶部是价格和交易事务、第二个为由此产生的头寸、第三个面板上是累计损益线图。

    首先以较浅颜色绘制出理论上的交易、头寸和损益，然后以主色覆盖画出实际值。如果它们完全吻合，那么理论值将不可见。差异通过代码或折线的失配得以显现。

    第四个面板理论和实际值在损益（P&L）方面的差异，可以被理解为是正的或负的“滑价”（slippage）。它是将实际损益减去理论损益计算而来。如果参数PLdiff 是“cumulative”，那么面板上显示的是实际组合和理论组合之间差异的累计总和；如果PLdiff是“episodic’”，它将显示损益的差异。

    data参数允许用户查看或返回在图中计算得出的数据，缺省为FALSE（仅图）

参考
    chart.Posn
