---
title: SccProperties 函数 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7bb8fd8172468dc1fc4d60d0f5e36ee7b4f9a588
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47470607"
---
# <a name="sccproperties-function"></a>SccProperties 函数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[SccProperties 函数](https://docs.microsoft.com/visualstudio/extensibility/sccproperties-function)。  
  
此函数显示文件或项目的源控件属性。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源控制插件上下文结构。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 lpFileName  
 [in]项目的文件的完全限定的路径名称。  
  
## <a name="return-value"></a>返回值  
 此函数的源控制插件实现应返回以下值之一：  
  
|“值”|描述|  
|-----------|-----------------|  
|SCC_OK|已成功显示属性。|  
|SCC_I_RELOADFILE|版本控制系统已修改文件属性，因此 IDE 应重新加载此文件。|  
|SCC_E_PROJNOTOPEN|尚未在源代码管理中打开指定的项目。|  
|SCC_E_NOTAUTHORIZED|用户无权查看此文件或项目的属性。|  
|SCC_E_FILENOTCONTROLLED|指定的文件或项目不受源代码管理。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|出现未知或常规错误。|  
  
## <a name="remarks"></a>备注  
 源代码管理插件在其自己的对话框中显示的属性。  
  
 这些属性定义的源代码管理插件和插件可能不同于插件。 如果该插件允许用户更改文件的源控件属性，它应返回`SCC_I_RELOAD`以指示需要重新加载此文件或项目的 IDE。  
  
## <a name="see-also"></a>请参阅  
 [源代码管理插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)
