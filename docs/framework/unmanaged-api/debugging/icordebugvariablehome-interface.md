---
title: ICorDebugVariableHome 接口
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae11cdbbdb0fa63d1b903d18aff133344fd17f2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422528"
---
# <a name="icordebugvariablehome-interface"></a>ICorDebugVariableHome 接口
表示本地变量或函数参数。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetArgumentIndex 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|获取函数自变量的索引。|  
|[GetCode 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|获取包含此"icor 调试代码"实例`ICorDebugVariableHome`对象。|  
|[GetLiveRange 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|获取对其此变量是实时的本机范围。|  
|[GetLocationType 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|获取变量的本机位置的类型。|  
|[GetOffset 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|获取从基寄存器变量的偏移量。|  
|[GetRegister 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|获取包含的位置类型的变量的寄存器`VLT_REGISTER`，和的变量的位置类型的基寄存器`VLT_REGISTER_RELATIVE`。|  
|[GetSlotIndex 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|获取本地变量的托管的槽索引。|  
  
## <a name="example"></a>示例  
 下面的代码片段使用[ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)对象名为`pCode4`。  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>请参阅  
 [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugVariableHomeEnum 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
