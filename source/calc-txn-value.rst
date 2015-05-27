calcTxnValue
============

描述
    计算一个事务或一次交易的总金额

用法
::

    calcTxnValue(TxnQty, TxnPrice, TxnFees, ConMult=1)

参数
    :TxnQty: 交易的总数量
    :TxnPrice: 达成交易的价格
    :TxnFees: 与交易事务相关的费用，如佣金
    :ConMult: 来自证券数据的乘数因子

返回值
    TxnValue：交易的总金额，包括费用
