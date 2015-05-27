PortfReturns
============

描述
    计算组合证券收益

用法
::

    PortfReturns(Account, method=c("contribution"), ..., Dates, Portfolios)

参数
    :Account: 要生成收益的账户的字符串名称
    :method: 目前仅支持“contribution”
    :...: 任何其它要传递的参数 （like native for .getBySymbol）
    :Dates: xts风格ISO 8601日期子集，缺省为NULL （所有日期）
    :Portfolios: 要获取收益的组合名称的串连字符串向量，缺省为NULL（所有组合）

说明
    该函数（到目前为止）计算组成账户的组合中每支证券的初始资产收益率。这些列将附加到每个组合或整个账户的资本收益率。
