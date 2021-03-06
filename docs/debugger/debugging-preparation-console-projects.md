---
title: 准备调试控制台项目 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f94dcc62b829078fb8efc43ef92ddb203e1a1e32
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709234"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>调试准备： 控制台项目 (C#，c + +、 Visual Basic 中， F#)

准备调试控制台项目类似于准备调试 Windows 项目，但是有一些额外的注意事项。 有关详细信息，请参阅[Windows 窗体应用程序](../debugger/debugging-preparation-windows-forms-applications.md)，和[调试准备：Windows 窗体应用程序 (.NET)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100))。 由于所有控制台应用程序的相似性，本主题介绍以下项目类型：

- C#Visual Basic 中，并F#控制台应用程序

- C++ 控制台应用程序 (.NET)

- C++ 控制台应用程序 (Win32)

  可能必须为控制台应用程序指定命令行自变量。 有关详细信息，请参阅[c + + 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)， [Visual Basic 调试配置的项目设置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)，或[项目设置为C#调试配置](../debugger/project-settings-for-csharp-debug-configurations.md)。

  同所有项目属性一样，这些参数将在调试会话之间和 Visual Studio 会话之间保留。 因此，如果控制台应用程序是以前调试过的，请记得在“\<项目”>“属性页”对话框中可能输入了先前会话中的参数。

  控制台应用程序使用“控制台”窗口接受输入以及显示输出消息。 要写入到**控制台**窗口中，你的应用程序必须使用**控制台**对象而不是 Debug 对象。 若要向“Visual Studio 输出”窗口写入内容，请照常使用 Debug 对象。 确保知道应用程序正在写入的位置，否则可能在错误的位置中查找消息。 有关详细信息，请参见 [Console 类](/dotnet/api/system.console)、[Debug 类](/dotnet/api/system.diagnostics.debug)和[输出窗口](../ide/reference/output-window.md)。

## <a name="starting-the-application"></a>启动应用程序
 某些控制台应用程序在启动后将运行完成，然后退出。 此行为可能不会为您提供足够的时间来中断执行并调试。 若要能够调试应用程序，请使用下列过程之一来启动应用程序：

- 在代码中设置断点并启动应用程序。

- 启动应用程序使用**F10** (**调试** > **单步跳过**) 或**F11** (**调试**  > **单步执行**)，然后通过使用其他选项，例如代码导航**运行时单击**。

- 在代码编辑器中，右击某行并选择**运行到光标处**。

  调试控制台应用程序时，你可能希望从命令提示符处而不是从 Visual Studio 中启动该应用程序。 在这种情况下，可以从命令提示处启动应用程序并将 Visual Studio 调试器附加到该应用程序。 有关详细信息，请参阅[附加到正在运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。

  当从 Visual Studio 中启动控制台应用程序时，“控制台”窗口有时会出现在 Visual Studio 窗口的后面。 如果尝试从 Visual Studio 中启动控制台应用程序但似乎未产生任何结果，请尝试移动 Visual Studio 窗口。

## <a name="see-also"></a>请参阅
- [调试本机代码](../debugger/debugging-native-code.md)
- [调试托管代码](../debugger/debugging-managed-code.md)
- [Visual C++ 项目类型](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#, F#, and Visual Basic Project Types](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)（C#、F# 和 Visual Basic 项目类型）
- [C++ 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [调试器安全](../debugger/debugger-security.md)