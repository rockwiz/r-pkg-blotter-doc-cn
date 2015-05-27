TotalRisk
=========

描述
    总风险的平方等于系统风险平方与特定风险平方之和。特定风险是回归方程中误差项的标准差。计算总风险时系统风险和特定风险都需年化处理

用法
::

    TotalRisk(Ra, Rb, Rf = 0, ...)

参数
    .. math::

        TotalRisk=\sqrt{{SystematicRisk}^2+{SpecificRisk}^2}

说明

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.75

范例
::

    data(portfolio_bacon)
    print(TotalRisk(portfolio_bacon[,1], portfolio_bacon[,2])) #expected 0.0134

    data(managers)
    print(TotalRisk(managers[ 1996 ,1], managers[ 1996 ,8]))
    print(TotalRisk(managers[ 1996 ,1:5], managers[ 1996 ,8]))


