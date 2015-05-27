dailyTxnPL
==========

描述
    按金融工具（instrument）生成每日交易事务已实现的或权益曲线（Equity Curve）上的损益。

用法
::

    dailyTxnPL(Portfolios, Symbols, drop.time=TRUE)

参数
    :Portfolios: 组合字符串
    :Symbols: 证券代码字符向量
    :drop.time: 去除POSIX日期戳的时间部件（如果有），缺省为 TRUE

说明
    设计用来为高频组合整理信息
