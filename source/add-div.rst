addDiv
======

描述
    添加现金分红交易事务到一个组合
用法
::

    addDiv(Portfolio, Symbol, TxnDate, DivPerShare, ..., TxnFees=0, ConMult, verbose=TRUE)

参数
    :Portfolio: 指向由initPortf结构化的组合对象的组合名称
    :Symbol: 组合中的一种证券的标识符，例如IBM
    :TxnDate: 以ISO 8601格式的交易日期，如“2008-09-01” 或“2010-01-05 09:54:23.12345”
    :DivPerShare: 每股或每单位数量的现金分红金额
    :...: 任何其它要传递的参数
    :TxnFees: 与交易事务相关的费用，如佣金。参见说明部分
    :verbose: 如果为TRUE（默认），函数将交易事务的元素打印一行输出到屏幕上，例如"2007-01-08 IBM 50 @ 77.6"；如果为FALSE，则不打印输出
    :ConMult: 合约或证券乘数因子，如果它没有在证券规范书（instrument specification）中定义

说明
    添加现金分红不像股票分拆一样影响头寸数量
