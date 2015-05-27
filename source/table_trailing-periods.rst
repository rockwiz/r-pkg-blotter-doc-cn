table.TrailingPeriods
=====================

描述
    滚动期间收益度量表

用法
::

    table.TrailingPeriods(R,  periods = subset(c(12,36,60), c(12,36,60)< length(as.matrix(R[,1]))),
                          FUNCS=c("mean","sd"), funcs.names = c("Average", "Std Dev"), digits = 4, ...)

    table.TrailingPeriodsRel(R, Rb, periods = subset(c(12,36,60), c(12,36,60)< length(as.matrix(R[,1]))),
                             FUNCS=c("cor","CAPM.beta"), funcs.names = c("Correlation", "Beta"), digits = 4, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 一个用来比较的指数、基准、组合或第二项资产的收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :periods: 滚动窗口的期数，c(3, 6, 9, 12, 18, 24, 36, 48)子集
    :funcs.names: 用来给表格行做标记的函数名称向量
    :FUNCS: 应用到滚动期（rolling period）的函数列表
    :digits: 进行四舍五入的指定位数
    :...: 任何其它传入FUNCS指定函数的参数

另见
    rollapply

范例
::

    data(edhec)
    #table.TrailingPeriods(edhec[,10:13], FUNCS=c("SharpeRatio","VaR"), funcs.names = c("Sharpe Ratio", "Modified VaR"),
    #                      periods=c(12,24,36))

    #result=table.TrailingPeriods(edhec[,10:13], FUNCS=c("SharpeRatio","VaR"),
    #                             funcs.names = c("Sharpe Ratio", "Modified VaR"), periods=c(12,24,36))

    table.TrailingPeriods(edhec[,10:13], periods=c(12,24,36))

    result=table.TrailingPeriods(edhec[,10:13], periods=c(12,24,36))
    require("Hmisc")
    textplot(format.df(result, na.blank=TRUE, numeric.dollar=FALSE, cdec=rep(3,dim(result)[2])),
             rmar = 0.8, cmar = 1.5,  max.cex=.9, halign = "center", valign = "top", row.valign="center",
             wrap.rownames=15, wrap.colnames=10, mar = c(0,0,3,0)+0.1)

    title(main="Trailing Period Statistics")

