---
title: "Метод IHostTask::Alert"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Alert
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bf48d3decd071c4c0f483476b885fc023b466f3e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="265fc-102">Метод IHostTask::Alert</span><span class="sxs-lookup"><span data-stu-id="265fc-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="265fc-103">Запросы, что узел пробуждения задач, представленный текущим [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) экземпляра, поэтому задача может быть прервана.</span><span class="sxs-lookup"><span data-stu-id="265fc-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="265fc-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="265fc-104">Syntax</span></span>  
  
```  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="265fc-105">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="265fc-105">Return Value</span></span>  
  
|<span data-ttu-id="265fc-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="265fc-106">HRESULT</span></span>|<span data-ttu-id="265fc-107">Описание</span><span class="sxs-lookup"><span data-stu-id="265fc-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="265fc-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="265fc-108">S_OK</span></span>|<span data-ttu-id="265fc-109">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="265fc-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="265fc-110">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="265fc-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="265fc-111">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="265fc-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="265fc-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="265fc-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="265fc-113">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="265fc-113">The call timed out.</span></span>|  
|<span data-ttu-id="265fc-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="265fc-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="265fc-115">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="265fc-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="265fc-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="265fc-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="265fc-117">Событие было отменено заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="265fc-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="265fc-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="265fc-118">E_FAIL</span></span>|<span data-ttu-id="265fc-119">Неизвестная Неустранимая ошибка.</span><span class="sxs-lookup"><span data-stu-id="265fc-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="265fc-120">Если метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="265fc-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="265fc-121">Последующие вызовы размещение методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="265fc-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="265fc-122">Примечания</span><span class="sxs-lookup"><span data-stu-id="265fc-122">Remarks</span></span>  
 <span data-ttu-id="265fc-123">Среда CLR вызывает `Alert` метод при <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> вызова из пользовательского кода, или когда <xref:System.AppDomain> связанную с текущим <xref:System.Threading.Thread> завершает работу.</span><span class="sxs-lookup"><span data-stu-id="265fc-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="265fc-124">Узел должен возвращаться немедленно, поскольку вызов выполняется асинхронно.</span><span class="sxs-lookup"><span data-stu-id="265fc-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="265fc-125">Если узел не может немедленно предупреждения задачи, оно должно инициироваться следующий раз, он переходит в состояние, в котором можно оповещения.</span><span class="sxs-lookup"><span data-stu-id="265fc-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="265fc-126">`Alert`затрагивает только те задачи, для которых прошел среда выполнения [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) значение WAIT_ALERTABLE для методов, таких как [соединения](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="265fc-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="265fc-127">Требования</span><span class="sxs-lookup"><span data-stu-id="265fc-127">Requirements</span></span>  
 <span data-ttu-id="265fc-128">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="265fc-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="265fc-129">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="265fc-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="265fc-130">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="265fc-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="265fc-131">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="265fc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="265fc-132">См. также</span><span class="sxs-lookup"><span data-stu-id="265fc-132">See Also</span></span>  
 [<span data-ttu-id="265fc-133">ICLRTask-интерфейс</span><span class="sxs-lookup"><span data-stu-id="265fc-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="265fc-134">ICLRTaskManager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="265fc-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="265fc-135">IHostTask-интерфейс</span><span class="sxs-lookup"><span data-stu-id="265fc-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="265fc-136">IHostTaskManager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="265fc-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)