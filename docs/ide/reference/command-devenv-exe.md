---
title: -Command (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6daa21f9db7eef9a651577ad829d884dccf353dc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717515"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

在启动 Visual Studio IDE 后执行指定命令。

## <a name="syntax"></a>语法

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>自变量

CommandName

必需。 Visual Studio 命令或其别名的完整名称（放在双引号中）。 有关命令和别名语法的详细信息，请参阅 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)。

## <a name="remarks"></a>备注

启动完成后，IDE 将执行已命名的命令。

::: moniker range="vs-2017"

如果使用此开关，IDE 将不会在启动时显示起始页。

::: moniker-end

如果外接程序公开了某个命令，则可以使用此开关从命令行启动此外接程序。 有关详细信息，请参阅[如何：使用加载项管理器控制加载项](/previous-versions/xwdatdwh(v=vs.140))。

## <a name="example"></a>示例

第一个示例启动 Visual Studio，并自动运行宏“打开收藏夹文件”。

第二个示例在 IDE 内打开 Web 浏览选项卡，并转到 Microsoft Docs 站点。

第三个示例新建名为 `some_file.cs` 的文件，并在代码编辑器中打开它。

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>请参阅

- [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
- [“命令”窗口](command-window.md)