.getByPortf
===========

描述
    获取一个账户中每个组合的属性

用法
::

    .getByPortf(Account, Attribute, Dates)

参数
    :Account: 一个包含组合概要（portfolio summary）的账户对象
    :Attribute: 为每个证券设定的列名称
    :Dates: 日期子集，为xts风格的ISO 8601字符串

说明
    从组合概要表（portfolio summary table）中获取账户中每个组合的计算后的属性。装配进portfolio-by-time表，规范为账户货币。

    属性：典型为以下值之一：'Long.Value', 'Short.Value', 'Net.Value', 'Gross.Value', 'Txn.Fees', 'Realized.PL', 'Unrealized.PL', 'Trading.PL'

返回值
    按组合的普通xts对象
