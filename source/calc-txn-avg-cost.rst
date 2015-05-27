calcTxnAvgCost
==============

描述
    计算一个按股数或按合约的交易成本，以匹配计价单位
用法
::

    calcTxnAvgCost(TxnValue, TxnQty, ConMult=1)

参数
    :TxnValue: 交易的总价值，包括费用
    :TxnQty: 交易的总数量units (shares)
    :ConMult: 来自证券数据的乘数因子

返回值
    TxnAvgCost：交易的归一化成本（按股数）
