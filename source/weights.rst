weights
=======
描述
    挑选的投资组合权重数据。一个xts对象，包含EDHEC对冲基金指数子集的月度权重列，该子集用来演示随时间再平衡投资组合。

    注意，所有EDHEC 指数在edhec可得到。

用法
::

    managers

格式
    CSV，符合有月度观测值的xts对象

说明
    一个用于给范例绘图的相对随机的权重文件。

范例
::

    data(weights)
    # 预览数据
    head(weights)

