---
title: IDiaEnumStackFrames::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9cf220c65cf11836e64a7e1f4c0142c89669f4b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619441"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
枚举序列中检索指定的数量的堆栈帧元素。

## <a name="syntax"></a>语法

```C++
HRESULT Next( 
   ULONG             celt,
   IDiaStackFrame**  rgelt,
   ULONG*            pceltFetched
);
```

#### <a name="parameters"></a>参数
 celt

[in]要检索的枚举器中的堆栈帧元素数目。

 rgelt

[out]数组，它是与请求填写[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)对象。

 pceltFetched

[out]在提取枚举器返回堆栈数 frame 元素。

## <a name="return-value"></a>返回值
 如果成功，则返回 `S_OK`。 返回`S_FALSE`是否存在的堆栈帧。 否则，返回错误代码。

## <a name="see-also"></a>请参阅
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)