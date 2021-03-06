---
title: IActiveScriptProfilerControl5::EnumHeap2 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c90c536dee76d67fdb93dd205e8f6eedff6dcc7
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150798"
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>IActiveScriptProfilerControl5::EnumHeap2 方法
返回的接口 ([IActiveScriptProfilerHeapEnum 接口](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) 可用于循环访问关联的脚本引擎的上下文中的 GC 堆对象。  
  
 可以调用此方法在调试或发布模式。 UI 线程处于空闲状态时，应调用此方法。 调用该方法后，应执行任何操作的脚本引擎除外[iactivescriptprofilerheapenum:: Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)直到[iactivescriptprofilerheapenum:: Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)，则返回 S_FALSE 或[IActiveScriptProfilerHeapEnum 接口](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)释放接口指针。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>参数  
 enumFlags  
 值，该值指定是否公开有关对象关系中指向的对象的额外信息。 附加信息可能指示指向的对象是否为 getter 或 setter 方法。 有关详细信息，请参阅[PROFILER_HEAP_ENUM_FLAGS 枚举](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)。  
  
 ppEnum  
 [out]返回[IActiveScriptProfilerHeapEnum 接口](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)。  
  
## <a name="return-value"></a>返回值  
 返回一个 HRESULT。 可能的值如下：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|堆枚举已成功完成。|  
|`E_OUTOFMEMORY`|没有足够内存可用于执行堆枚举。|  
|`E_FAIL`|发生内部错误。|