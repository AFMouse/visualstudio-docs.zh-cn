---
title: 缺少日期对象 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a53ff758622cf719c2b10ea47fc516ac8684eb6a
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842242"
---
# <a name="date-object-expected"></a>缺少日期对象
你尝试调用**Date.prototype.toString**或**Date.prototype.valueOf**方法以外的类型的对象上`Date`。 调用此类型的对象的类型必须是`Date`。 例如：  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   仅调用**Date.prototype.toString**或**Date.prototype.valueOf**类型的对象上的方法`Date`。  
  
## <a name="see-also"></a>请参阅  
 [Date 对象](../../javascript/reference/date-object-javascript.md)   
 [getDate 方法 (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [内部对象](../../javascript/intrinsic-objects-javascript.md)