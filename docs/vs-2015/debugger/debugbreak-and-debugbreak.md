---
title: DebugBreak 和 __debugbreak |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7d26d78cf5e1995c25560e70e46ee4f6fde3a25
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "58937233"
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak 和 __debugbreak
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

可以在代码中的任意点调用 DebugBreak Win32 函数或 [__debugbreak](http://msdn.microsoft.com/library/1d1e1c0c-891a-4613-ae4b-d790094ba830) 内部函数。 `DebugBreak` 和 `__debugbreak` 具有与在该位置设置断点相同的效果。  
  
 由于 `DebugBreak` 是对系统函数的调用，因此必须安装系统调试符号，以确保中断后显示正确的调用堆栈信息。 否则，调试器可能在显示一条调用堆栈信息后就停止显示。 如果使用 `__debugbreak`，则不需要符号。  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](http://msdn.microsoft.com/library/48bb9929-7d78-4fd8-a092-ae3c9f971858)   
 [调试器安全](../debugger/debugger-security.md)   
 [调试本机代码](../debugger/debugging-native-code.md)   
 [指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
