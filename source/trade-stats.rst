tradeStats
==========

描述
    对一个或多个组合中的一支或多支证券计算统计交易事务和损益。

用法
::

    tradeStats(Portfolios, Symbols)

参数
    :Portfolios: 组合字符串
    :Symbols: 证券代码字符串，缺省为NULL
    :uses: 对每日统计（dailyStats），决定数字是否要从交易或权益曲线（equity curve）计算

说明
    该函数计算一个或多个组合中的一支或多支证券的交易级（trade-level）统计。

    每一本关于交易的书籍、关于分析交易系统的经纪报告或博客文章在哪些交易统计是必需的，它们应如何显示等方面观点略微不同。我们选择不做这种类型的价值判断，而着眼于后处理阶段的包容性显示。

    函数的输出是一个数据框，其命名的列对应每个统计量。每行是单个组合+证券（portfolio+symbol）组合。数值以全精度返回。也许该函数的输出在所有条件下比你希望显示的要多，但它适合重塑显示。从数据框构建概要报告可能很容易实现，通过使用某些工具，如textplot或data.frame，with rounding, fancy formatting等等。取决于你的需求。
