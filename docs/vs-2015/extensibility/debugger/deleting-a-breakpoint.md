---
title: 删除断点 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9a70cfe5b728cc9af019752bd0c9c9d2f5105043
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "58933415"
---
# <a name="deleting-a-breakpoint"></a>删除断点
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

下面介绍删除挂起断点时的过程：  
  
## <a name="deletion-process"></a>删除过程  
 会话调试管理器 (SDM) 调用[IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)方法移除挂起断点和所有绑定的断点绑定从它。  
  
> [!NOTE]
>  此外可以通过调用删除单个绑定的断点[IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)。  
  
## <a name="see-also"></a>请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)
