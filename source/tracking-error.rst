TrackingError
=============

描述
    计算收益相对基准追踪误差（绩效相对基准中无法解释部分的度量）

用法
::

    TrackingError(Ra, Rb, scale = NA)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）

说明
    追踪误差通过取投资者收益和基准收益之间平方偏差平均值的平方根，然后将结果乘以收益期数（scale）平方根计算而来。

    .. math::

        TrackingError=\sqrt{\sum{\frac{{(R_a-R_b)}^2}{len(R_\alpha)\sqrt{scale}}}}\centerdot\sqrt{scale}

参考
    Sharpe, W.F. The Sharpe Ratio,Journal of Portfolio Management,Fall 1994, 49-58.

另见
    InformationRatio TrackingError

范例
::

    data(managers)
    TrackingError(managers[,1,drop=FALSE], managers[,8,drop=FALSE])
    TrackingError(managers[,1:6], managers[,8,drop=FALSE])
    TrackingError(managers[,1:6], managers[,8:7,drop=FALSE])

