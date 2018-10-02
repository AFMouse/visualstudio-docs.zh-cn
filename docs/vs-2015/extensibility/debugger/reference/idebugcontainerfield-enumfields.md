---
title: IDebugContainerField::EnumFields |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a1fb33a65fb0bb86d3c043dd250b60b1533fed4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47478391"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主题的最新版本，请参阅[IDebugContainerField::EnumFields](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcontainerfield-enumfields)。  
  
创建容器的字段的枚举器。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwKindFilter`  
 [in]组合[FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)选择要枚举的字段的常量。 字段类型可以描述存储类型，如类或基元，或特定的信息，如本地、 参数或"this"指针。  
  
 `dwModifiersFilter`  
 [in]组合[FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)选择要枚举的字段的常量。 字段修饰符可以是访问权限，如公共或私有或存储信息，如虚拟、 静态的或最后一个。  
  
 `pszNameFilter`  
 [in]要枚举的字段的名称。 如果要返回所有字段，这可以是 null 值。  
  
 `nameMatch`  
 [in]中的值[NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)枚举，用于控制是否搜索是否区分大小写。  
  
 `ppEnum`  
 [out]返回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)对象，表示的字段的列表。 如果没有字段，则返回 null 值。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回 S_OK 或 S_FALSE 如果没有字段。 否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 `dwKindFilter`， `dwModifiersFilter`，和`pszNameFilter`参数可以结合使用，例如，若要选择名为"MyMethod"的所有公共虚拟方法。  
  
## <a name="see-also"></a>请参阅  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
