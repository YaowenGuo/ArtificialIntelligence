# Sketcher

主要功能分类：
- 通用工具
    - 草图工具
        - 创建
        - 编辑
        - 将草图映射到面上
        - 重定位草图
        - 验证草图
        - 合并
        - 镜像
    
    - 编辑模式工具
        - 退出编辑
        - 查看草图
        - 截面视图

    - 工具（v0.21 引入）
        - 网格开关
        - 捕获开关
        - 渲染顺序配置

    - 其它
        - 结束操作

 - 几何创建工具
    - 点
    - 线
    - 弧
    - 圆
    - 二次曲线（Create conic）
        - 圆心椭圆
        - 三点椭圆
        - 椭圆弧
        - 双曲线弧
        - 抛物线弧
    - B样条线
        - 控制点B样条线
        - 封闭B样条线
        - 节点B样条线
        - 封闭节点B样条线
    - 折线
    - 矩形
    - 正多边形
    - 圆矩形（Slot 矩形的两端是半圆）
    - 圆角（Create fillet）
        - 圆角： 在两条非平行线之间创建圆角
        - 保留相交点创建圆角：保留两条非平行线的相交点，同时创建圆角
    - 截取：根据一个点截断线、园、弧
    - 延伸（Extend）：将直线或圆弧扩展到边界线、圆弧、椭圆、椭圆弧或空间中的一个点。
    - 拆分（Split）：将一条边一分为二，同时保留大部分约束条件。
    - 外部几何（External geometry）：创建连接到外部几何体的边缘。
    - 副本（Carbon copy）：复制另一个草图的几何形状
    - Toggle construction geometry: Toggles sketch geometry from/to construction mode. Construction geometry is shown in blue and is discarded outside of Sketch editing mode.


- 约束工具
    - 几何约束
        - 点重合
        - 点约束到线上
        - 竖直
        - 水平
        - 平行
        - 垂直
        - 相切
        - 相等
        - 对称
        - 阻塞：它阻止边缘移动，也就是说，它阻止其顶点改变其当前位置。对于固定B样条线的位置应该特别有用

    - 尺寸约束
        - 锁（Lock）： Constrains the selected item by setting vertical and horizontal distances relative to the origin, thereby locking the location of that item. These constraint distances can be edited later.
        - 水平距离
        - 竖直距离
        - 距离
        - 半径/直径
        - 角度

    - 特殊约束
        - 折射：约束两条线服从折射定律来模拟光通过界面。

    - 约束工具
        - 切换/退出引用约束
        - 启用/禁用约束

- 草图工具

- B样条工具

- 虚拟空间
