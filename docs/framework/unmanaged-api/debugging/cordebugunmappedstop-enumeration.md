---
title: Перечисление CorDebugUnmappedStop
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d812a452910913f169d4377bafa82e823c533d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404421"
---
# <a name="cordebugunmappedstop-enumeration"></a>Перечисление CorDebugUnmappedStop
Указывает тип несопоставимого кода, который может привести к прерыванию выполнения кода пошаговым средством.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|`STOP_NONE`|Не останавливайте в любой тип несопоставимого кода.|  
|`STOP_PROLOG`|Остановите кода пролога.|  
|`STOP_EPILOG`|Остановится в коде эпилога.|  
|`STOP_NO_MAPPING_INFO`|Остановится в коде, не имеет сопоставления информации.|  
|`STOP_OTHER_UNMAPPED`|Остановится в неуправляемом коде, который не помещается в прологе, эпилога, сведения о сопоставлении нет или неуправляемой категории.|  
|`STOP_UNMANAGED`|Остановится в неуправляемом коде. Это значение допустимо только при отладке взаимодействия.|  
|`STOP_ALL`|Останавливается во всех типах неуправляемого кода.|  
  
## <a name="remarks"></a>Примечания  
 Используйте [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) метод, чтобы задать флаги, указывающие несопоставимого кода, в котором будет остановлено пошаговым.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Перечисления отладки](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
