---
title: "ICorDebugFunctionBreakpoint интерфейс1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunctionBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunctionBreakpoint
helpviewer_keywords: ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 910317bea8af3a80ee66544651de2372808734bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctionbreakpoint-interface1"></a><span data-ttu-id="ae81f-102">ICorDebugFunctionBreakpoint интерфейс1</span><span class="sxs-lookup"><span data-stu-id="ae81f-102">ICorDebugFunctionBreakpoint Interface1</span></span>
<span data-ttu-id="ae81f-103">Расширяет интерфейс ICorDebugBreakpoint для поддержки точек останова в функциях.</span><span class="sxs-lookup"><span data-stu-id="ae81f-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae81f-104">Методы</span><span class="sxs-lookup"><span data-stu-id="ae81f-104">Methods</span></span>  
  
|<span data-ttu-id="ae81f-105">Метод</span><span class="sxs-lookup"><span data-stu-id="ae81f-105">Method</span></span>|<span data-ttu-id="ae81f-106">Описание</span><span class="sxs-lookup"><span data-stu-id="ae81f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae81f-107">Метод GetFunction</span><span class="sxs-lookup"><span data-stu-id="ae81f-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="ae81f-108">Получает указатель на интерфейс ICorDebugFunction, который ссылается на функцию, в которой задана точка останова.</span><span class="sxs-lookup"><span data-stu-id="ae81f-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="ae81f-109">GetOffset-метод</span><span class="sxs-lookup"><span data-stu-id="ae81f-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="ae81f-110">Получает смещение от точки останова в функции.</span><span class="sxs-lookup"><span data-stu-id="ae81f-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae81f-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="ae81f-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae81f-112">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="ae81f-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae81f-113">Требования</span><span class="sxs-lookup"><span data-stu-id="ae81f-113">Requirements</span></span>  
 <span data-ttu-id="ae81f-114">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae81f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae81f-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae81f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae81f-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae81f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae81f-117">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae81f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae81f-118">См. также</span><span class="sxs-lookup"><span data-stu-id="ae81f-118">See Also</span></span>  
 [<span data-ttu-id="ae81f-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="ae81f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)