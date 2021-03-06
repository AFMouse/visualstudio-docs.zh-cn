---
title: '&lt;程序集&gt;元素 （ClickOnce 部署） |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b77cfacf3dca2c2cc20d674f79929e9958a16d4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "58932509"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;程序集&gt;元素 （ClickOnce 部署）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

部署清单的的顶级元素。  
  
## <a name="syntax"></a>语法  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>元素和属性  
 `assembly`元素是根元素，是必需的。 它包含的第一个元素必须是`assemblyIdentity`元素。 清单元素必须在以下命名空间： `urn:schemas-microsoft-com:asm.v1`， `urn:schemas-microsoft-com:asm.v2`，和`http://www.w3.org/2000/09/xmldsig#`。 程序集的子元素也必须通过继承或使用标记，这些命名空间中。  
  
 `assembly` 元素具有以下属性。  
  
|特性|描述|  
|---------------|-----------------|  
|`manifestVersion`|必需。 此属性必须设置为`1.0`。|  
  
## <a name="example"></a>示例  
 下面的代码示例演示`assembly`部署使用的应用程序的部署清单中的元素[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]。 此代码示例是为提供一个更大示例的一部分[ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)主题。  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
```  
  
## <a name="see-also"></a>请参阅  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)   
 [\<assembly> 元素](../deployment/assembly-element-clickonce-application.md)
