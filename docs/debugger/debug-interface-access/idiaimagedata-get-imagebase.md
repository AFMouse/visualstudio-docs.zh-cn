---
title: IDiaImageData::get_imageBase | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de8c333391530cd86c6fc66a8e6c36ce8cfecd5f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623861"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
检索其中应基于映像的内存位置。

## <a name="syntax"></a>语法

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>参数
 `pRetVal`

[out]返回建议的图像的基值。

## <a name="return-value"></a>返回值
 如果成功，则返回`S_OK`; 否则为返回错误代码。

## <a name="remarks"></a>备注
 由于映像基冲突而进行映像可能会重新设定基址自动到未使用的内存位置在加载时。 此方法返回已在编译时存储在模块中的基本提示 （建议的内存位置）。

## <a name="see-also"></a>请参阅
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)