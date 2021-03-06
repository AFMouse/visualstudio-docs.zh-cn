---
title: 使用代码图分析器查找潜在问题
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fd3bb1537d0e985e91f93ea094ec546ed9a6092
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "55912334"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>使用代码图分析器查找潜在问题

在代码图上运行分析器以帮助识别可能过于复杂或者可能需要改进的代码。 例如，可以使用以下分析器：

|**查找所需代码**|**检查这些区域，以确定是否**|
|-|-|
|循环依赖项|可以简化它们，并考虑是否可以中断这些循环。|
|依赖项太多|它们将执行很多功能或确定更改这些区域的影响。 格式正确的代码图将显示最少数目的依赖项。 若要使代码更易于维护、更改、测试和重复使用，请考虑是否重构这些区域，以使它们更清楚地定义，或是否可以合并执行类似功能的代码。|
|无依赖项|它们是必需项还是是否应删除此代码。|

## <a name="analyze-code-maps"></a>分析代码图

在代码图工具栏上选择**布局** > **分析器**，和你想要运行然后分析器：

|**分析器**|**标识节点**|
|-|-|
|**循环引用分析器**|每个其他节点上也具有循环依赖项。 **注意：** 中的循环依赖关系**泛型**组时不会显示在地图上相应的组。|
|**查找中心分析器**|位于前 25% 个高度连接的节点当中<br /><br /> **若要隐藏代码图上的所有其他节点**<br /><br /> -打开代码图的快捷菜单中，选择**高级**，**选择**，**隐藏未选内容**。<br />     代码图会隐藏未选定的节点，并且分析器会将新节点标识为中心。|
|**未引用的节点分析器**|不具有来自任何其他节点的引用。 注意：在假设不使用代码之前，验证每种情况。 不能在代码中以静态方式找到某些依赖项，如 XAML 依赖项和运行时依赖项。|

在你应用代码图分析器之后，它们将继续运行。 如果更改代码图，应用的任何分析器将自动重新处理更新的代码图。 若要停止运行分析器，请在代码图工具栏上，选择**布局** > **分析器**。 关闭所选的分析器。

> [!TIP]
> 如果你的代码图非常大，运行分析器则可能导致内存不足异常。 如果发生这种情况，请编辑代码图以减小其范围，或者生成一个较小的代码图，然后运行分析器。

## <a name="see-also"></a>请参阅

- [映射解决方案中的依赖项](../modeling/map-dependencies-across-your-solutions.md)
- [使用代码图调试应用程序](../modeling/use-code-maps-to-debug-your-applications.md)
- [调试时映射调用堆栈上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
