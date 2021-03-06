---
title: 如何：触发事件; 当编辑器失去焦点 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84cc3d8b2ed75184e4126b4ea1bb707108e60f21
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699361"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>如何：触发事件; 当编辑器失去焦点
有时有必要知道当编辑器失去焦点的窗口框架上。 例如，可能需要在代码窗口中提取代码后对其焦点不再位于编辑器中。 以下过程提供了为接收通知的编辑器失去焦点要遵循的步骤。

## <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>触发事件以响应编辑器失去焦点

1.  通过获取监视所选内容的事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>对象从<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>。

2.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A>并将其提供你<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>对象。

3.  在调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>，查找`elementid==SEID_WindowFrame`。

4.  测试`varValueNew`两个参数：

    1.  要查找该窗口框架。

    2.  您的程序会失去对该窗口框架的选择点。