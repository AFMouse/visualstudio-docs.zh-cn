---
title: CPU 使用率图 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42995305b76acdda7f24fb7a45f717c9f2c174a2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2019
ms.locfileid: "56631245"
---
# <a name="cpu-utilization-graph"></a>CPU 使用率图
CPU 使用率图显示一段时间内应用中的使用程度。 X 轴表示跟踪的持续时间，Y 轴表示系统上的逻辑内核数。 此图形不显示在某个给定时间哪个特定内核处于活动状态。 例如，如果两个内核在某一给定时间段内均以 50% 的使用率运行，则此视图将显示使用一个逻辑内核。

## <a name="cpu-utilization-graph-colors"></a>CPU 使用率图颜色

-   绿色表示系统中当前进程的逻辑内核使用率。

-   浅灰色表示系统上其他进程的逻辑内核利用率。 如果 CPU 图中的浅灰色百分比过高，则表示其他进程已使系统负载过重，您的进程可能会被这些进程抢占资源。 若要减少其他进程使用的逻辑内核数，请减少系统上运行的逻辑内核数。

-   深灰色表示系统进程的逻辑内核消耗。 您无法直接控制这部分逻辑内核消耗，但由于这些消耗会影响您的进程可以使用的逻辑内核情况，因此了解这些消耗何时出现非常有用。

-   白色表示系统上未使用逻辑内核的可用性。 如果可以找到更多的并行机会，这些核心则可用于你的进程。

## <a name="see-also"></a>请参阅
- [使用率视图](../profiling/utilization-view.md)
- [CPU 平均使用率](../profiling/average-cpu-utilization.md)