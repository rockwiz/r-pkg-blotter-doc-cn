.initPosPL
==========

描述
    为一个组合中的证券初始化头寸损益。

用法
::

    .initPosPL(initDate="1950-01-01", ..., initPosQty=0, initConMult=1, initCcyMult=1)

参数
    :initDate: 给定的第一个收盘价之前的日期，用于包含初始账户证券和初始头寸
    :...: 任何其它要传递的参数
    :initPosQty: 初始头寸，缺省是0
    :initConMult: 初始合约乘数因子，缺省是1
    :initCcyMult: 初始货币乘数因子，缺省是1

说明
    构造数据容器，用于存储从交易事务和收盘价计算而来的损益值（P&L values）。

    构造多列xts对象，用于存储派生的头寸信息
