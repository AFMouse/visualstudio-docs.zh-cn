---
title: 工作流设计器的活动设计器时
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d9ea1f6bd42526eb0ea38c23cbf0f28c4346515
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953241"
---
# <a name="while-activity-designer"></a>While 活动设计器

<xref:System.Activities.Statements.While>活动在执行中包含的活动及其<xref:System.Activities.Statements.While.Body%2A>时指定<xref:System.Activities.Statements.While.Condition%2A>的计算结果为**true**。 包含的活动可能永远都不会执行。 如果希望所包含的活动至少执行一次，请改用 <xref:System.Activities.Statements.DoWhile> 活动。

## <a name="while-properties-in-workflow-designer"></a>工作流设计器中的 While 属性

下表列出最有用的 <xref:System.Activities.Statements.While> 活动属性并说明如何在设计器中使用它们。

|属性名|必需|用法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.While> 活动设计器在标头中的友好名称。 默认值为 While。 可以在编辑该值**属性**窗口或直接在活动设计器标头。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|
|<xref:System.Activities.Statements.While.Body%2A>|False|包含要执行的活动时<xref:System.Activities.Statements.While.Condition%2A>计算结果为**true**。|
|<xref:System.Activities.Statements.While.Condition%2A>|True|包含 Visual Basic 表达式求值以确定是否在活动<xref:System.Activities.Statements.While.Body%2A>要执行。|

## <a name="see-also"></a>请参阅

- [控制流](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)