---
title: “打开项目”命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 916ea8435571efc01f38e408d4fc2d4563c16f1c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "54753480"
---
# <a name="open-project-command"></a>“打开项目”命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
打开现有项目。  
  
## <a name="syntax"></a>语法  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>自变量  
 `filename`  
 必需。 要打开的项目的完整路径和文件名。  
  
 `filename` 参数的语法要求用引号将包含空格的路径括起来。  
  
## <a name="remarks"></a>备注  
 键入内容时，自动完成功能会尝试查找正确的路径和文件名。  
  
 调试时此命令不可用。  
  
## <a name="example"></a>示例  
 此示例打开 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 项目 Test1。  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## <a name="see-also"></a>请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找/命令”框](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
