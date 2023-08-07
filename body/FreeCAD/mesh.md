# Mesh 编辑

FreeCAD 的 mesh 操作分为六组：

- Mesh 和其它格式转换。包括导入/导出，实体转 Mesh 和 Mesh 转实体。

- Mesh 面操作

- Mesh 对象之间的布尔操作

- Mesh 面的裁剪和分割

- Mesh 对象的分割和合并

- Mesh 对象的分析和修复

## Mesh 和其它对象的转换

### 1. 导入和导出

从文件导入和导出到文件，过于简单不做赘述。

### 2. 从实体创建 Mesh

### 3. 直接创建简单的 Mesh 对象

### 4. [Mesh 转可编辑 Solid](https://www.youtube.com/watch?v=DOCMumn9Oww)

1. 导入 Mesh 文件 （stl，obj 等），切换到 Part 工作台

2. 选中要转换的 Mesh 物体，Menu -> Part -> Create shape from mesh.

3. 选中新创建的 shape, Menu -> Part -> Create a copy -> Refine shape

4. Menu -> Part -> Shape builder -> 选中 Solid from shell -> 切换 Model 视图选中 Refine 后的 shape -> 点 Create 创建，然后关闭即可。

5. 接下来创建一个 Part，其中添加一个 Body, 将创建的实体拖到 Body 中即可任意编辑。

## Mesh 面操作

- 协调网格对象的法线

- 翻转网格对象的法线

- Fill hools: 一次性修复对象表面的所有破洞。会让输入一个限制修补三角形的数量，超出限制数量的破洞不会被修复。

- Close hool: 通过点击破洞边缘的面来修复该面同方向的破洞。右键弹出菜单可结束修复。

- Add triangle: 通过点击三个点来创建一个三角形。

- Remove components: 通过选择三角形来删除。

- Smooth: 是对象整体更加圆滑，对于圆润的物体可能有比较好的操作效果。对于棱角的物体操作简直是毁容。

- Refinement: 需要安装 gmsh 的 sdk，并在命令操作面板填写路径。这个命令对于细分网格有比较好的效果，想要减少网格则不是那么方便，可能需要自己多调整限制条件来多试几次。不如使用 Path 操作中的 Refine 命令，需要先转化为 Shape，参看 [Mesh 转可编辑 Solid]。
- Decimation: 减少网格，对于平面有较好的操作效果。曲面操作不显著。

- Scale: 缩放

## 布尔操作

这个比较简单，就是多个对象之间的布尔运算。就是需要下载一个 OpenSCAD 软件来执行操作。

## Mesh 裁剪

- Cut mesh: 删除选中区域的（内/外）三角形。或者 split 创建新的删除对象。删除也会删除对向的三角形，规则有点没整明白。

- Trim Mesh: 也是选中区域，跟 Cut mesh 不同的是，会沿着选中先整齐切割，如果线跨国三角形，会把三角形切断。（切割规则也很迷惑）

- Trim mesh with a plane: 

## Mesh segmentation

## Mesh analyze
