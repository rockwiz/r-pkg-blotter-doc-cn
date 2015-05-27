updateEndEq
===========

描述
    更新一个账户的最终证券

用法
::

    updateEndEq(Account, Dates)

参数
    :Account: 标识账户的字符串
    :Dates: 证券计算的开始日期

说明
    计算End.Eq和Net.Performance

    需要updateAcct已经运行，并且其它辅助函数已经将有关信息附加到表中（例如，additions或 withdrawals、fees、interest等等）
