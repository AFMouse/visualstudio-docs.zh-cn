---
title: 错误：本地计算机上的防火墙 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 23290ebb12c2cb3e6bb12554aa9fbb89c4fb82fa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "58934022"
---
# <a name="error-firewall-on-local-machine"></a>错误：本地计算机上的防火墙
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本地计算机（运行 Visual Studio 的计算机）上的 Internet 连接防火墙未设置为允许远程调试。 为了使用默认传输进行托管或本机远程调试，必须为 DCOM 通信打开 TCP 135 端口。 必须打开文件和打印机共享，且必须将 devenv.exe 添加到例外列表。 可能还需要打开某些 IPSEC 端口。  
  
 有关详细信息，请参阅[设置 Up the Remote Tools 在设备上](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)。
