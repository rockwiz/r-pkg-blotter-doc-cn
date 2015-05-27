table.SpecificRisk
==================

描述
    特定风险、系统风险和总风险表

用法
::

    table.SpecificRisk(Ra, Rb, Rf = 0, digits = 4)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :Rf: 与收益同时期的无风险收益率
    :digits: 进行四舍五入的指定位数

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.76

另见
    SystematicRisk SpecificRisk TotalRisk

范例
::

    data(managers)
    table.SpecificRisk(managers[,1:8], managers[,8])

    require("Hmisc")
    result = t(table.SpecificRisk(managers[,1:8], managers[,8], Rf=.04/12))

    textplot(format.df(result, na.blank=TRUE, numeric.dollar=FALSE, cdec=c(3,3,1)),
             rmar = 0.8, cmar = 2, max.cex=.9, halign = "center", valign = "top",
             row.valign="center", wrap.rownames=20, wrap.colnames=10,
             col.rownames=c("red", rep("darkgray",5), rep("orange",2)), mar = c(0,0,3,0)+0.1)
    title(main="Portfolio specific, systematic and total risk")


