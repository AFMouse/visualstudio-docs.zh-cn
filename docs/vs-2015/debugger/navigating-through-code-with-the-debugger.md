---
title: 使用调试器浏览代码 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a38d078356acf4e78aeeb97687126616d027351f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "58933220"
---
# <a name="navigating-through-code-with-the-debugger"></a>使用调试器浏览代码
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

帮助熟悉命令和快捷方式在调试器中的代码中导航，这样做更快、 更轻松地查找和解决您的应用程序中的问题。 导航代码在调试器中的，您可以[检查您的应用程序的状态](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables)或了解有关其执行流的详细信息。  
  
## <a name="start-debugging"></a>“启动调试”  
 通常情况下，启动调试会话使用**F5** (**调试** / **开始调试**)。 此命令启动附有调试器的应用。  
  
 绿色箭头还会启动调试器 (与相同**F5**)。  
  
 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 您可使用附加调试器启动该应用的一些其他方法包括**F11** ([单步执行代码](#BKMK_Step_into__over__or_out_of_the_code))， **F10** ([逐过程执行代码](#BKMK_Step_over_Step_out))，或通过使用**运行到光标处**。  这些选项所执行的操作，请参阅有关此主题中的其他部分。  
  
 调试时，黄线将显示下一步将执行的代码。  
  
 ![DBG&#95;Basics&#95;Break&#95;Mode](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 调试时，您可以类似的命令之间进行切换**F5**， **F11**和使用其他功能来快速转到想要查看的代码 （例如断点） 本主题中所述。  
  
 仅当调试器暂停时，大多数调试器功能，如局部变量窗口中查看变量值或在监视窗口中计算表达式是可用 (也称为*中断模式下*)。 调试器暂停时，应用程序状态已挂起函数，变量时，对象保留在内存中。 在中断模式下，可以检查元素的位置和状态，以查看存在冲突或 bug。 对于某些项目类型，您还可以在中断模式下应用所做的调整。  
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a> 单步执行代码，  
 若要停止调试时代码 （每个语句） 的每一行上，使用**F11**键盘快捷方式 (或**调试** / **单步执行**菜单上)。  
  
> [!TIP]
>  执行每行代码，你可以悬停在变量，以查看它们的值，或者可以使用[局部变量](../debugger/autos-and-locals-windows.md)并[监视](../debugger/autos-and-locals-windows.md)windows 以监视更改其值。  
  
 下面是一些有关的行为的详细信息**单步执行**:  
  
- 在嵌套函数调用上， **“逐语句”** 将进入并单步执行嵌套最深的函数。 如果对类似 **的调用使用** “逐语句” `Func1(Func2())`，调试器将进入并单步执行函数 `Func2`。  
  
- 实际上，调试器逐句通过代码语句，而不是物理行。 例如， `if` 子句可以写在一行内：  
  
  ```csharp  
  int x = 42;  
  string s = "Not answered";  
  if( int x == 42) s = "Answered!";  
  ```  
  
  ```vb  
  Dim x As Integer = 42  
  Dim s As String = "Not answered"  
  If x = 42 Then s = "Answered!"  
  ```  
  
   当你单步执行此行时，调试器将该条件视为一步，将结果视为另一步（在此示例中，条件为 true）。  
  
  若要直观地跟踪调用堆栈，单步执行函数时，请参阅[调试时映射调用堆栈上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。  
  
##  <a name="BKMK_Step_over_Step_out"></a> 单步执行代码，正在跳过函数  
 当在调试器中运行代码，通常您会意识到不需要查看特定函数中会发生什么情况 (不关心或知道其工作方式，类似于经过全面测试的库代码)。 使用以下命令以跳过代码 （函数仍可以执行，当然，但调试器跳过它们）。  
  
|键盘命令|菜单命令|描述|  
|----------------------|------------------|-----------------|  
|**F10**|**逐过程**|如果当前行包含函数调用中，**单步跳过**运行的代码则被调用的函数返回后，在第一行代码处挂起执行。|  
|**Shift+F11**|**跳出**|**单步跳出**会继续运行代码，当前函数返回 （通过当前函数调试器跳） 时挂起执行。|  
  
> [!TIP]
>  如果你需要在应用中查找的入口点，请先使用**F10**或**F11**。 检查应用程序状态或尝试找出有关其执行流的详细信息时，这些命令很有帮助。  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> 运行到特定位置或函数  
 调试代码的首选的方法，这些方法时通常很有用知道具体的代码你想要检查，或至少知道你想要开始调试。  
  
-   **在代码中设置断点**  
  
     若要在代码中设置简单断点，请打开 Visual Studio 编辑器中的源文件。 你想要暂停执行、，然后右键单击代码窗口以查看上下文菜单选择中的代码行上设置光标**断点 / 插入断点**(或按**F9**)。 调试器挂起执行权限才能执行行。  
  
     ![设置断点](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Visual Studio 中的断点提供了一组丰富的附加功能，例如条件断点和跟踪点。 请参阅[使用断点](../debugger/using-breakpoints.md)。  
  
-   **运行到光标处**  
  
     若要运行到光标位置，请将光标放在源窗口中可执行的代码行上。 在编辑器的上下文菜单 （在编辑器中右键单击），选择**运行到光标处**。 这就像设置临时断点。  
  
-   **手动中断代码**  
  
     若要中断执行应用程序中代码的下一个可用行，选择**调试**，**全部中断**(键盘：**Ctrl + Alt + Break**)。  
  
     如果中断正在执行的代码，而没有响应的源或符号 (.pdb) 文件，调试器将显示“未找到源文件”  或“未找到符号”  页面，帮助你找到相应的文件。 请参阅[指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。 如果你无法访问支持文件，仍可以在“反汇编”窗口中调试汇编指令。  
  
-   **在调用堆栈上运行到函数**  
  
     在中**调用堆栈**窗口 （调试时可用），选择函数，右键单击并选择**运行到光标处**。 若要直观地跟踪调用堆栈，请参阅[调试时映射调用堆栈上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。  
  
-   **运行到通过名称指定的函数**  
  
     可以让调试器在运行你的应用程序，直至到达指定的函数。 你可以通过名称指定函数，也可以从调用堆栈中选择函数。  
  
     若要通过名称指定函数，请选择 **“调试”**、 **“新建断点”**、 **“在函数处中断”**，然后输入函数名称和其他标识信息。  
  
     ![新建断点对话框](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     如果是重载函数，或者函数在多个命名空间，你可以在 **“选择断点”** 对话框中选择想要的函数。  
  
     ![选择断点对话框](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> 移动指针以更改执行流  
 调试器暂停时，您可以移动指令指针来设置要执行的代码的下一个语句。 源窗口或“反汇编”窗口的空白区域中的黄色箭头标记要执行的下一条语句的位置。 通过移动此箭头，可以跳过部分代码或返回到以前执行过的行。 在某些情况下可以使用此方法，例如，跳过包含已知 bug 的代码段。  
  
 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 要设置下一条要执行的语句，请使用以下过程之一：  
  
-   在源窗口中，将黄色箭头拖动希望执行下一语句的位置，该位置应在同一源文件。  
  
-   在源窗口中，将光标放置在你想要执行的下，右键单击并选择的行**设置下一语句**。  
  
-   在反汇编窗口中，将光标放置在你想要执行的下，右键单击程序集指令上并选择**设置下一语句**。  
  
> [!CAUTION]
>  设置下一条语句将导致程序计数器直接跳到新位置。 使用此命令时要小心：  
> 
> - 不执行旧执行点和新执行点之间的指令。  
>   -   如果向后移动执行点，则不撤消插入的指令。  
>   -   将下一条语句移动到另一个函数或范围通常会导致调用堆栈损坏，导致一个运行时错误或异常。 如果尝试将下一条语句移动到另一个范围，则调试器将打开一个含有警告的对话框，并提供一个取消该操作的机会。 在 Visual Basic 中，不能将下一条语句移动到另一个范围或函数。  
>   -   在本机 C++ 中，如果已启用运行时检查，设置下一条语句会导致执行到达方法的结尾时引发异常。  
>   -   当启用“编辑并继续”时，如果你进行了“编辑并继续”无法立即重新映射的编辑，那么 **“设置下一语句”** 将失败。 例如，如果你编辑了 catch 块中的代码，将发生这种情况。 发生这种情况时，你将看到一条错误消息，告诉你该操作不受支持。  
> 
> [!NOTE]
>  在托管代码中，在以下情况下不能移动下一条语句：  
> 
> - 下一条语句与当前语句不在同一个方法中。  
>   -   使用实时调试启动调试。  
>   -   正在展开一个调用堆栈。  
>   -   已引发一个 System.StackOverflowException 或 System.Threading.ThreadAbortException 异常。  
  
 应用程序处于活动运行状态时不能设置下一条语句。 要设置下一语句，调试器必须处于中断模式。  
  
## <a name="step-into-non-user-code"></a>单步执行非用户代码  
 默认情况下，调试器尝试显示只有你应用的代码在调试时，该域由调试器设置调用*仅我的代码*。 (请参阅[仅我的代码](../debugger/just-my-code.md)若要查看这对不同项目类型和语言的工作方式以及可以如何自定义行为。)但是，有时调试时，你可能想要查看框架代码、 第三方库代码中或调用到操作系统 （系统调用）。  
  
 您可以关闭仅我的代码通过转到**工具** / **选项** / **调试**并清除**启用 '仅我的代码'** 复选框。  
  
 当禁用仅我的代码时，调试器可以单步执行非用户代码，在调试器窗口中显示非用户代码。  
  
> [!NOTE]
>  设备项目不支持“仅我的代码”。  
  
 **单步执行系统调用**  
  
 如果你已加载系统代码的调试符号，并且未启用仅我的代码，您可以单步执行系统调用中，正如其他任何调用。  
  
 若要访问 Microsoft 符号文件，请参阅[使用符号服务器查找不在本地计算机上的符号文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine)中[指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)主题。  
  
 在调试时加载特定系统组件的符号：  
  
1.  打开模块窗口 (键盘：**Ctrl + Alt + U**)。  
  
2.  选择要加载符号的模块。  
  
     查看 **“符号状态”** 列可以了解哪些模块加载了符号。  
  
3.  在上下文菜单中选择 **“加载符号”** 。  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> 单步执行托管代码中的属性和运算符  
 默认情况下，调试器将逐过程执行托管代码中的属性和运算符。 在多数情况下，这会提供较好的调试体验。 若要启用单步执行属性或运算符，请选择**调试** / **选项**。 在 **“调试”** / **“常规”** 页面上，清除 **“逐过程执行属性和运算符(仅限托管)”** 复选框
