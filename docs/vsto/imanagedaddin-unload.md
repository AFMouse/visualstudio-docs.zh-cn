---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 296502aa461688c34152d86ee21aab5f2c83ecb4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640488"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  只在托管 VSTO 外接程序卸载之前调用。

## <a name="syntax"></a>语法

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>返回值
 HRESULT 值，指示方法是否已成功完成。

## <a name="remarks"></a>备注
 当前版本的 Microsoft Office 不调用此方法。 此方法保留供将来使用。

## <a name="see-also"></a>请参阅
- [IManagedAddin 接口](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Load](../vsto/imanagedaddin-load.md)
