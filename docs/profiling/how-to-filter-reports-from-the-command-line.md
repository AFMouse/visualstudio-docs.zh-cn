---
title: 如何：从命令行筛选报表 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c90ca0bea8126308b1260258044cece53218fb3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624290"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>如何：从命令行筛选报告
通过使用 VSPerfReport 命令选项，可以根据分析数据文件的特定时间段筛选报告，或将数据限制到一个或多个进程或线程。 有关此命令的详细信息，请参阅 [VSPerfReport](../profiling/vsperfreport.md)。

|选项|说明|
|-------------|-----------------|
|**StartTime:**[*Value*]|仅显示此值（以毫秒为单位）之后收集的数据。|
|**EndTime:**[*Value*]|仅显示此值（以毫秒为单位）之前收集的数据。|
|**FilterFile:** `VSPFFile`|指定从“Visual Studio 性能报告”窗口生成的筛选器文件的位置。|
|**MsFilter:**[*StartTime,Duration*]|仅显示从 `StartTime` 到 `Duration` 之间的数据（以毫秒为单位）。|
|**Process:**[*Pid*]|仅显示来自指定进程的数据。|
|**Thread:**[*ThreadID*]|仅显示来自指定线程的数据。|
|**Thread:**[*ThreadID,ProcessID*]|仅显示与指定进程相关的指定线程的数据。|