---
title: DoWhile 活动设计器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d09954409baccfdc5d9eb083a15bd02f5d16cb85
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "58933122"
---
# <a name="dowhile-activity-designer"></a>DoWhile 活动设计器
<xref:System.Activities.Statements.DoWhile>活动在执行中包含的活动及其<xref:System.Activities.Statements.DoWhile.Body%2A>至少一次，直到指定的条件的计算结果为**false**。 如果需要执行循环体中包含的活动零次或多次，请改用 <xref:System.Activities.Statements.While> 活动。  
  
## <a name="dowhile-properties-in-the-workflow-designer"></a>工作流设计器中的 DoWhile 属性  
 下表列出最有用的 <xref:System.Activities.Statements.DoWhile> 活动属性并说明如何在设计器中使用它们。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|要执行该条件时的活动 **，则返回 true**。 若要添加<xref:System.Activities.Statements.DoWhile.Body%2A>活动，将活动从工具箱拖到拖**正文**框**DoWhile**带提示文本"此处放置活动"的活动设计器。|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|每次循环迭代后要计算的条件。 若要设置<xref:System.Activities.Statements.DoWhile.Condition%2A>，键入[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]中的表达式**条件**框**DoWhile**活动设计器或在属性网格中。|  
  
## <a name="see-also"></a>请参阅  
 [时](../workflow-designer/while-activity-designer.md)   
 [控制流](../workflow-designer/control-flow-activity-designers.md)