---
title: 如何：设置 ClickOnce 应用程序的自定义权限 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 279dd66ca1f814dbd52593d52040818edf8f408b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "58935518"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>如何：为 ClickOnce 应用程序设置自定义权限
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

可以部署对 Internet 或本地 Intranet 区域使用默认权限的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 应用程序。 或者，可以为应用程序所需的特定权限创建自定义区域。 可以通过在“项目设计器”  的“安全” 页上自定义安全权限来执行此操作。  
  
### <a name="to-customize-a-permission"></a>自定义权限  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击 **“安全”** 选项卡。  
  
3.  选中“启用 ClickOnce 安全设置”  复选框。  
  
4.  选择“这是部分可信的应用程序”  选项按钮。  
  
     “ClickOnce 安全权限”  部分中的控件已启用。  
  
5.  在“将要从中安装应用程序的区域”  下拉列表中，单击“(自定义)” 。  
  
6.  单击“编辑权限 XML” 。  
  
     随即会在“XML 编辑器”中打开 app.manifest 文件。  
  
7.  在 `</applicationRequestMinimum>` 元素之前，为应用程序所需的权限添加 XML 代码。  
  
    > [!NOTE]
    >  可以使用权限集的 `ToXml` 方法为应用程序清单生成 XML 代码。 例如，若要为 <xref:System.Security.Permissions.EnvironmentPermission> 权限集生成 XML，请调用 <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> 方法。 有关详细信息的结构的权限集 XML，请参阅[NIB:如何：通过使用 XML 文件的权限集的导入](http://msdn.microsoft.com/dea16b54-c108-408a-ac36-cdc05f746236)。  
  
## <a name="see-also"></a>请参阅  
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 应用程序的代码访问安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)
