table.Variability
=================

描述
    均值绝对差、月度标准差以及年化标准差表

用法
::

    table.Variability(R, scale = NA, geometric = TRUE, digits = 4)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）
    :geometric: 生成几何（TRUE）或简单（FALSE）收益，缺省为TRUE
    :digits: 进行四舍五入的指定位数

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.65

另见
    StdDev.annualized MeanAbsoluteDeviation

范例
::

    data(managers)
    table.Variability(managers[,1:8])

    require("Hmisc")
    result = t(table.Variability(managers[,1:8]))

    textplot(format.df(result, na.blank=TRUE, numeric.dollar=FALSE, cdec=c(3,3,1)),
             rmar = 0.8, cmar = 2, max.cex=.9, halign = "center", valign = "top",
             row.valign="center", wrap.rownames=20, wrap.colnames=10,
             col.rownames=c("red", rep("darkgray",5), rep("orange",2)), mar = c(0,0,3,0)+0.1)
    title(main="Portfolio variability")


