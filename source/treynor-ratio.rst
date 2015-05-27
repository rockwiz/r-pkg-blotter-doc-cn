TreynorRatio
============
描述
    计算超额收益相对CAPM beta的Treynor 比率。Treynor与夏普比率（Sharpe Ratio）一样，除了它使用beta作为波动性度量
    （除以投资者相对beta的超额收益）。

用法
::

    TreynorRatio(Ra, Rb, Rf = 0, scale = NA)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :Rf: 与收益同时期的无风险收益率
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）

说明
    方程 :math:`\frac{\overline{(R_a-R_f)}}{\beta_{a,b}}`

参考
    http://en.wikipedia.org/wiki/Treynor_ratio

另见
    SharpeRatio SortinoRatio CAPM.beta

范例
::

    data(managers)
    round(TreynorRatio(managers[,1,drop=FALSE], managers[,8,drop=FALSE], Rf=.035/12),4)
    round(TreynorRatio(managers[,1,drop=FALSE], managers[,8,drop=FALSE], Rf = managers[,10,drop=FALSE]),4)
    round(TreynorRatio(managers[,1:6], managers[,8,drop=FALSE], Rf=.035/12),4)
    round(TreynorRatio(managers[,1:6], managers[,8,drop=FALSE], Rf = managers[,10,drop=FALSE]),4)
    round(TreynorRatio(managers[,1:6], managers[,8:7,drop=FALSE], Rf=.035/12),4)
    round(TreynorRatio(managers[,1:6], managers[,8:7,drop=FALSE], Rf = managers[,10,drop=FALSE]),4)

