---
title: CA1302:请不要对区域设置特定的字符串进行硬编码
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a52add4453276ebf415b47f7f50e74b51a573306
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970603"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302:请不要对区域设置特定的字符串进行硬编码

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|类别|Microsoft.Globalization|
|是否重大更改|非换行|

## <a name="cause"></a>原因
 一种方法使用字符串文本表示某些系统文件夹的路径的一部分。

## <a name="rule-description"></a>规则说明
 <xref:System.Environment.SpecialFolder?displayProperty=fullName>枚举包含的特殊系统文件夹，请参阅的成员。 这些文件夹的位置可以具有不同的值在不同操作系统上，用户可以更改某些位置，位置已经进行了本地化。 特殊文件夹的一个示例是系统文件夹，即"C:\WINDOWS\system32"上[!INCLUDE[winxp](../code-quality/includes/winxp_md.md)]但上的"C:\WINNT\system32" [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]。 <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName>方法返回与之关联的位置<xref:System.Environment.SpecialFolder>枚举。 由返回的位置<xref:System.Environment.GetFolderPath%2A>进行本地化，且适用于当前正在运行的计算机。

 此规则基于进行标记，通过使用检索的文件夹路径<xref:System.Environment.GetFolderPath%2A>方法转换成单独的目录级别。 每个字符串进行比较的令牌。 如果找到匹配项，则假定该方法生成一个字符串，表示与令牌相关联的系统位置。 对于可移植性和可本地化性，使用<xref:System.Environment.GetFolderPath%2A>方法来检索而不是使用字符串文本的特殊系统文件夹的位置。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要解决此规则的冲突，检索的位置，通过使用<xref:System.Environment.GetFolderPath%2A>方法。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 则可以安全地禁止显示此规则的警告，如果字符串文字不用于到一个与之关联的系统位置，请参阅<xref:System.Environment.SpecialFolder>枚举。

## <a name="example"></a>示例
 下面的示例生成与该规则将生成三个警告的常见应用程序数据文件夹的路径。 接下来，该示例通过检索路径<xref:System.Environment.GetFolderPath%2A>方法。

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>相关的规则
 [CA1303:不要将文本作为本地化参数传递](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)