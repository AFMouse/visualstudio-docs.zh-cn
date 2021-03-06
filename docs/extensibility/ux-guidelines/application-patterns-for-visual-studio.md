---
title: Visual Studio 的应用程序模式 |Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe97972d882fa8806de925bac6a072cd2dde4513
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/25/2019
ms.locfileid: "56796876"
---
# <a name="application-patterns-for-visual-studio"></a>Visual Studio 的应用程序模式
##  <a name="BKMK_WindowInteractions"></a> 窗口的交互

### <a name="overview"></a>概述
在 Visual Studio 中使用的两个主窗口类型是文档编辑器和工具窗口。 很少见，但可能的是大型的无模式对话框。 尽管这些是在外壳程序中所有无模式，但其模式是本质上不同。 本部分介绍了文档窗口中，工具窗口和无模式对话框之间的差异。 中介绍了模式对话框模式[对话框](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)。

### <a name="comparing-window-usage-patterns"></a>比较窗口使用模式
**文档窗口**几乎总是还显示在文档中。 这使文档编辑器"center 阶段"排列周围的补充工具窗口。

一个**工具窗口**最常显示为单独的较小窗口中折叠对 IDE 的边缘。 这可以是可见、 隐藏或自动隐藏。 但是，有时工具窗口中的显示文档井中，通过取消选中**停靠窗口/** 窗口上的属性。 这会导致更多实际空间，但也一种常见设计决策： 在尝试将集成到 Visual Studio 时，您必须决定是否应显示你的功能，工具窗口或文档窗口。

**无模式对话框**我们建议您不要在 Visual Studio 中。 最无模式对话框，根据定义，浮动工具窗口，并应通过这种方式实现。 在正常的工具窗口停靠到外壳的侧的大小将会过于受限的情况下允许无模式对话框。 它们还允许在用户将有可能，将对话框中移动到辅助显示器的情况下使用。

将仔细哪种容器类型有关所需。 UI 设计的常见使用情况模式需要考虑以下几点下表中。

||文档窗口|工具窗口|无模式对话框|
|-|---------------------|-----------------|---------------------|
| **位置** | 始终定位在文档中也并不会不停靠在 IDE 边缘。 它可以是"拉取"以使它浮动单独从主外壳。 | 通常在 IDE 边缘停靠选项卡上，但可以是自定义以浮点值、 自动隐藏 （取消固定），或也停靠在文档中。|独立于 IDE 的大型浮动窗口。 |
| **提交模型** | *延迟的提交*<br /><br /> 若要将数据保存在文档中，用户必须发出**文件&gt;保存**，**另存为**，或**保存所有**命令。 然后提交一次保存到它正在"更新"中的数据的概念，文档窗口具有命令。 当关闭文档窗口，所有内容都保存到磁盘，或可以丢失。 | *立即提交*<br /><br /> 没有任何保存模型。 为帮助编辑文件检查器工具窗口，该文件必须在活动编辑器或设计器中打开和编辑器或设计器拥有保存。 | *延迟或立即提交*<br /><br /> 大多数情况下，较大的无模式对话框需要操作，以提交更改，并允许一个"取消"操作，这将回滚任何对话框会话中所做的更改。  这用于区分开来的工具窗口从无模式对话框，工具窗口始终可以立即提交模型。 |
| **可见性** | *打开/创建 （文件） 并关闭*<br /><br /> 打开文档窗口是通过打开现有文档或使用模板来创建新文档。 没有任何"Open\<特定编辑器 >"命令。 | *隐藏和显示*<br /><br /> 单实例工具窗口可以显示或隐藏。 内容和工具窗口内的状态保留是否在视图中或隐藏。 多实例工具窗口可以为已关闭，以及隐藏。 多实例工具窗口关闭时，内容和工具窗口中的状态将被放弃。 | *从命令启动*<br /><br /> 从基于任务的命令启动对话框。 |
| **实例** | *多实例*<br /><br /> 当某些编辑器还允许在多个编辑器中打开同一文件时，可以在相同的时间和编辑不同的文件，打开多个编辑器 (使用**窗口&gt;新的窗口**命令)。<br /><br /> 在同一时间 （项目设计器），一个单一的编辑器可能正在编辑的一个或多个文件。 | *单-或多的实例*<br /><br /> 内容更改将反映上下文 （如在属性浏览器） 或将焦点/上下文推送到其他窗口 （解决方案资源管理器中的任务列表）。<br /><br /> 如果没有人信服的理由不到，单实例和多实例工具窗口应与在活动文档窗口相关联。 | *单实例* |
| **示例** | **文本编辑器**，如代码编辑器<br /><br /> **设计图面，**，如窗体设计器或建模图面<br /><br /> **控制布局类似于对话框**，如清单设计器 | **解决方案资源管理器**提供了一种解决方案和解决方案中包含的项目<br /><br /> **服务器资源管理器**提供用户选择在窗口中打开的服务器和数据连接的分层视图。 打开对象从数据库层次结构，如查询时，将打开一个文档窗口，并允许用户来编辑该查询。<br /><br /> **属性浏览器**显示在文档窗口或另一个工具窗口中的所选对象的属性。 属性已提供分层的网格视图中或在复杂的类似对话框的控件，并允许用户设置这些属性的值。 | |

##  <a name="BKMK_ToolWindows"></a> 工具窗口

### <a name="overview"></a>概述
工具窗口支持文档窗口中的用户的工作。 它们可以用于显示表示 Visual Studio 提供了和可操作的基本根对象的层次结构。

在考虑新的工具窗口在 IDE 中，作者应：

-   使用适合任务的现有工具窗口，并创建新的具有类似功能。 如果他们提供明显不同的"工具"或功能，不能将其集成到类似的窗口，或通过将现有窗口转变为透视的中心，应仅创建新的工具窗口。

-   使用标准命令栏中，如果需要请在工具窗口的顶部。

-   在使用其他工具窗口中已存在控件演示文稿和键盘导航模式保持一致。

-   在与其他工具窗口中的控件演示文稿保持一致。

-   特定于文档的工具窗口可见自动在可能的情况下，以使它们仅在激活的父文档时。

-   请确保其窗口内容可通过键盘 （支持箭头键） 导航。

#### <a name="tool-window-states"></a>工具窗口状态
Visual Studio 工具窗口具有不同的状态，其中一些为激活用户 （如自动隐藏功能）。 其他状态，自动可见，如允许工具窗口，以正确的上下文中显示和隐藏时不需要。 总共有五种工具窗口状态。

-   **停靠/固定**工具窗口可以附加到文档区域四边的任何。 工具窗口标题栏中显示的图钉图标。 工具窗口可以水平或垂直边缘的外壳和其他工具窗口，并且也可以链接选项卡。

-   **自动隐藏**工具窗口将取消固定。 不可见的离开 （使用工具窗口和它的图标的名称） 的选项卡上的文档区域边缘可以滑动窗口。 当用户悬停在选项卡时，工具窗口滑出。

-   **自动可见**等编辑器，另一个用户界面，将启动或获得焦点时自动显示工具窗口。

-   **浮点**工具窗口将鼠标悬停在 IDE 之外。 这可用于多监视器配置。

-   **选项卡式的文档**工具窗口可以停靠在文档中良好。 这是适用于大型工具窗口，如对象浏览器中，需要更多实际空间不是停靠在框架边缘到允许的。

![工具窗口状态在 Visual Studio 中的](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702年 01_ToolWindowStates")<br />Visual Studio 中的“工具”窗口状态

#### <a name="single-instance-and-multi-instance"></a>单实例和多实例
工具窗口是单实例还是多个实例。 某些单实例工具窗口可能与活动文档窗口中，相关联，而多实例工具窗口可能不会。 多实例工具窗口响应**窗口&gt;新的窗口**命令通过创建窗口的新实例。 下图演示了一个工具窗口，窗口的实例处于活动状态时使新窗口命令：

![工具窗口中，这样新建窗口命令窗口的实例时处于活动状态](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702年 02_ToolWindowEnablingCommand")<br />工具窗口中，这样新建窗口命令窗口的实例时处于活动状态

单实例工具窗口可以显示或隐藏，而多实例工具窗口可以为已关闭，以及隐藏。 所有工具窗口可以都停靠，选项卡链接、 浮动或作为多文档界面 (MDI) 子窗口 （类似于一个文档窗口） 设置。 所有工具窗口应都响应窗口菜单中的适当的窗口管理命令：

![在 Visual Studio 窗口菜单中的窗口管理命令](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702年 03_WindowManagementControls")<br />在 Visual Studio 窗口菜单中的窗口管理命令

#### <a name="document-specific-tool-windows"></a>特定于文档的工具窗口
某些工具窗口用于根据给定类型的文档发生变化。 这些窗口持续更新以反映功能适用于 IDE 中的活动文档窗口。

工具窗口的内容发生变化以反映所选的编辑器的示例包括工具箱和文档大纲。 当编辑器具有焦点，不提供到窗口的上下文时，这些窗口将显示一个水印。

#### <a name="navigable-list-tool-windows"></a>可导航列表工具窗口
某些工具窗口显示的用户可以与交互的可导航项的列表。 在此类型的窗口中，应始终有反馈当前项在列表中，即使在窗口处于非活动状态。 列表应响应**GoToNextLocation**并**GoToPrevLocation**通过还更改在窗口中的当前选定的项的命令

可导航列表工具窗口的示例是在解决方案资源管理器和查找结果窗口。

### <a name="tool-window-types"></a>工具窗口类型

#### <a name="common-tool-windows-and-their-functions"></a>常用的工具窗口和及其功能

**层次结构工具窗口**

| 工具窗口 | 函数 |
| --- | --- |
| “解决方案资源管理器” | 显示的文档列表的层次结构树包含在项目、 杂项文件和解决方案项。 在项目中项的显示由拥有项目类型 （例如，基于引用的、 基于目录的或混合类型） 的包定义。 |
| 类视图 | 类和文档，文件本身的独立的工作集中的各种元素的层次结构树。 |
| 服务器资源管理器 | 显示解决方案中的所有服务器和数据连接一个层次结构树。 |
| 文档大纲 | 活动文档的层次结构。 |

**网格工具窗口**

| 工具窗口 | 函数 |
| --- | --- |
| Properties | 一个网格，其中显示所选对象，以及值选取器来编辑这些属性的属性列表。 |
| 任务列表 | 一个网格，使用户可以创建、 编辑或删除任务和提出的意见。 |

**内容的工具窗口**

| 工具窗口 | 函数 |
| --- | --- |
| 帮助 | 一个窗口，允许用户获取的帮助，从"我如何"的各种方法的访问权限 MSDN 论坛的视频。 |
| 动态帮助 | 工具窗口，其中显示链接到帮助主题适用于当前所选内容。 |
| 对象浏览器 | 在左的窗格和对象的属性层次结构对象组件和右侧的列中的方法的列表两列框架集。 |

**对话框工具窗口**

| 工具窗口 | 函数 |
| --- | --- |
| 查找 | 允许用户查找或查找并在解决方案中的各种文件中替换的对话框。 |
| 高级的查找 | 允许用户查找或查找并在解决方案中的各种文件中替换的对话框。 |

**其他工具窗口**

::: moniker range="vs-2017"

| 工具窗口 | 函数 |
| --- | --- |
| 工具箱 | 用于存储将放置到设计图面，为所有设计器提供一致的拖动源上的元素的工具窗口。 |
| 起始页 | 在用户门户到 Visual Studio 中，有权访问的开发人员新闻、 Visual Studio 的帮助，以及最近使用的项目的源。 用户还可以通过将从 StartPage.xaml 文件复制创建自定义起始页"Common7\IDE\StartPages\"到 Visual Studio 中的 StartPages 文件夹的 Visual Studio program files 目录记录目录，然后再编辑 XAML通过手动或在 Visual Studio 或其他代码编辑器中打开它。 |

::: moniker-end

::: moniker range=">=vs-2019"

| 工具窗口 | 函数 |
| --- | --- |
| 工具箱 | 用于存储将放置到设计图面，为所有设计器提供一致的拖动源上的元素的工具窗口。 |

::: moniker-end

**调试器工具窗口**

| 工具窗口 | 函数 |
| --- | --- |
| 自动 ||
| 即时 ||
| 输出 | 可以使用输出窗口，您有文本事件或状态来声明。 |
| 内存 ||
| 断点 ||
| 正在运行 ||
| 文档 ||
| 调用堆栈 ||
| 局部变量 ||
| 监视文件 ||
| 反汇编 ||
| 寄存器 ||
| 线程 ||

##  <a name="BKMK_DocumentEditorConventions"></a> 文档编辑器约定

### <a name="document-interactions"></a>文档的交互
"文档井中"是在 IDE 中的最大空间，其中用户通常一直致力于他们的注意力才能完成其任务的补充工具窗口。 文档编辑器表示的用户打开和保存 Visual Studio 中工作的基本单位。 它们保留强烈的所选内容绑定到解决方案资源管理器或其他活动的层次结构窗口。 用户应该能够指向一个这些层次结构窗口和解决方案、 项目或 Visual Studio 包提供的另一个根对象到知道包含该文档以及它的关系。

文档编辑需要一致的用户体验。 若要允许用户可以专注于手头的任务而不是窗口管理和查找命令上，选择最适合用于编辑该文档类型的用户任务的文档视图策略。

#### <a name="common-interactions-for-the-document-well"></a>常见的文档井中的交互

-   维护一致的交互模型中常用**新的文件**并**打开的文件**体验。

-   当文档窗口打开时，请更新相关的窗口和菜单中的相关的功能。

-   菜单命令相应地集成到等常见菜单**编辑**，**格式**，并**视图**菜单。 如果大量的专用命令都不可用，则可以创建新菜单。 仅当该文档具有焦点时，应会显示此新菜单。

-   可能在编辑器的顶部放置嵌入式的工具栏。 这是优于具有显示在编辑器外的单独工具栏。

-   始终都是在解决方案资源管理器或类似活动中的选项层次结构窗口。

-   双击解决方案资源管理器中的文档应执行相同的操作**打开**。

-   如果可以在文档类型上使用多个编辑器，用户应能重写或重置给定的文档类型使用的默认操作**打开**对话框中，右键单击该文件并选择**打开使用**从快捷菜单。

-   不生成文档中的向导。

### <a name="user-expectations-for-specific-document-types"></a>对特定文档类型的用户期望
有几个不同的基本类型的文档编辑器，每个都有一组交互与相同类型的其他人相一致。

-   **基于文本的编辑器：** 代码编辑器、 日志文件

-   **设计图面：** WPF 窗体设计器中，Windows 窗体

-   **对话框样式编辑器：** 清单设计器中，项目属性

-   **模型设计器：** 工作流设计器、 codemap、 体系结构关系图、 进度

也有几种也使用该文档的非编辑器类型。 尽管它们不编辑文档本身，他们需要遵循的文档窗口的标准交互操作。

-   **报表：** IntelliTrace 报表、 HYPER-V 报表、 探查器报告

-   **仪表板：** 诊断中心

#### <a name="text-based-editors"></a>基于文本的编辑器

-   文档参与预览选项卡模式，即用于预览文档，而无需打开它。

-   配套工具窗口，如文档大纲中，可以表示文档的结构。

-   IntelliSense （如果适用） 将与其他代码编辑器行为一致。

-   弹出窗口或辅助用户界面执行类似的样式和图案现有类似的 UI，如 CodeLens。

-   在信息栏控件顶部的文档中或在状态栏中将提供有关文档状态的消息。

-   用户必须能够自定义字体和颜色使用的外观**工具 > 选项**页上，共享的字体和颜色页或一个特定于编辑器。

#### <a name="design-surfaces"></a>设计图面

-   空的设计器应具有水印，该值指示如何开始在图面上。

-   视图切换机制将遵循现有模式，例如双击打开代码编辑器中或允许与这两个窗格的交互的文档窗口中的选项卡。

-   应通过工具箱中，执行将元素添加到设计图面上，除非需要针对性极强的工具窗口。

-   在图面上的项将遵循一致的选择模型。

-   嵌入的工具栏包含特定于文档的命令仅、 不常见命令，如**保存**。

#### <a name="dialog-style-editors"></a>对话框样式编辑器

-   控件的布局应遵循正常对话框布局约定。

-   在编辑器中的选项卡不应与文档选项卡的外观，它们应匹配的两个允许内部选项卡样式之一。

-   用户必须能够与使用键盘; 仅控件进行交互可以通过使用标准的助记键激活编辑器和通过控件或按 tab 键。

-   在设计器应使用常见的保存模型。 尽管其他按钮可能比较合适，应表面上看，放置任何总体保存或提交按钮。

#### <a name="model-designers"></a>模型设计器

-   空的设计器应具有水印，该值指示如何开始在图面上。

-   应通过工具箱向设计图面添加元素。

-   在图面上的项将遵循一致的选择模型。

-   嵌入的工具栏包含特定于文档的命令仅、 不常见命令，如**保存**。

-   图例可以显示面上，指示或成为水印。

-   用户必须能够自定义使用的字体/颜色的外观**工具 > 选项**页上，共享的字体和颜色页或一个特定于编辑器。

#### <a name="reports"></a>报表

-   报表是通常只信息并不参与保存模型。 但是，它们可能包含指向其他相关信息或展开和折叠的部分如交互。

-   在图面上的大部分命令应为超链接，不是按钮。

-   布局应包含一个标头，并遵循标准报表布局准则。

#### <a name="dashboards"></a>仪表板

-   仪表板没有交互模型本身，但作为一种方法提供的各种其他工具。

-   它们不参与保存模型。

-   用户必须能够与使用键盘，通过激活编辑器并按 tab 键浏览控件或使用标准的助记键的控件进行交互。

##  <a name="BKMK_Dialogs"></a> 对话框

### <a name="introduction"></a>介绍
在 Visual Studio 中的对话框通常应支持一个离散的用户的工作单位，然后关闭。

如果已确定你需要一个对话框，您将有三个选项，按优先顺序：

1.  将您的功能集成到 Visual Studio 中的共享对话框之一。

2.  创建对话中使用现有的类似对话中找到的模式。

3.  创建一个新的对话框中，以下交互和布局准则。

本部分介绍如何选择在 Visual Studio 工作流中的正确对话框模式和对话框设计的常见约定。

### <a name="themes"></a>主题
在 Visual Studio 中的对话遵循以下两种基本样式之一：

#### <a name="standard-unthemed"></a>标准 (unthemed)
对话框大多数标准实用程序的对话框，并且应该 unthemed。 不要重新创建模板公共控件或尝试创建各种风格的"现代"按钮或控件。 控件和 chrome 外观，请按照[对话框的标准 Windows 桌面的交互指南](/windows/desktop/uxguide/win-dialog-box)。

#### <a name="themed"></a>主题
Specialty"签名"对话框可能主题化。 主题对话框具有独特的外观，还具有一些特殊的交互模式与样式关联。 主题对话框仅当满足这些要求：

-   对话框是一种常见的体验，将看到并使用通常或多个用户 (例如，**新的项目**对话框。

-   对话框中包含重要产品的品牌元素 (例如，**帐户设置**对话框)。

-   对话框中显示为一个更大的流，包括其他主题的对话的组成部分 (例如，**添加连接的服务**对话框)。

-   对话框是体验的作用战略中升级或个性化的产品版本的重要组成部分。

在创建主题对话框时，使用适当的环境颜色并遵循正确的布局和交互模式。 (请参阅[Visual Studio 的布局](../../extensibility/ux-guidelines/layout-for-visual-studio.md)。)

### <a name="dialog-design"></a>对话框设计
设计良好的对话框需要考虑下列元素：

-   支持用户任务

-   对话框文本样式、 语言和术语

-   控制选择和 UI 约定

-   视觉对象布局规范和控件的对齐方式

-   键盘访问

#### <a name="content-organization"></a>内容的组织
请考虑这些基本类型的对话框之间的差异：

-   [简单对话框](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs)提供单一模式窗口中的控件。 此演示文稿可能包括复杂的控件模式，包括字段选择器或图标栏的变体。

-   [分层对话框](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs)用于充分利用屏幕空间，当一个单一用户界面包含多组控件时。 对话框的分组是"分层"通过选项卡控件、 导航列表控件或按钮，以便用户可以选择分组的若要查看在任何给定时间点。

-   [向导](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards)可用于指导用户完成的步骤来完成任务的逻辑顺序。 顺序面板，有时会引入不同的工作流 （"分支"） 依赖于在上一个面板中所做的选择来提供一系列的选项。

####  <a name="BKMK_SimpleDialogs"></a> 简单对话框
一个简单的对话框是一个演示文稿的单一模式窗口中的控件。 此演示文稿可能包括复杂的控件模式，例如字段选取器的变体。 简单的对话框，请按照标准的常规布局，以及任何所需的复杂控件分组的特定布局。

![> 创建强名称密钥是一个简单对话框在 Visual Studio 中的一个示例。](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704年 01_CreateStrongNameKey")<br />创建强名称密钥是一个简单对话框在 Visual Studio 中的一个示例。

####  <a name="BKMK_LayeredDialogs"></a> 分层的对话框
分层的对话框包括选项卡、 仪表板和嵌入式的树。 它们用于最大化房地产时有多个组的一个单一用户界面中提供的控件。 分组的分层，以便用户可以选择分组的若要查看在任何时候。

在最简单的情况下，用于分组之间进行切换的机制是选项卡控件。 有多种替代方法。 请参阅优先级和如何选择最合适的样式的分层。

**工具&gt;选项**对话框是使用嵌入式的树的分层对话框的示例：

![工具 > 选项是一个分层对话框在 Visual Studio 中的一个示例。](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704年 02_ToolsOptions")<br />工具 > 选项是一个分层对话框在 Visual Studio 中的一个示例。

####  <a name="BKMK_Wizards"></a> 向导
向导可用于将用户一定逻辑顺序的步骤完成定向中完成任务。 顺序面板中提供了一系列选项，用户必须继续完成再继续到下的每个步骤。 足够的默认值是可用的一旦**完成**按钮处于启用状态。

 模式向导用于任务的：

-   包含分支，具体取决于用户选择在其中提供不同的路径

-   包含的步骤，其中后续步骤取决于来自前面步骤的用户输入之间的依赖项

-   足够复杂 UI 应该用于说明提供的选项以及每个步骤中可能的结果

-   是事务性的需要一系列步骤来完成整个提交任何更改之前

### <a name="common-conventions"></a>常见约定
要实现最佳的设计和对话框的功能，并遵照这些约定对话框大小、 位置、 标准、 控制配置和对齐方式、 UI 文本、 标题栏、 控制按钮和访问密钥。

有关特定于布局的指南，请参阅[Visual Studio 的布局](../../extensibility/ux-guidelines/layout-for-visual-studio.md)。

#### <a name="size"></a>大小
对话框应符合最小的 1024 x 768 屏幕分辨率，并且初始对话框大小不应超过 900 x 700 像素为单位。 对话框可能是可调整大小，但它不是一项要求。

有两个建议可调整大小对话框：

1.  最小大小是为将优化的控件的对话框定义剪辑，没有设置，并调整以适应合理本地化增长。

2.  用户扩展大小仍然存在从一个会话到另一个会话。 例如，如果用户可以扩展到 150%一个对话框，对话框中的后续启动将 150%处显示。

#### <a name="position"></a>位置
对话框必须出现在首次启动 IDE 内居中。 无法调整大小对话框的最后一个位置不需要保持不变，因此它们将显示在后续启动上居中。

可调整大小对话框大小应保留在后续启动。 可调整大小模式对话框的位置不需要保留。 它们在 IDE 中居中显示阻止对话框中的不可预测或不可用的位置中用户的显示配置发生更改时出现的可能性。

可重新定位的无模式对话框，用户的位置应在上维护后续启动，对话框可能会经常使用的大型工作流过程中不可或缺。

最顶层的对话框时对话框必须生成其他对话框，应级联而向右和向下从父以便明显它们已导航到新位置的用户。

#### <a name="modality"></a>模式
正在模式意味着用户所需完成或取消对话框，然后再继续。 模式对话框阻止用户与环境的其他部分进行交互，由于功能的任务流应尽可能保守地使用它们。 需要模式操作时，Visual Studio 提供许多您可以将各种功能集成到共享对话框。 如果必须创建一个新的对话框，请按照类似的功能与现有的对话的交互模式。

当用户需要进行一次执行两个活动时，如**查找**并**替换为**时编写新代码，该对话框应为无模式，以便用户可以轻松地切换它们之间。 Visual Studio 通常使用此种类型的编辑器支持链接的任务的工具窗口。

#### <a name="control-configuration"></a>控制配置
在使用完成相同的事情，在 Visual Studio 中的现有控件配置保持一致。

#### <a name="title-bars"></a>标题栏

- 标题栏中的文本必须反映启动它的命令的名称。

- 无图标应在对话框标题栏中使用。 在其中系统需要一个的情况下，使用 Visual Studio 徽标。

- 对话框不应具有最小化或最大化按钮。

- 标题栏中的帮助按钮已被弃用。 不要将它们添加到新的对话框。 当它们存在时，它们应启动是从概念上讲与任务相关的帮助主题。

  ![Visual Studio 对话框中的标题栏的准则规范](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704年 03_TitleBarSpecs")<br />Visual Studio 对话框中的标题栏的准则规范

#### <a name="control-buttons"></a>控件按钮
一般情况下，**确定**，**取消**，并**帮助**按钮应在该对话框右下角中水平排列。 如果对话框具有多个其他按钮将出现与控件按钮的视觉混淆的对话框底部，则允许备用垂直堆栈。

![Visual Studio 对话框中的控件按钮的可接受配置](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704年 04_ControlButtonConfig")<br />可接受的 Visual Studio 对话框中的控件按钮配置

对话框中必须包含一个默认控件按钮。 若要确定最佳的命令，以用作默认设置，请选择从以下选项 （按优先级顺序列出）：

-   选择作为默认值的最安全、 最安全的命令。 这意味着选择最能防止数据丢失以及避免意外的系统访问权限的命令。

-   如果数据丢失和安全性不因素，然后选择基于方便使用的默认命令。 包括默认值为最可能的命令将提高用户的工作流，如果对话框支持频繁地或重复的任务。

避免选择默认命令的永久破坏性操作。 如果存在此类命令，则更安全的命令为默认值改为选择。

#### <a name="access-keys"></a>访问键
不使用访问密钥**确定**，**取消**，或**帮助**按钮。 默认情况下，这些按钮映射到键盘快捷方式：

| 按钮名称 | 键盘快捷键 |
| --- | --- |
| 确定 | Enter |
| 取消 | Esc |
| 帮助 | F1 |

#### <a name="imagery"></a>图像
在对话框中尽量少使用的映像。 请勿使用大图标在对话框中只是用完空间。 使用映像，才会传达给用户，例如警告图标或状态动画消息的重要组成部分。

###  <a name="BKMK_PrioritizingAndLayering"></a> 确定优先级和分层

#### <a name="prioritizing-your-ui"></a>确定你的 UI 的优先级
可能有必要将某些用户界面元素引入到前端并将更高级的行为和到对话框选项 （包括晦涩命令）。 为 forefront 提供常用的功能，通过留出空间，并使其可见默认情况下，在 UI 中使用的文本标签时显示此对话框。

#### <a name="layering-your-ui"></a>分层 UI
如果你确定一个对话框，有必要，但你想要向用户显示的相关的功能远不止简单的对话框中可以显示的内容，然后需要你的 UI 层。 Visual Studio 使用的最常见的分层方法为选项卡和走廊或仪表板。 在某些情况下，可以展开和折叠的区域可能正合适。 在 Visual Studio 中通常不建议自适应 UI。

有一些优点和缺点分层通过类似于选项卡上的控件的 UI 的不同方法。 查看下面以确保您选择的一种分层方法，适合于您的具体情况的列表。

##### <a name="tabbing"></a>Tab 键次序

| 切换机制 | 优点和正确使用 | 缺点和不恰当地使用 |
| --- | --- | --- |
| Tab 控件 | 进行逻辑分组的对话框页，为相关集<br /><br />适用于五个 （或一个行中适应整个对话框的选项卡的数目） 对话框中的相关控件的页<br /><br />选项卡标签必须是短： 可以轻松地识别的内容的一个或两个词<br /><br />常见的系统对话框样式<br /><br />示例:**文件资源管理器&gt;项属性** | 很难进行简短的说明性标签<br /><br />通常不会扩展过去的五个选项卡在一个对话框<br /><br />如果有太多的选项卡，为当前行 （使用备用的分层方法） 不适当<br /><br />不可扩展 |
| 侧栏导航 | 可以容纳更多类别比选项卡的简单切换设备<br /><br />类别 （没有层次结构） 的简单列表<br /><br />可扩展<br /><br />示例:**自定义...&gt; 添加命令** | 使用的水平空间少于三个组是否不好<br /><br />任务可能是更好地适合于下拉列表 |
| 树控件 | 允许不受限制的类别<br /><br />允许进行分组和/或类别的层次结构<br /><br />可扩展<br /><br />示例:**工具&gt;选项** | 嵌入很深的层次结构可能会导致过多的水平滚动<br /><br />Visual Studio 提供了过度使用了树视图 |
| 向导 | 通过引导用户完成基于任务的顺序步骤有助于完成任务： 该向导表示高级任务和各个面板表示完成整个任务所需的子任务<br /><br />如果跨 Ui 边界，作为用户本应在何时具有要使用多个编辑器和工具窗口完成任务的任务非常有用<br /><br />此任务需要分支时很有用<br /><br />当任务包含步骤之间的依赖关系时非常有用<br /><br />可以在一个对话框，可以减少不同类似的对话框，展示一个决策分支与多个类似的任务时很有用 | 不适合于不需要的顺序工作流的任何任务<br /><br />用户会变得过载而混淆通过具有太多步骤的向导<br /><br />向导本质上是具有有限的屏幕空间 |

##### <a name="hallways-or-dashboards"></a>走廊或仪表板
走廊和仪表板是对话框或用作启动指向其他对话框和窗口的面板。 设计良好的"走廊"立即呈现仅最常见的选项、 命令和设置，使用户能够轻松地完成常见任务。 像实际的走廊提供了访问背后聊天室的走廊，此处不太常见 UI 收集到单独"聊天室"（通常是其他对话框） 的可访问从主走廊里的相关功能。

或者，一个 UI，而不是重构到不同的位置不太常见功能是只需一个仪表板提供了单个集合中所有可用的功能。

![用于公开其他 UI 在 Outlook 中的过道概念](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704年 08_Hallway")<br />用于公开其他 UI 在 Outlook 中的过道概念

##### <a name="adaptive-ui"></a>自适应 UI
显示或隐藏 UI 基于使用情况或自行报告，用户的体验是在隐藏其他部分的同时显示必要的 UI 的另一种方法。 建议不要在 Visual Studio 中，用于确定何时显示或隐藏 UI 的算法可能比较棘手，以及规则将始终是错误的情况下一些组。

##  <a name="BKMK_Projects"></a>项目

### <a name="projects-in-the-solution-explorer"></a>在解决方案资源管理器中的项目
大多数项目归类为基于引用的、 基于目录的还是混合。 在解决方案资源管理器中同时支持所有三种类型的项目。 使用项目中的用户体验的根在此窗口内发生。 尽管不同的项目节点引用、 目录或混合类型的项目，但没有一种常见的交互模式应遵循特定于项目的用户模式之前应用作为起始点。

项目应始终：

-   支持的功能，若要添加项目文件夹来组织项目内容

-   维护一致的模型项目持久性

项目还应该维护一致的交互模型：

-   删除项目项

-   保存文档

-   项目属性编辑

-   编辑另一种视图中的项目

-   拖放操作

### <a name="drag-and-drop-interaction-model"></a>拖放交互模型
项目通常分类本身作为基于引用的 （能够持久保存到存储中的项目项的唯一引用），基于目录的 （无法以物理方式持久保存项目项只能存储在项目的层次结构），或混合 （能够保留的引用或物理项）。 IDE 可容纳所有三种类型的项目中同时**解决方案资源管理器**。

从拖放的角度看，以下特征应该应用于每种类型的项目中**解决方案资源管理器**:

-   **基于引用的项目：** 关键在于项目正在拖动围绕对存储中的项的引用。 基于引用的项目可作为移动操作的源时，它应仅删除从项目到项目引用。 不应将硬盘驱动器中实际删除项。 时基于引用的项目可作为移动 （或复制） 操作的目标，它应添加对原始的源项的引用，而无需进行的项的私有副本。

-   **基于目录的项目：** 拖放的角度来看，从该项目拖动围绕物理项而不是一个引用。 当基于目录的项目可作为移动操作的源时，它应结束从硬盘中删除物理项，以及从该项目将其删除。 基于目录的项目可作为移动 （或复制） 操作的目标，它应在其目标位置中发出源项的副本。

-   **多重目标项目：** 从拖放的角度来看，此类型的项目的行为为基础的性质 （对存储中的项的引用），或者项本身正在拖动的项。 上面介绍了引用和物理的项的正确行为。

如果只有一种类型的项目中**解决方案资源管理器**，拖放操作将是非常简单。 由于每个项目系统具有定义它自己的拖放行为的功能，应遵循特定的准则 （基于 Windows 资源管理器拖放行为），以确保可预测的用户体验：

-   未修改拖动操作**解决方案资源管理器**（当 Ctrl 和 Shift 键都不按住） 应导致移动操作。

-   按住 shift 并拖动操作还应导致移动操作。

-   按住 ctrl 键拖动操作应导致复制操作。

-   基于引用的和混合项目系统支持的源项添加链接 （或引用） 的概念。 当这些项目都拖放操作的目标 (当**Ctrl + Shift** ，是否按下)，它应导致对添加到项目中的项的引用

并非所有拖放操作都都是合理的基于引用的、 基于目录的和混合项目组合。 具体而言，它会产生问题，假设以允许基于目录的源项目和基于引用的目标项目之间移动操作，因为源基于目录的项目必须删除在移动完成后的源项。 目标基于引用的项目将最终会对已删除的项的引用。

它也是令人误解，假设以允许这些类型的项目之间的复制操作，因为目标基于引用的项目不应将源项的独立副本。 同样，Ctrl + Shift 拖动到基于目录的目标项目，从而不应允许因为基于目录的项目不能保留的引用。 在不支持拖放操作的情况下，IDE 应禁止下拉菜单，并向用户显示不可拖动光标 （下指针表中所示）。

若要正确实现拖放行为，拖动源项目需要进行通信本质上的对目标项目。 （例如，是否基于引用或目录的？）此信息由源提供的剪贴板格式表示。 拖动 （或剪贴板复制操作） 的源作为项目应提供任一`CF_VSREFPROJECTITEMS`或`CF_VSSTGPROJECTITEMS`分别，具体取决于项目是基于引用的或基于目录的。 这些格式都具有相同的数据内容，这类似于 Windows`CF_HDROP`设置的格式，但列表的字符串，而不是文件名，是双-`NULL`终止列表`Projref`字符串 (从返回`IVsSolution::GetProjrefOfItem`或`::GetProjrefOfProject`根据需要)。

作为拖放 （或剪贴板粘贴操作） 的目标，项目应接受这两项`CF_VSREFPROJECTITEMS`和`CF_VSSTGPROJECTITEMS`，但根据目标项目和源代码项目的性质而异的拖放操作完全处理。 源项目是否提供了通过声明它的性质`CF_VSREFPROJECTITEMS`或`CF_VSSTGPROJECTITEMS`。 拖放目标了解它自己的性质，因此有足够的信息来决定为是否移动、 复制，或应执行链接。 用户还会修改的拖放操作应执行通过按 Ctrl、 Shift 或同时 Ctrl 和 Shift 键。 务必拖放目标以正确地表明将提前在执行哪些操作及其`DragEnter`和`DragOver`方法。 **解决方案资源管理器**会自动知道源项目和目标项目是否为同一个项目。

特别是不支持将项目项跨 Visual Studio 的实例 （例如，从 devenv.exe 到另一个实例）。 **解决方案资源管理器**直接禁用这。

用户应始终能够确定通过选择某一项，将其拖到目标位置，并观察以下鼠标指针的显示之前删除项的拖放操作的效果：

| 鼠标指针 | 命令 | 描述 |
| :---: | --- | --- |
| ![鼠标"不放下"图标](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706年 01_MouseNoDrop") | 不删除 | 项不能删除到指定位置。 |
| ![鼠标"复制"图标](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706年 02_MouseCopy") | 复制 | 将项复制到目标位置。 |
| ![鼠标"移动"图标](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706年 03_MouseMove") | 移动 | 项将移动到目标位置。 |
| ![鼠标"添加引用"图标](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706年 04_MouseAddRef") | 添加引用 | 对所选的项的引用将添加到目标位置。 |

#### <a name="reference-based-projects"></a>基于引用的项目
 下表总结了拖放 （以及剪切/复制/粘贴） 执行的操作应根据源项和修饰符键按下的基于引用的目标项目的性质：

| 修饰符 | 类别 | 源项：引用/链接 | 源项：物理该项或文件系统 (`CF_HDROP`) |
| --- | --- | --- | --- |
| 没有修饰符 | 操作 | 移动 | 链接 |
| 没有修饰符 | 目标 | 将引用添加到原始项 | 将引用添加到原始项 |
| 没有修饰符 | 源 | 对原始项删除引用 | 将保留原始项目 |
| 没有修饰符 | 结果 | `DROPEFFECT_MOVE` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 | `DROPEFFECT_LINK` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 |
| Shift+Drag | 操作 | 移动 | 不删除 |
| Shift+Drag | 目标 | 将引用添加到原始项 | 不删除 |
| Shift+Drag | 源 | 对原始项删除引用 | 不删除 |
| Shift+Drag | 结果 | `DROPEFFECT_MOVE` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 | 不删除 |
| Ctrl+Drag | 操作 | 复制 | 不删除 |
| Ctrl+Drag | 目标 | 将引用添加到原始项 | 不删除 |
| Ctrl+Drag | 源 | 将保留原始项目引用 | 不删除 |
| Ctrl+Drag | 结果 | `DROPEFFECT_COPY` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 | 不删除 |
| Ctrl+Shift+Drag | 操作 | 链接 | 链接 |
| Ctrl+Shift+Drag | 目标 | 将引用添加到原始项 | 将引用添加到原始项 |
| Ctrl+Shift+Drag | 源 | 将保留原始项目引用 | 将保留原始项目 |
| Ctrl+Shift+Drag | 结果 | `DROPEFFECT_LINK` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 | `DROPEFFECT_LINK` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 |
| Ctrl+Shift+Drag | 说明 | 与 Windows 资源管理器中的快捷方式拖放行为相同。 ||
| 剪切/粘贴 | 操作 | 移动 | 链接 |
| 剪切/粘贴 | 目标 | 将引用添加到原始项 | 将引用添加到原始项 |
| 剪切/粘贴 | 源 | 将保留原始项目引用|将保留原始项目 |
| 剪切/粘贴 | 结果 | 项目仍保留在存储中的原始位置 | 项目仍保留在存储中的原始位置 |
| 复制/粘贴 | 操作 | 复制 | 链接 |
| 复制/粘贴 | 源 | 将引用添加到原始项 | 将引用添加到原始项 |
| 复制/粘贴 | 结果 | 将保留原始项目引用 | 将保留原始项目 |
| 复制/粘贴 | 操作 | 项目仍保留在存储中的原始位置 | 项目仍保留在存储中的原始位置 |

#### <a name="directory-based-projects"></a>基于目录的项目
下表总结了拖放 （以及剪切/复制/粘贴） 执行的操作应根据源项和修饰符键按下的基于目录的目标项目的性质：


| 修饰符 | 类别 | 源项：引用/链接 | 源项：物理该项或文件系统 (`CF_HDROP`) |
|-----------------|----------| - | - |
| 没有修饰符 | 操作 | 移动 | 移动 |
| 没有修饰符 | 目标 | 复制到目标位置的项 | 复制到目标位置的项 |
| 没有修饰符 | 源 | 对原始项删除引用 | 对原始项删除引用 |
| Shift+Drag | 操作 | 移动 | 移动 |
| Shift+Drag | 目标 | 复制到目标位置的项 | 复制到目标位置的项 |
| Shift+Drag | 源 | 对原始项删除引用 | 从原始位置中删除项 |
| Shift+Drag | 结果 | `DROPEFFECT_MOVE` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 | `DROPEFFECT_MOVE` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 |
| Ctrl+Drag | 操作 | 复制 | 复制 |
| Ctrl+Drag | 目标 | 复制到目标位置的项 | 复制到目标位置的项 |
| Ctrl+Drag | 源 | 将保留原始项目引用 | 将保留原始项目引用 |
| Ctrl+Drag | 结果 | `DROPEFFECT_COPY` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 | `DROPEFFECT_COPY` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 |
| Ctrl+Shift+Drag | | 不删除 | 不删除 |
| 剪切/粘贴 | 操作 | 移动 | 移动 |
| 剪切/粘贴 | 目标 | 复制到目标位置的项 | 复制到目标位置的项 |
| 剪切/粘贴 | 源 | 对原始项删除引用 | 从原始位置中删除项 |
| 剪切/粘贴 | 结果 | 项目仍保留在存储中的原始位置 | 从存储中的原始位置删除项 |
| 复制/粘贴 | 操作 | 复制 | 复制 |
| 复制/粘贴 | 目标 | 将引用添加到原始项 | 复制到目标位置的项 |
| 复制/粘贴 | 源 | 将保留原始项目 | 将保留原始项目 |
| 复制/粘贴 | 结果 | 项目仍保留在存储中的原始位置 | 项将保留在原始位置的项存储 |

#### <a name="mixed-target-projects"></a>多重目标项目
下表总结了拖放 （以及剪切/复制/粘贴） 执行的操作应根据源项和修饰符键按下的多重目标项目的性质：

| 修饰符 | 类别 | 源项：引用/链接 | 源项：物理该项或文件系统 (`CF_HDROP`) |
| --- | --- | --- | --- |
| 没有修饰符 | 操作 | 移动 | 移动 |
| 没有修饰符 | 目标 | 将引用添加到原始项 | 复制到目标位置的项 |
| 没有修饰符 | 源 | 对原始项删除引用 | 对原始项删除引用 |
| 没有修饰符 | 结果 | `DROPEFFECT_ MOVE` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 | `DROPEFFECT_ MOVE` 作为从操作返回`::Drop`和从存储中的原始位置删除项 |
| Shift+Drag | 操作 | 移动 | 移动 |
| Shift+Drag | 目标 | 将引用添加到原始项 | 复制到目标位置的项 |
| Shift+Drag | 源 | 对原始项删除引用 | 从原始位置中删除项 |
| Shift+Drag | 结果 | `DROPEFFECT_ MOVE` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 | `DROPEFFECT_ MOVE` 作为从操作返回`::Drop`和从存储中的原始位置删除项 |
| Ctrl+Drag | 操作 | 复制 | 复制 |
| Ctrl+Drag | 目标 | 将引用添加到原始项 | 复制到目标位置的项 |
| Ctrl+Drag | 源 | 将保留原始项目引用 | 将保留原始项目 |
| Ctrl+Drag | 结果 | `DROPEFFECT_ COPY` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 | `DROPEFFECT_ COPY` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 |
| Ctrl+Shift+Drag | 操作 | 链接 | 链接 |
| Ctrl+Shift+Drag | 目标 | 将引用添加到原始项 | 将引用添加到原始源项 |
| Ctrl+Shift+Drag | 源 | 将保留原始项目引用 | 将保留原始项目 |
| Ctrl+Shift+Drag | 结果 | `DROPEFFECT_ LINK` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 | `DROPEFFECT_ LINK` 作为从操作返回`::Drop`和项目仍保留在存储中的原始位置 |
| 剪切/粘贴 | 操作 | 移动 | 移动 |
| 剪切/粘贴 | 目标 | 复制到目标位置的项 | 复制到目标位置的项 |
| 剪切/粘贴 | 源 | 对原始项删除引用 | 从原始位置中删除项 |
| 剪切/粘贴 | 结果 | 项目仍保留在存储中的原始位置 | 从存储中的原始位置删除项 |
| 复制/粘贴 | 操作 | 复制 | 复制 |
| 复制/粘贴 | 目标 | 将引用添加到原始项 | 复制到目标位置的项 |
| 复制/粘贴 | 源 | 将保留原始项目 | 将保留原始项目 |
| 复制/粘贴 | 结果 | 项目仍保留在存储中的原始位置 | 项目仍保留在存储中的原始位置 |

这些详细信息应纳入考虑范围，在实现中拖动时**解决方案资源管理器**:

-   多个选择方案的设计。

-   在目标项目的文件的名称 （完整路径） 必须是唯一或不应允许拖放。

-   文件夹名称必须唯一 （不区分大小写） 在正在删除它们的级别。

-   有在拖动 （不在上述方案中所述） 时已打开的或已关闭的文件之间的行为差异。

-   顶级文件的行为略有不同文件夹中的文件。

另一个问题需要注意的是如何处理具有打开的设计器或编辑器项上的移动操作。 预期的行为是，如下所示 （这适用于所有项目类型）：

1.  如果打开编辑器/设计器不具有任何未保存的更改，然后在编辑器/设计器窗口应以无提示方式关闭。

2.  如果打开编辑器/设计器也有未保存的更改，然后拖动源应等待发生，然后询问用户将具有类似于下面的提示的窗口在关闭之前已打开的文档中保存未提交的更改的下拉:

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

这使用户能够在目标进行其副本之前保存正在进行的工作。 新方法`IVsHierarchyDropDataSource2::OnBeforeDropNotify`添加了以启用这种空格处理。

目标然后将复制项的状态，因为它是在存储中 (不包括在编辑器中未保存的更改，如果用户选择**否**)。 目标已完成其复制后 (在`IVsHierarchyDropDataSource::Drop`)，源有机会在完成移动操作的删除部分 (在`IVsHierarchyDropDataSource::OnDropNotify`)。

未保存的更改与任何编辑器应保持打开状态。 对于这些文档具有未保存的更改，这意味着将执行移动操作的复制部分，但将中止删除部分。 当用户选择多个选择方案中**否**，这些文档具有未保存的更改不应关闭或删除，但未保存的更改不应关闭并删除。