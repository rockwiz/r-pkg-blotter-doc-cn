VolatilitySkewness
==================

描述
    波动偏度和omega测度一样，但使用二阶偏动量，是上方方差和下方方差的比值。可变偏度是上方风险和下方风险之间比值

用法
::

    VolatilitySkewness(R, MAR = 0, stat = c("volatility", "variability"), ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :MAR: 最小可接受收益，与收益的周期性相同
    :stat: "volatility"或"variability"之一，指明返回波动偏度还是可变偏度
    :...: 其它要传入的参数

说明
    .. math::

        VolatilitySkewness(R, MAR)=\frac{\sigma^2_U}{\sigma^2_D}

        VariabilitySkewness(R, MAR)=\frac{\sigma_U}{\sigma_D}


    其中，:math:`\sigma_U` 是上方风险， :math:`\sigma_D` 是下方风险

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.97-98

范例
::

    data(portfolio_bacon)
    MAR = 0.005
    print(VolatilitySkewness(portfolio_bacon[,1], MAR, stat="volatility")) #expected 1.32
    print(VolatilitySkewness(portfolio_bacon[,1], MAR, stat="variability")) #expected 1.15
    MAR = 0
    data(managers)
    # print(VolatilitySkewness(managers[ 1996 ], MAR, stat="volatility"))
    print(VolatilitySkewness(managers[ 1996 ,1], MAR, stat="volatility"))

