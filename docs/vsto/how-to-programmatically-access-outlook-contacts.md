---
title: 如何：以编程方式访问 Outlook 联系人
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c46df4218a12c0f9a155567aeee0c007d0a19c53
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598201"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>如何：以编程方式访问 Outlook 联系人
  本示例查找其姓氏包含指定的搜索字符串的所有联系人。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>示例
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]

## <a name="compile-the-code"></a>编译代码
 此示例需要：

-   联系人姓氏和名字包含字符串"**Na"** (例如，Tzipi Butnaru) 在**联系人**文件夹。

## <a name="see-also"></a>请参阅
- [使用联系人项](../vsto/working-with-contact-items.md)
- [如何：以编程方式将条目添加到 Outlook 联系人](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [如何：以编程方式搜索特定联系人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [如何：以编程方式在联系人中的电子邮件地址搜索](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [如何：以编程方式删除 Outlook 联系人](../vsto/how-to-programmatically-delete-outlook-contacts.md)
