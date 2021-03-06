---
title: CA2200:再次引发以保留堆栈详细信息
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 55c58f098616a5c3c2d6ad72f56e8eda51f689be
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "55935391"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200:再次引发以保留堆栈详细信息

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|类别|Microsoft.Usage|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因

引发异常和中显式指定的异常`throw`语句。

## <a name="rule-description"></a>规则说明

一旦引发异常，它携带的一部分是信息的堆栈跟踪。 堆栈跟踪是开头的方法引发的异常和结束的捕获的异常的方法的方法调用层次结构的列表。 如果通过指定在异常重新引发异常`throw`语句在当前方法中重新启动的堆栈跟踪和引发异常的原始方法与当前方法之间的方法调用列表将丢失。 若要保持与异常的原始堆栈跟踪信息，请使用`throw`而无需指定异常的语句。

## <a name="how-to-fix-violations"></a>如何解决冲突

若要解决此规则的冲突，重新引发异常，而无需显式指定异常。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告

不禁止显示此规则发出的警告。

## <a name="example"></a>示例

下面的示例演示一种方法， `CatchAndRethrowExplicitly`，这违反了规则和方法， `CatchAndRethrowImplicitly`，以及满足该规则。

[!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
[!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]