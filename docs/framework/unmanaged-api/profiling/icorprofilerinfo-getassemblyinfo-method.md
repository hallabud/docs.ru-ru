---
title: "Метод ICorProfilerInfo::GetAssemblyInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetAssemblyInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d4eab4a4bfbf91fd86a3742600f3383a8d374905
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="4b8d6-102">Метод ICorProfilerInfo::GetAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="4b8d6-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="4b8d6-103">Принимает идентификатор сборки и возвращает имя сборки, а также идентификатор ее модуля манифеста.</span><span class="sxs-lookup"><span data-stu-id="4b8d6-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b8d6-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4b8d6-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b8d6-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="4b8d6-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="4b8d6-106">[in] Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="4b8d6-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="4b8d6-107">[in] Длина `szName` в символах.</span><span class="sxs-lookup"><span data-stu-id="4b8d6-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4b8d6-108">[out] Указатель на общую длину имени сборки в символах.</span><span class="sxs-lookup"><span data-stu-id="4b8d6-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="4b8d6-109">[out] Буфер расширенных символов, предоставленный вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="4b8d6-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="4b8d6-110">Когда функция возвращает значение, оно содержит имя сборки.</span><span class="sxs-lookup"><span data-stu-id="4b8d6-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="4b8d6-111">[out] Указатель на идентификатор домена приложения, содержащего эту сборку.</span><span class="sxs-lookup"><span data-stu-id="4b8d6-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="4b8d6-112">[out] Указатель на идентификатор модуля манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="4b8d6-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b8d6-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="4b8d6-113">Remarks</span></span>  
 <span data-ttu-id="4b8d6-114">После возврата этого метода необходимо убедиться, что буфер `szName` был достаточно велик, чтобы вместить в себя полное имя сборки.</span><span class="sxs-lookup"><span data-stu-id="4b8d6-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="4b8d6-115">Для этого сравните значение, на которое указывает параметр `pcchName`, со значением параметра `cchName`.</span><span class="sxs-lookup"><span data-stu-id="4b8d6-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="4b8d6-116">Если параметр `pcchName` указывает на значение, превышающее значение `cchName`, выделите буфер `szName` большего размера, обновите параметр `cchName`, задав новый, больший размер, и вызовите метод `GetAssemblyInfo` снова.</span><span class="sxs-lookup"><span data-stu-id="4b8d6-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="4b8d6-117">Кроме того, сначала можно вызвать метод `GetAssemblyInfo` с буфером `szName` нулевой длины для получения правильного размера буфера.</span><span class="sxs-lookup"><span data-stu-id="4b8d6-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="4b8d6-118">Затем можно настроить размер буфера, исходя из значения, возвращенного в `pcchName`, и вызвать метод `GetAssemblyInfo` снова.</span><span class="sxs-lookup"><span data-stu-id="4b8d6-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b8d6-119">Требования</span><span class="sxs-lookup"><span data-stu-id="4b8d6-119">Requirements</span></span>  
 <span data-ttu-id="4b8d6-120">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b8d6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b8d6-121">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4b8d6-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4b8d6-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b8d6-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b8d6-123">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b8d6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b8d6-124">См. также</span><span class="sxs-lookup"><span data-stu-id="4b8d6-124">See Also</span></span>  
 [<span data-ttu-id="4b8d6-125">ICorProfilerInfo-интерфейс</span><span class="sxs-lookup"><span data-stu-id="4b8d6-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="4b8d6-126">Интерфейсы профилирования</span><span class="sxs-lookup"><span data-stu-id="4b8d6-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="4b8d6-127">Профилирование</span><span class="sxs-lookup"><span data-stu-id="4b8d6-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)