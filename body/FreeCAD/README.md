# FreeCAD

FreeCAD 是一个通用的参数化三维计算机辅助设计(CAD)建模应用程序，主要用于设计现实生活中的物体。参数建模是建模类型之一，在这种建模方式中，设计的3D对象的形状由参数控制。例如，砖的形状可能由三个参数控制：高度，宽度和长度。这些参数是对象的一部分，即使创建对象后，也可以随时修改。除了简单的值，对象可以将其他对象作为参数。例如，您可以具有将砖作为输入的对象，并从中创建列。您可以将一个参数对象视为一个从参数创建几何形状的小程序。

## Workbench 

Workbenches are groups of tools (toolbar buttons, menus, and other interface controls) that are grouped together by specialty. Think of a workshop where you have different people working together: A person who works with metal, another with wood. Each of them has, in their workshop, a separate table with specific tools for his/her job. However, they can all work on the same objects. The same happens in FreeCAD.

The same tool may appear in more than one workbench. The button icon for a particular tool will always be the same no matter which workbench it appears in.


- Part + Sketcher
    The Part Workbench provides basic tools for working with solid parts: primitives, such as cubes and spheres, and simple geometric operations and boolean operations. Being the main anchor point with OpenCasCade, the Part workbench provides the foundation of FreeCAD's geometry system, and almost all other workbenches produce Part-based geometry.

- Part Design + Sketcher
    The objects created with the Part Workbench are relatively simple; they are intended to be used with boolean operations (unions and cuts) in order to build more complex shapes. This modeling paradigm is known as the constructive solid geometry (CSG) workflow, and it was the traditional methodology used in early CAD systems. On the other hand, the PartDesign Workbench provides a more modern workflow to constructing shapes: it uses a parametrically defined sketch, that is extruded to form a basic solid body, which is then modified by parametric transformations (feature editing), until the final object is obtained.

- Arch + Draft
    The Arch Workbench contains tools to work with BIM projects (civil engineering and architecture).

- Draft
    The Draft Workbench provides tools to do basic 2D CAD drafting tasks: lines, circles, etc... and a series of generic handy tools such as move, rotate or scale. It also provides several drawing aids, such as grid and snapping. It is principally meant to draw the guidelines for Arch objects, but also serves as FreeCAD's "swiss knife".


**Part 工作台为 FreeCAD 的几何系统提供了基础， 大多数其他工作台都是在零件工作台之上构建其功能的。**

**新手最好不要混用 Part 和 Part Design 工作台，直到完全掌握其中之一并理解其中的原理，两者有很多完成相同目的但是不同命的操作，容易让新手困惑，而另一些操作看起来一样，但是却作用于不同的对象。更好的组合是 Part + Sketcher 和 Part Design + Sketcher 两者组合之一。**

1. 必须在 PartDesign 创建一个实体（Body）再绘制草图，才能填充（Pad）成为一个三维物体。直接创建的草图不能只能是二位的。

2. 草图必须 `完全约束`，才能进行填充（Pad）,否则无法成功。

## 建模

FreeCAD 没有采用传统的 CSG（Constructive Solid Geometry 构造实体几何，使用三角形来表示模型表面）来作为主要建模方式。而是使用 BREP（Boundary Representation 边界表示）几何。BREP 对象的表面由数学曲线定义，这允许绝对的精度，无论尺度如何。但这并不代表 FreeCAD 只能操作 BREP 几何，FreeCAD 同样提供了 Mesh Workbench 来操作网格几何，同时提供了工具来将两者相互转换。但是提供的 Mesh 操作功能相对简单。

尽管其他工作台通常提供更高级的工具来构建和操作几何，但由于它们实际上都在操作Part对象，因此了解这些对象的内部工作方式并能够使用Part工具是非常有用的，因为它们更简单，通常可以帮助您解决更智能的工具无法正确解决的问题。