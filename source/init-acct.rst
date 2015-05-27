initAcct
========

描述
    构建数据容器，用于存储计算后的账户数值，如归集损益（aggregated P&L）、证券（equity）

用法
::

    initAcct(name="default", portfolios, initDate="1950-01-01", initEq=0, currency="USD", ...)

参数
    :name: 账户名称，字符串
    :portfolios: 包含在该账户中的组合名称，字符串
    :initDate: 给定的第一个收盘价之前的日期，用于包含初始账户证券和初始头寸
    :currency: ISO 货币标识符，用于本地化组合货币
    :initEq: 以浮点数表示的基于组合货币的初始账户证券
    :...: 任何其它要传递的参数

说明
    输入组合：一个附属于该账户的组合对象的名称列表。

    | initDate：给定的第一个收盘价之前的日期，用于包含初始账户证券和初始头寸
    | initEq：初始证券或起始资金，缺省为100,000

    输出构建多列xts对象，用于存储归集后的组合计算结果

    注意，一个账户对象是附带组合概要信息的组合列表

    账户对象按CFTC的 13列展示表建模。以CFTC的6列展示开始，包括：Beg.Eq、Additions、Withdrawals、Net.Perf、End.Eq、Period.ROR。没有理由持久化Period.ROR，并且Beg.Eq = Previous End.Eq，因此我们留下4列。注意， Period.ROR可被以不同方式计算，因而最好保留作为一个函数。

    要达到CFTC的13列，添加：Gross.Realized、Commission、Net.Realized、Int.Income、Ch.Unrealized、Advisory.Fees、Wealth.Index。再次，没有必要添加Wealth.Index。最终，这些附加列都会有用。Gross.Realized 将以as (Net) Realized.PL + Txn.Fees计算。
