---
title: 'Idiasymbol:: Get_lowerbound |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lowerBound method
ms.assetid: e9a6440b-d068-4de4-a240-6723d20812b9
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bfae7bc80935f0f2fab8e6290c9dd0edbdaacde
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "58935747"
---
# <a name="idiasymbolgetlowerbound"></a>IDiaSymbol::get_lowerBound
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

检索 FORTRAN 数组维度的下限。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT get_lowerBound (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pRetVal`  
 [out]返回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)对象，它表示 FORTRAN 数组维度的下限。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回`S_FALSE`或错误代码。  
  
> [!NOTE]
>  返回值为`S_FALSE`表示该属性不是可用于符号。  
  
## <a name="see-also"></a>请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
