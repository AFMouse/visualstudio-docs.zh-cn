---
title: IActiveScriptParseProcedureOld 接口 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99fa06086bfad56b266b043716e82181aa4c97d5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160623"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld 接口
允许源代码文本有关添加到脚本中的过程。 对于已解释的脚本语言不具有独立的创作环境，例如 VBScript 中，这提供了一种替代机制 (而不`IActiveScriptParse`或`IPersist*`) 添加到命名空间的脚本过程。  
  
> [!NOTE]
>  此接口已弃用的`IActiveScriptParseProcedure`接口。  
  
## <a name="methods"></a>方法  
 除了继承的方法之外`IUnknown`，则`IActiveScriptParseProcedureOld`接口公开以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|分析给定的代码过程并将该过程添加到命名空间。|  
  
## <a name="see-also"></a>请参阅  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)