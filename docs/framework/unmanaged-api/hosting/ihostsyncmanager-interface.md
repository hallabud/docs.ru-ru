---
title: "Интерфейс IHostSyncManager"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager
helpviewer_keywords: IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 951f7808e238f514ffcf19a8dda0033b7b07172c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="c7f65-102">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="c7f65-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="c7f65-103">Предоставляет методы, позволяющие общеязыковой среды выполнения (CLR), для создания примитивы синхронизации, вызвав узла вместо использования функций синхронизации Win32.</span><span class="sxs-lookup"><span data-stu-id="c7f65-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7f65-104">Методы</span><span class="sxs-lookup"><span data-stu-id="c7f65-104">Methods</span></span>  
  
|<span data-ttu-id="c7f65-105">Метод</span><span class="sxs-lookup"><span data-stu-id="c7f65-105">Method</span></span>|<span data-ttu-id="c7f65-106">Описание</span><span class="sxs-lookup"><span data-stu-id="c7f65-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7f65-107">CreateAutoEvent-метод</span><span class="sxs-lookup"><span data-stu-id="c7f65-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="c7f65-108">Создает объект события автоматического сброса.</span><span class="sxs-lookup"><span data-stu-id="c7f65-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="c7f65-109">Createcrst-метод</span><span class="sxs-lookup"><span data-stu-id="c7f65-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="c7f65-110">Создает объект критической секции для синхронизации.</span><span class="sxs-lookup"><span data-stu-id="c7f65-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="c7f65-111">Createcrstwithspincount-метод</span><span class="sxs-lookup"><span data-stu-id="c7f65-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="c7f65-112">Создает объект критической секции с прокруток для синхронизации.</span><span class="sxs-lookup"><span data-stu-id="c7f65-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="c7f65-113">Createmanualevent-метод</span><span class="sxs-lookup"><span data-stu-id="c7f65-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="c7f65-114">Создает объект события ручного сброса.</span><span class="sxs-lookup"><span data-stu-id="c7f65-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="c7f65-115">Createmonitorevent-метод</span><span class="sxs-lookup"><span data-stu-id="c7f65-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="c7f65-116">Создает объект, отслеживаемый события автоматического сброса.</span><span class="sxs-lookup"><span data-stu-id="c7f65-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="c7f65-117">Createrwlockreaderevent-метод</span><span class="sxs-lookup"><span data-stu-id="c7f65-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="c7f65-118">Создает объект события ручного сброса для реализации блокировки чтения.</span><span class="sxs-lookup"><span data-stu-id="c7f65-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="c7f65-119">Createrwlockwriterevent-метод</span><span class="sxs-lookup"><span data-stu-id="c7f65-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="c7f65-120">Создает объект события автоматического сброса для реализации блокировки модуля записи.</span><span class="sxs-lookup"><span data-stu-id="c7f65-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="c7f65-121">Createsemaphore-метод</span><span class="sxs-lookup"><span data-stu-id="c7f65-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="c7f65-122">Создает [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) объекта для среды CLR в качестве семафор для ожидания события.</span><span class="sxs-lookup"><span data-stu-id="c7f65-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="c7f65-123">Setclrsyncmanager-метод</span><span class="sxs-lookup"><span data-stu-id="c7f65-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="c7f65-124">Наборы [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) экземпляра для связи с текущим `IHostSyncManager` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="c7f65-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7f65-125">Примечания</span><span class="sxs-lookup"><span data-stu-id="c7f65-125">Remarks</span></span>  
 <span data-ttu-id="c7f65-126">Среда CLR обнаруживает реализация `IHostSyncManager` путем вызова [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) метод с `IID` из IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="c7f65-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7f65-127">Требования</span><span class="sxs-lookup"><span data-stu-id="c7f65-127">Requirements</span></span>  
 <span data-ttu-id="c7f65-128">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7f65-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7f65-129">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c7f65-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7f65-130">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7f65-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7f65-131">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7f65-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f65-132">См. также</span><span class="sxs-lookup"><span data-stu-id="c7f65-132">See Also</span></span>  
 [<span data-ttu-id="c7f65-133">ICLRSyncManager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="c7f65-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="c7f65-134">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="c7f65-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)