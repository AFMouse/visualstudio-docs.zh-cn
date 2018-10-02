---
title: 将数据保存在事务中 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4b6d6befe4bbe29147a59b9700b8f148154e6c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47477516"
---
# <a name="save-data-in-a-transaction"></a>将数据保存在事务中
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[将数据保存在事务中](https://docs.microsoft.com/visualstudio/data-tools/save-data-in-a-transaction)。  
  
  
本演练演示如何将数据保存在事务中，通过使用<xref:System.Transactions>命名空间。 此示例使用源自 Northwind 示例数据库的 `Customers` 和 `Orders` 表。  
  
## <a name="prerequisites"></a>系统必备  
 本演练需要对 Northwind 示例数据库的访问权限。 有关设置 Northwind 示例数据库的信息，请参阅[如何： 安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
## <a name="create-a-windows-application"></a>创建 Windows 应用程序  
 第一步是创建**Windows 应用程序**。  
  
#### <a name="to-create-the-new-windows-project"></a>创建新的 Windows 项目  
  
1.  在 Visual Studio 中，在**文件**菜单中，创建一个新**项目**。  
  
2.  将项目命名**SavingDataInATransactionWalkthrough**。  
  
3.  选择**Windows 应用程序**，然后选择**确定**。 有关详细信息，请参阅[客户端应用程序](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)。  
  
     **SavingDataInATransactionWalkthrough**创建项目并将其添加到**解决方案资源管理器**。  
  
## <a name="create-a-database-data-source"></a>创建数据库数据源  
 此步骤中使用[数据源配置向导](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)创建基于数据源`Customers`和`Orders`Northwind 示例数据库中的表。  
  
#### <a name="to-create-the-data-source"></a>创建数据源  
  
1.  上**数据**菜单中，选择**显示数据源**。  
  
2.  在中**数据源**窗口中，选择**添加新数据源**以启动**数据源配置向导**。  
  
3.  上**选择数据源类型**屏幕上，选择**数据库**，然后选择**下一步**。  
  
4.  上**选择您的数据连接**屏幕执行下列任一操作：  
  
    -   如果下拉列表中包含到 Northwind 示例数据库的数据连接，请选择该连接。  
  
         或  
  
    -   选择**新的连接**以启动**添加/修改连接**对话框并创建到 Northwind 数据库的连接。  
  
5.  如果你的数据库需要密码，选择选项以包括敏感数据，然后选择**下一步**。  
  
6.  上**将连接字符串保存到应用程序配置文件**屏幕上，选择**下一步**。  
  
7.  上**选择数据库对象**屏幕上，展开**表**节点。  
  
8.  选择`Customers`并`Orders`表，并选择**完成**。  
  
     **NorthwindDataSet**添加到项目并`Customers`并`Orders`表中出现**数据源**窗口。  
  
## <a name="addcontrols-to-the-form"></a>向窗体 Addcontrols  
 可以通过将项从创建数据绑定控件**数据源**窗口拖到窗体上的。  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>若要创建数据绑定 Windows 窗体控件  
  
-   在中**数据源**窗口中，展开**客户**节点。  
  
-   将主**客户**从节点**数据源**窗口拖到**Form1**。  
  
     用于导航记录的 <xref:System.Windows.Forms.DataGridView> 控件和工具栏（<xref:System.Windows.Forms.BindingNavigator>）将显示在窗体上。 一个[NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)， [CustomersTableAdapter](../data-tools/tableadapter-overview.md)，<xref:System.Windows.Forms.BindingSource>，并<xref:System.Windows.Forms.BindingNavigator>组件栏中出现。  
  
-   将相关**订单**节点 (非主**订单**节点，但下面的相关的子表节点**传真**列) 到下面的表单上**CustomersDataGridView**。  
  
     窗体上显示一个 <xref:System.Windows.Forms.DataGridView>。 [OrdersTableAdapter](../data-tools/tableadapter-overview.md)和<xref:System.Windows.Forms.BindingSource>组件栏中出现。  
  
## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>添加对 System.Transactions 程序集的引用  
 事务使用 <xref:System.Transactions> 命名空间。 默认情况下，没有添加对 system.transactions 程序集的项目引用，因此你需要手动将其添加。  
  
#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>添加对 System.Transactions DLL 文件的引用  
  
1.  上**项目**菜单中，选择**添加引用**。  
  
2.  选择**System.Transactions**(在 **.NET**选项卡)，然后选择**确定**。  
  
     对引用**System.Transactions**添加到项目。  
  
## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>记得修改 BindingNavigator 的 SaveItem 按钮中的代码  
 对于拖放到窗体上的第一个表，代码添加到默认情况下`click`事件的保存按钮<xref:System.Windows.Forms.BindingNavigator>。 你需要手动添加代码以更新所有附加的表。 对于本演练，我们重构的现有保存代码源自保存按钮的单击事件处理程序。我们还创建更多的方法来提供基于行是否需要添加或删除特定的更新功能。  
  
#### <a name="to-modify-the-auto-generated-save-code"></a>修改自动生成的保存代码  
  
1.  选择**保存**按钮**CustomersBindingNavigator** （带有软盘图标的按钮）。  
  
2.  将 `CustomersBindingNavigatorSaveItem_Click` 方法替换为以下代码：  
  
     [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
     [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]  
  
 对相关数据的协调更改的顺序如下：  
  
-   删除子记录。 (在这种情况下，删除记录`Orders`表。)  
  
-   删除父记录。 (在这种情况下，删除记录`Customers`表。)  
  
-   插入父记录。(在这种情况下中, 插入记录`Customers`表。)  
  
-   插入子记录。 (在这种情况下中, 插入记录`Orders`表。)  
  
#### <a name="to-delete-existing-orders"></a>删除现有顺序  
  
-   添加以下`DeleteOrders`方法**Form1**:  
  
     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]  
  
#### <a name="to-delete-existing-customers"></a>删除现有客户  
  
-   添加以下`DeleteCustomers`方法**Form1**:  
  
     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]  
  
#### <a name="to-add-new-customers"></a>添加新客户  
  
-   添加以下`AddNewCustomers`方法**Form1**:  
  
     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]  
  
#### <a name="to-add-new-orders"></a>添加新顺序  
  
-   添加以下`AddNewOrders`方法**Form1**:  
  
     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]  
  
## <a name="run-the-application"></a>运行此应用程序  
  
#### <a name="to-run-the-application"></a>要运行应用程序  
  
-   选择**F5**运行该应用程序。  
  
## <a name="see-also"></a>请参阅  
 [将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)
