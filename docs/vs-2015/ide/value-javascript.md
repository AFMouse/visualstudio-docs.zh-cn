---
title: '&lt;值&gt;(JavaScript) |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ac74dde41a2d6cea0a768cfc89838cc34ce41afd
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "54799137"
---
# <a name="ltvaluegt-javascript"></a>&lt;value&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定文档信息`get`和`set`ECMAScript 3 属性的函数。  
  
## <a name="syntax"></a>语法  
  
```  
<value type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID">description  
</value>  
```  
  
#### <a name="parameters"></a>参数  
 `type`  
 可选。 属性的数据类型。 类型可以是以下值之一：  
  
- 是在 ECMAScript 5 规范中，例如 ECMAScript 语言类型`Number`和`Object`。  
  
- DOM 对象，例如`HTMLElement`， `Window`，和`Document`。  
  
- JavaScript 构造函数。  
  
  `integer`  
  可选。 如果`type`是`Number`，指定属性是否为整数。 设置为`true`以指示该属性是一个整数; 否则，将设置为`false`。 Visual Studio 不使用此属性以提供 IntelliSense 信息。  
  
  `domElement`  
  可选。 此属性已弃用;`type`特性将优先于此属性。 此属性指定是否有案可稽的属性是 DOM 元素。 设置为`true`以指定该属性是一个 DOM 元素; 否则，将设置为`false`。 如果`type`未设置属性和`domElement`设置为`true`，IntelliSense 将有案可稽的属性视为`HTMLElement`执行语句完成时。  
  
  `mayBeNull`  
  可选。 指定是否可以设置有案可稽的属性为 null。 设置为`true`若要指示可以将属性设置为 null; 否则为设置为`false`。 默认值为 `false`。 Visual Studio 不使用此属性以提供 IntelliSense 信息。  
  
  `elementType`  
  可选。 如果`type`是`Array`，此属性指定数组中元素的类型。  
  
  `elementInteger`  
  可选。 如果`type`是`Array`并`elementType`是`Number`，此属性指定数组中的元素是否为整数。 设置为`true`来指示数组中的元素都是整数; 否则，将设置为`false`。 Visual Studio 不使用此属性以提供 IntelliSense 信息。  
  
  `elementDomElement`  
  可选。 此属性已弃用;`elementType`特性将优先于此属性。 如果`type`是`Array`，此属性指定数组中的元素是否 DOM 元素。 设置为`true`来指定元素的 DOM 元素; 否则，将设置为`false`。 如果`elementType`未设置属性和`elementDomElement`设置为`true`，IntelliSense 将作为数组中的每个元素`HTMLElement`执行语句完成时。  
  
  `elementMayBeNull`  
  可选。 如果`type`是`Array`，指定是否可以设置数组中的元素为 null。 设置为`true`若要指示为 null; 否则为，可以设置数组中的元素，将设置为`false`。 默认值为 `false`。 Visual Studio 不使用此属性以提供 IntelliSense 信息。  
  
  `locid`  
  可选。 有关属性的本地化信息的标识符。 该标识符是任一成员 ID 或其对应于`name`属性在 OpenAjax 元数据定义消息绑定中的值。 标识符类型取决于中指定的格式[ \<loc >](../ide/loc-javascript.md)元素。  
  
  `description`  
  可选。 属性的说明。  
  
## <a name="remarks"></a>备注  
 ECMAScript 5 属性使用[\<摘要 >](../ide/summary-javascript.md)元素。  
  
 使用`<value>`元素之前`get`或`set`函数。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何使用`<value>`元素上的`get`函数。  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [XML 文档注释](../ide/xml-documentation-comments-javascript.md)
