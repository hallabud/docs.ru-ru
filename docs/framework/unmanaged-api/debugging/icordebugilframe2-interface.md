---
title: ICorDebugILFrame2 интерфейс1
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccb39609b37aff09ac7890df562d6c08e3c3c159
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugilframe2-interface1"></a>ICorDebugILFrame2 интерфейс1
Логическое расширение интерфейса ICorDebugILFrame-интерфейс.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|Возвращает объект ICorDebugTypeEnum, содержащий <xref:System.Type> параметры в этом кадре.|  
|[Метод RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|Перераспределяет отредактированную функцию путем указания нового смещения MSIL.|  
  
## <a name="remarks"></a>Примечания  
  
> [!NOTE]
>  Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы отладки](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
