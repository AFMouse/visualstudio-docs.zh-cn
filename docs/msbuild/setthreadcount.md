---
title: SetThreadCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 656e491e683c7ec2de23ea7e49938e833af3a295
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709611"
---
# <a name="setthreadcount"></a>SetThreadCount
设置全局线程计数，并将该计数分配给当前线程。

## <a name="syntax"></a>语法

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>参数
[in] `threadCount`

 要使用的线程数。

## <a name="return-value"></a>返回值
 线程数更新后，则返回带 SUCCEEDED 位集的 HRESULT。

## <a name="requirements"></a>要求
 **标头：** FileTracker.h