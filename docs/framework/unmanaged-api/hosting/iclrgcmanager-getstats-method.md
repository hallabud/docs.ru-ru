---
title: "Метод ICLRGCManager::GetStats"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager.GetStats
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06d52bd0348e4667f1e3ec43a371021922f12ded
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="f0009-102">Метод ICLRGCManager::GetStats</span><span class="sxs-lookup"><span data-stu-id="f0009-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="f0009-103">Получает набор текущих статистических данных о системе сборки мусора среды CLR.</span><span class="sxs-lookup"><span data-stu-id="f0009-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0009-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f0009-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0009-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="f0009-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="f0009-106">[in, out] Объект [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) экземпляр, содержащий запрошенную статистики.</span><span class="sxs-lookup"><span data-stu-id="f0009-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0009-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f0009-107">Return Value</span></span>  
  
|<span data-ttu-id="f0009-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0009-108">HRESULT</span></span>|<span data-ttu-id="f0009-109">Описание</span><span class="sxs-lookup"><span data-stu-id="f0009-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0009-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0009-110">S_OK</span></span>|<span data-ttu-id="f0009-111">`GetStats`успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="f0009-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="f0009-112">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f0009-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f0009-113">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="f0009-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f0009-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f0009-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f0009-115">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="f0009-115">The call timed out.</span></span>|  
|<span data-ttu-id="f0009-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f0009-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f0009-117">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="f0009-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f0009-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f0009-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f0009-119">Событие было отменено заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="f0009-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f0009-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f0009-120">E_FAIL</span></span>|<span data-ttu-id="f0009-121">Неизвестная Неустранимая ошибка.</span><span class="sxs-lookup"><span data-stu-id="f0009-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f0009-122">После метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="f0009-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f0009-123">Последующие вызовы размещение методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f0009-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0009-124">Примечания</span><span class="sxs-lookup"><span data-stu-id="f0009-124">Remarks</span></span>  
 <span data-ttu-id="f0009-125">Среда CLR вычисляет и возвращает только те статистические данные, которые определяются `Flags` поле `pStats`.</span><span class="sxs-lookup"><span data-stu-id="f0009-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="f0009-126">Задать `Flags` на один или несколько значений [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) перечисления, чтобы указать, какая именно статистика в [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) структуры должны быть заданы.</span><span class="sxs-lookup"><span data-stu-id="f0009-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="f0009-127">Ниже приведен пример использования:</span><span class="sxs-lookup"><span data-stu-id="f0009-127">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f0009-128">Требования</span><span class="sxs-lookup"><span data-stu-id="f0009-128">Requirements</span></span>  
 <span data-ttu-id="f0009-129">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0009-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0009-130">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f0009-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0009-131">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0009-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0009-132">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0009-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0009-133">См. также</span><span class="sxs-lookup"><span data-stu-id="f0009-133">See Also</span></span>  
 [<span data-ttu-id="f0009-134">Автоматическое управление памятью</span><span class="sxs-lookup"><span data-stu-id="f0009-134">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="f0009-135">COR_GC_STATS-структура</span><span class="sxs-lookup"><span data-stu-id="f0009-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="f0009-136">COR_GC_STAT_TYPES-перечисление</span><span class="sxs-lookup"><span data-stu-id="f0009-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)  
 [<span data-ttu-id="f0009-137">Сборка мусора</span><span class="sxs-lookup"><span data-stu-id="f0009-137">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="f0009-138">ICLRControl-интерфейс</span><span class="sxs-lookup"><span data-stu-id="f0009-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="f0009-139">Iclrgcmanager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="f0009-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="f0009-140">Интерфейсы размещения CLR</span><span class="sxs-lookup"><span data-stu-id="f0009-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="f0009-141">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="f0009-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="f0009-142">Размещение</span><span class="sxs-lookup"><span data-stu-id="f0009-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)