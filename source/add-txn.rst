addTxn
======

描述
    添加一个交易事务到一个组合

用法
::

    addTxn(Portfolio, Symbol, TxnDate, TxnQty, TxnPrice, ..., TxnFees=0, ConMult, verbose=TRUE)

参数
    :Portfolio: 指向由initPortf结构化的组合对象的组合名称
    :Symbol: 组合中的一种证券的标识符，例如IBM
    :TxnDate: 以ISO 8601格式的交易日期，如“2008-09-01” 或“2010-01-05 09:54:23.12345”
    :TxnQty: 总的交易数量（如股数或合约数）。正数值代表“买入”，负数值表示“卖出”
    :TxnPrice: 交易价格
    :...: 任何其它要传递的参数
    :TxnFees: 与交易事务相关的费用，如佣金。参见说明部分
    :ConMult: 合约或证券乘数因子，如果它没有在证券规范书（instrument specification）中定义
    :verbose: 如果为TRUE（默认），函数将交易事务的元素打印一行输出到屏幕上，例如"2007-01-08 IBM 50 @ 77.6"；如果为FALSE，则不打印输出

说明
    当组合出现交易或调整，addTxn 函数计算交易价值和平均成本、头寸变化、由此带来的头寸平均成本以及任何从交易中已实现的利润或亏损。然后，它将交易事务和运算（过程和结果1）存储在组合对象中。

    费用被标示为负数值，将从交易价值中减去。TxnFees可以是一个固定额，或者是一个确定费用总额的函数。pennyPerShare函数提供一个交易成本函数的简单范例。

备注
    addTxn函数最终也将处理其它类型交易类型，如公司活动造成的调整或期权过期、授予期权等。
参考
    addTxns, pennyPerShare, initPortf
