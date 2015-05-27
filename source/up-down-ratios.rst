UpDownRatios
============

描述
    计算资产在上升和下跌市场中表现的矩阵，根据基准资产上升或下降期间度量。

用法
::

    UpDownRatios(Ra, Rb, method = c("Capture", "Number", "Percent"), side = c("Up", "Down"))

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :method: “Capture”、“Number”或“Percent”，指明要返回的度量
    :side: “上涨”或“下跌”市场统计量

说明
    该函数设计用来计算几个相关矩阵：

* Up (Down) Capture Ratio：基准上升（下降）时投资的复合收益除以基准上升（下降）时基准的复合收益的度量。值越大（小），越好。
* Up (Down) Number Ratio：同样，基准上升（下降）时投资的上升（下降）期数除以基准上升（下降）时基准的上升（下降）期数 的度量。
* Up (Down) Percentage Ratio：基准上升（下降）时投资绩效超过基准绩效的期数除以基准上升（下降）的期数。不像前两个矩阵，两种情况下，都是值越高越好。

参考
    Bacon, C. Practical Portfolio Performance Measurement and Attribution. Wiley. 2004. p. 47

范例
::

    data(managers)
    UpDownRatios(managers[,1, drop=FALSE], managers[,8, drop=FALSE])
    UpDownRatios(managers[,1:6, drop=FALSE], managers[,8, drop=FALSE])
    UpDownRatios(managers[,1, drop=FALSE], managers[,8, drop=FALSE], method="Capture")
    # Up Capture:
    UpDownRatios(managers[,1, drop=FALSE], managers[,8, drop=FALSE], side="Up", method="Capture")
    # Down Capture:
    UpDownRatios(managers[,1, drop=FALSE], managers[,8, drop=FALSE], side="Down", method="Capture")

