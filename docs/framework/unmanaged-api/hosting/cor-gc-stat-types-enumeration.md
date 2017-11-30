---
title: "Перечисление COR_GC_STAT_TYPES"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_STAT_TYPES
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_STAT_TYPES
helpviewer_keywords: COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4cf66026ecf92d0158a1010e82c078478c280f9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="a3f19-102">Перечисление COR_GC_STAT_TYPES</span><span class="sxs-lookup"><span data-stu-id="a3f19-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="a3f19-103">Указывает статистику, записываемую для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="a3f19-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3f19-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a3f19-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="a3f19-105">Примечания</span><span class="sxs-lookup"><span data-stu-id="a3f19-105">Remarks</span></span>  
 <span data-ttu-id="a3f19-106">Это перечисление указывает, какая именно статистика в [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) структуры должны задаваться [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="a3f19-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="a3f19-107">Члены</span><span class="sxs-lookup"><span data-stu-id="a3f19-107">Members</span></span>  
  
|<span data-ttu-id="a3f19-108">Член</span><span class="sxs-lookup"><span data-stu-id="a3f19-108">Member</span></span>|<span data-ttu-id="a3f19-109">Описание</span><span class="sxs-lookup"><span data-stu-id="a3f19-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="a3f19-110">Записи количество сборок мусора, выполненных для каждого поколения.</span><span class="sxs-lookup"><span data-stu-id="a3f19-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="a3f19-111">Записи об использовании и сборке мусора коллекции размер статистику памяти.</span><span class="sxs-lookup"><span data-stu-id="a3f19-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3f19-112">Требования</span><span class="sxs-lookup"><span data-stu-id="a3f19-112">Requirements</span></span>  
 <span data-ttu-id="a3f19-113">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3f19-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3f19-114">**Заголовок:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="a3f19-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="a3f19-115">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3f19-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3f19-116">См. также</span><span class="sxs-lookup"><span data-stu-id="a3f19-116">See Also</span></span>  
 [<span data-ttu-id="a3f19-117">COR_GC_STATS-структура</span><span class="sxs-lookup"><span data-stu-id="a3f19-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="a3f19-118">Перечисления размещения</span><span class="sxs-lookup"><span data-stu-id="a3f19-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)