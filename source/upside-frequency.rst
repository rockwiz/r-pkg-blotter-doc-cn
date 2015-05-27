UpsideFrequency
===============

描述
    取高于目标（或MAR）收益的收益子集，然后把该子集长度除以总收益个数

用法
::

    UpsideFrequency(R, MAR = 0, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :MAR: 最小可接受收益，与收益的周期性相同
    :...: 其它要传入的参数

说明
    .. math::

        UpsideFrequency(R, MAR)=\sum^n_{t=1}\frac{max[(R_t-MAR),0]}{R_t\times{n}}

    其中，n是序列中所有观测样本数

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.94

范例
::

    data(portfolio_bacon)
    MAR = 0.005
    print(UpsideFrequency(portfolio_bacon[,1], MAR)) #expected 0.542
    data(managers)
    print(UpsideFrequency(managers[ 1996 ]))
    print(UpsideFrequency(managers[ 1996 ,1])) #expected 0.75


