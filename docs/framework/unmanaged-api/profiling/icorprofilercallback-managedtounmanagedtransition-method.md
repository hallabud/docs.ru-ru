---
title: "Метод ICorProfilerCallback::ManagedToUnmanagedTransition"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ManagedToUnmanagedTransition
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9da8dd44d5b87cd1c65b8b8837c9dd378039d332
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="7afce-102">Метод ICorProfilerCallback::ManagedToUnmanagedTransition</span><span class="sxs-lookup"><span data-stu-id="7afce-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>
<span data-ttu-id="7afce-103">Уведомляет профилировщик о переходе из управляемого кода в неуправляемый код.</span><span class="sxs-lookup"><span data-stu-id="7afce-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7afce-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7afce-104">Syntax</span></span>  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7afce-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="7afce-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7afce-106">[in] Идентификатор функции, которая вызывается.</span><span class="sxs-lookup"><span data-stu-id="7afce-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="7afce-107">[in] Значение [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) перечисления, которое указывает, произошло из-за вызовов неуправляемого кода из управляемого кода или из-за возврат из управляемой функции, вызывается один из неуправляемого перехода.</span><span class="sxs-lookup"><span data-stu-id="7afce-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7afce-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="7afce-108">Remarks</span></span>  
 <span data-ttu-id="7afce-109">Если значение `reason` является COR_PRF_TRANSITION_CALL, функция, идентификатор имеет неуправляемую функцию, который никогда не будет компилироваться с помощью компилятора just-in-time.</span><span class="sxs-lookup"><span data-stu-id="7afce-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="7afce-110">Неуправляемые функции имеют основные сведения, связанные с ними, такие как имя и некоторые метаданные.</span><span class="sxs-lookup"><span data-stu-id="7afce-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="7afce-111">Если неуправляемая функция была вызвана с помощью неявного вызова (PInvoke), среда выполнения не может определить назначение вызова и значение `functionId` будет иметь значение null.</span><span class="sxs-lookup"><span data-stu-id="7afce-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="7afce-112">Дополнительные сведения о неявный PInvoke см. в разделе [с помощью взаимодействия C++ (неявный PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span><span class="sxs-lookup"><span data-stu-id="7afce-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7afce-113">Требования</span><span class="sxs-lookup"><span data-stu-id="7afce-113">Requirements</span></span>  
 <span data-ttu-id="7afce-114">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7afce-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7afce-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7afce-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7afce-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7afce-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7afce-117">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7afce-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7afce-118">См. также</span><span class="sxs-lookup"><span data-stu-id="7afce-118">See Also</span></span>  
 [<span data-ttu-id="7afce-119">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="7afce-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="7afce-120">Метод UnmanagedToManagedTransition</span><span class="sxs-lookup"><span data-stu-id="7afce-120">UnmanagedToManagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)  
 [<span data-ttu-id="7afce-121">Использование явного вызова Pinvoke в C++ (атрибут DllImport)</span><span class="sxs-lookup"><span data-stu-id="7afce-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)