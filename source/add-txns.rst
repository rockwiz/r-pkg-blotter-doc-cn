addTxns
=======

描述
    添加多个交易事务到一个组合

用法
::

    addTxns(Portfolio, Symbol, TxnData, verbose=TRUE, ..., ConMult)

参数
    :Portfolio: 指向由initPortf结构化的组合对象的组合名称
    :Symbol: 组合中的一种证券的标识符，例如IBM
    :TxnData: 一个包含所有所需交易事务（txn）字段的xts对象
    :...: 任何其它要传递的参数
    :verbose: 如果为TRUE（默认），函数将交易事务的元素打印一行输出到屏幕上，例如"2007-01-08 IBM 50 @ 77.6"；如果为FALSE，则不打印输出
    :ConMult: 合约或证券乘数因子，如果它没有在证券规范书（instrument specification）中定义

参考
    addTxn, initPortf
