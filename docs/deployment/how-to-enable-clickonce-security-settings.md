---
title: 如何： 启用 ClickOnce 安全设置 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f89db12596754630eddaf78b9429eb2983625481
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599828"
---
# <a name="how-to-enable-clickonce-security-settings"></a>如何：启用 ClickOnce 安全设置
若要发布应用程序，必须启用 ClickOnce 应用程序的代码访问安全性。 当您发布应用程序使用发布向导时，这是自动完成。

 在某些情况下，启用代码访问安全性可能会影响性能时生成或调试应用程序;在这些情况下，你可能想要暂时禁用的安全设置。

 ClickOnce 安全设置可以启用或禁用**安全**页**项目设计器**。

### <a name="to-enable-clickonce-security-settings"></a>若要启用 ClickOnce 安全设置

1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。

2.  单击 **“安全”** 选项卡。

3.  选中“启用 ClickOnce 安全设置”  复选框。

     现在，您可以为安全性页上的应用程序定制的安全设置。

    > [!NOTE]
    >  每次通过发布应用程序会自动选中此复选框**发布**向导。

### <a name="to-disable-clickonce-security-settings"></a>若要禁用 ClickOnce 安全设置

1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。

2.  单击 **“安全”** 选项卡。

3.  清除**启用 ClickOnce 安全设置**复选框。

     将使用完全信任安全设置; 运行你的应用程序上的任何设置**安全**页将被忽略。

    > [!NOTE]
    >  使用发布向导发布应用程序每次将选中此复选框;每次成功发布后，您必须清除它。

## <a name="see-also"></a>请参阅
- [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)
- [ClickOnce 应用程序的代码访问安全性](../deployment/code-access-security-for-clickonce-applications.md)
