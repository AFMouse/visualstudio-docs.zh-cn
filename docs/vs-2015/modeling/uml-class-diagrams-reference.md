---
title: UML 类图：引用 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.generalization.properties
- vs.teamarch.logicalclassdiagram.toolbox
- vs.teamarch.UMLModelExplorer.association
- vs.teamarch.common.unspecifiedtype.properties
- vs.teamarch.logicalclassdiagram.diagram
- vs.teamarch.UMLModelExplorer.logicalclassdiagram
- vs.teamarch.UMLModelExplorer.generalization
- vs.teamarch.common.unspecifiedtype
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: b7c88be0-0d86-4d65-af74-f37e8812d20f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 07930dc31651d11aedccc6c597070bbba62ff0b9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "58937008"
---
# <a name="uml-class-diagrams-reference"></a>UML 类图：参考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 类图描述在应用程序内部以及应用程序与其用户在通信时使用的对象和信息结构。 它描述的信息不具有对任何特定实现的引用。 它的类和关系可以采用许多方法来实现，例如数据库表、XML 节点或软件对象的组合。  
  
> [!NOTE]
>  本主题针对 UML 类图。 还有另一种类图，即 .NET 类图，它用于可视化程序代码。 有关详细信息，请参阅[设计和查看类和类型](http://go.microsoft.com/fwlink/?LinkId=142231)。  
  
 若要创建 UML 类图中，在**体系结构**菜单中，选择**新建 UML 或层关系图**。 有关如何绘制 UML 类图的详细信息，请参阅[UML 类图：指导原则](../modeling/uml-class-diagrams-guidelines.md)。 有关如何创建和绘制建模图的详细信息，请参阅[编辑 UML 模型和关系图](../modeling/edit-uml-models-and-diagrams.md)。  
  
 若要查看支持此功能的 Visual Studio 的版本，请参阅 [体系结构和建模工具的版本支持](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="reading-class-diagrams"></a>读取类图  
 本节中的表介绍可在 UML 类图上看到的元素。 有关这些元素的属性的信息，请参阅以下主题：  
  
- [UML 类图上类型的属性](../modeling/properties-of-types-on-uml-class-diagrams.md)  
  
- [UML 类图上特性的属性](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
- [UML 类图中操作的属性](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
- [UML 类图上关联的属性](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
  ![显示关系和属性的三个类](../modeling/media/uml-classovreading.png "UML_ClassOvReading")  
  
| **Shape** |       **元素**        |                                                                                                                                                             **说明**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **类**         |                                                           共享给定结构或行为特征的对象的定义。 有关详细信息，请参阅[uml 类型的属性的类图](../modeling/properties-of-types-on-uml-class-diagrams.md)。                                                            |
|     1     |        分类器        |                                                                                                             类、接口或枚举的通用名称。 组件、用例和参与者也是分类器。                                                                                                             |
|     2     | 折叠/展开控件 |                                                                                         如果看不到分类器的详细信息，则单击分类器左上角的扩展器。 可能还必须单击每段上的 [+]。                                                                                         |
|     3     |      **特性**       |   附加到每个分类器实例的类型化值。<br /><br /> 若要添加的属性，请单击**特性**部分，然后按**ENTER**。 键入该特性的签名。 有关详细信息，请参阅[属性的属性在 UML 类图](../modeling/properties-of-attributes-on-uml-class-diagrams.md)。   |
|     4     |      **Operation**       | 分类器的实例可执行的方法或函数。 若要添加操作，请单击**Operations**部分，然后按**ENTER**。 键入该操作的签名。 有关详细信息，请参阅[UML 操作的属性类图](../modeling/properties-of-operations-on-uml-class-diagrams.md)。 |
|     5     |     **关联**      |                                                                  两个分类器的成员之间的关系。 有关详细信息，请参阅[属性关联在 UML 类图](../modeling/properties-of-associations-on-uml-class-diagrams.md)。                                                                   |
|    5a     |     **聚合**      |                                                                                                    表示共享所有权关系的关联。 **聚合**所有者角色的属性设置为**共享**。                                                                                                     |
|    5b     |     **组合**      |                                                                                                      表示整体-部分关系的关联。 **聚合**所有者角色的属性设置为**复合**。                                                                                                      |
|     6     |   **关联名称**   |                                                                                                                                         关联的名称。 该名称可以留空。                                                                                                                                          |
|     7     |      **角色名称**       |                       角色（即关联的一端）的名称。 可用于引用关联对象。 在前面的图示中，对于任何“订单”`O`，`O.ChosenMenu` 是其关联菜单。<br /><br /> 每个角色都有自己的属性，这些属性列在关联的属性下。                       |
|     8     |     **重数**     |                                         指示此端有多少个对象可以链接到另一端的每个对象。 在该示例中，每个“订单”必须链接到正好一个“菜单”。<br /><br /> **\\**\* 表示可为的链接数没有上限。                                         |
|     9     |    **泛化**    |  *特定*分类器继承从其定义的一部分*常规*分类器。 通用分类器位于连接线的箭头端。 特定分类器继承特性、关联和操作。<br /><br /> 使用**继承**工具来创建两个分类器之间泛化。   |
  
 ![包包含接口和枚举](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")  
  
|形状|元素|描述|  
|-----------|-------------|-----------------|  
|10|**Interface**|对象的部分外部可见行为的定义。 有关详细信息，请参阅[uml 类型的属性的类图](../modeling/properties-of-types-on-uml-class-diagrams.md)。|  
|11|**枚举**|由一组文本值组成的分类器。|  
|12|**包**|一组分类器、关联、操作、生命线、组件和包。 逻辑类图表示包中包含成员分类器和成员包。<br /><br /> 名称的作用域内的包，以便**Class1**内**Package1**不同于**Class1**该包外的。 包的名称显示为的一部分**限定名**其内容的属性。<br /><br /> 可以设置**链接的包**来指包的任何 UML 关系图的属性。 在该关系图上创建的所有元素随后都将成为该包的一部分。 它们将显示在包之下**UML 模型资源管理器**。|  
|13|**Import**|包之间的关系，指示一个包中包括另一个包的所有定义。|  
|14|**依赖关系**|如果箭头端的分类器发生更改，则依赖分类器的定义或实现可能会更改。|  
  
 ![显示与连接器和棒糖形的实现](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")  
  
|形状|**元素**|描述|  
|-----------|-----------------|-----------------|  
|15|**实现**|该类实现由接口定义的操作和特性。<br /><br /> 使用**继承**工具可创建一个类和接口之间实现。|  
|16|**实现**|同一关系的可选表示形式。 棒糖形符号上的标签用于标识接口。<br /><br /> 若要创建此表示形式，请选择一个现有实现关系。 关联附近将显示一个操作标记。 单击该操作标记，然后依次**显示为棒糖形**。|  
  
## <a name="see-also"></a>请参阅  
 [编辑 UML 模型和关系图](../modeling/edit-uml-models-and-diagrams.md)   
 [UML 类关系图：指导原则](../modeling/uml-class-diagrams-guidelines.md)   
 [UML 类图上类型的属性](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [UML 类图上特性的属性](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [UML 类图上的操作的属性](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [UML 类图上关联的属性](../modeling/properties-of-associations-on-uml-class-diagrams.md)
