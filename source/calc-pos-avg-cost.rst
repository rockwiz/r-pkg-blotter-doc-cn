calcPosAvgCost
==============

描述
    计算一个交易后头寸的平均成本。

用法
::

    calcPosAvgCost(PrevPosQty, PrevPosAvgCost, TxnValue, PosQty, ConMult=1)

参数
    :PrevPosQty: 之前头寸的数量
    :PrevPosAvgCost: 之前头寸的平均头寸成本
    :TxnValue: 交易的总价值，包括费用
    :PosQty: 交易形成的头寸的总数量
    :ConMult: 来自证券数据的乘数因子

返回值
    PosAvgCost：交易形成的头寸的平均成本
