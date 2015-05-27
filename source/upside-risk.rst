UpsideRisk
==========

描述
    上方风险同取高于MAR而不是均值收益或零的收益的半离差一样。要计算UpsideRisk，取高于目标或MAR收益的子集，
    然后取它们和目标间的差。求皮肤和，然后除以收益总个数，再返回平方根。

用法
::

    UpsideRisk(R, MAR = 0, method = c("full", "subset"), stat = c("risk","variance", "potential"), ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :MAR: 最小可接受收益，与收益的周期性相同
    :method: “full”或“subset”之一，指明用全序列的长度还是MAR之下序列子集的长度作为分母，缺省为“full”
    :stat: "risk", "variance" 或 "potential"之一，指明返回上方风险、方差或potential
    :...: 其它要传入的参数

说明
    .. math::

        UpsideRisk(R, MAR)=\sqrt{\sum^n_{t=1}\frac{{max[(R_t-MAR),0]}^2}{n}}

        UpsideVariance(R, MAR)=\sum^n_{t=1}\frac{{max[(R_t-MAR),0]}^2}{n}

        UpsidePotential(R, MAR)=\sum^n_{t=1}\frac{max[(R_t-MAR),0]}{n}

    其中，n是序列中所有观测样本数或落在MAR之下子集中观测样本数

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008

范例
::

    data(portfolio_bacon)
    MAR = 0.005
    print(UpsideRisk(portfolio_bacon[,1], MAR, stat="risk")) #expected 0.02937
    print(UpsideRisk(portfolio_bacon[,1], MAR, stat="variance")) #expected 0.08628
    print(UpsideRisk(portfolio_bacon[,1], MAR, stat="potential")) #expected 0.01771
    MAR = 0
    data(managers)
    print(UpsideRisk(managers[ 1996 ], MAR, stat="risk"))
    print(UpsideRisk(managers[ 1996 ,1], MAR, stat="risk")) #expected 1.820

