---
title: "Метод IMetaDataAssemblyEmit::DefineAssembly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 86002eb38d72ee628dbf54d0b5691f0816e6f996
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="7652d-102">Метод IMetaDataAssemblyEmit::DefineAssembly</span><span class="sxs-lookup"><span data-stu-id="7652d-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="7652d-103">Создает `Assembly` структура содержащую метаданные для указанной сборки и возвращает связанный токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="7652d-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7652d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7652d-104">Syntax</span></span>  
  
```  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,   
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7652d-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="7652d-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="7652d-106">[in] Открытый ключ, который идентифицирует издателя сборки, или значение NULL, если сборка не имеет строгого имени.</span><span class="sxs-lookup"><span data-stu-id="7652d-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="7652d-107">[in] Размер в байтах `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="7652d-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="7652d-108">[in] Идентификатор алгоритма хэширования, используемого для шифрования файлов в сборке, или значение NULL для задания алгоритма SHA-1.</span><span class="sxs-lookup"><span data-stu-id="7652d-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="7652d-109">[in] Понятное текстовое имя сборки.</span><span class="sxs-lookup"><span data-stu-id="7652d-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="7652d-110">Это значение не должно превышать 1024 символа.</span><span class="sxs-lookup"><span data-stu-id="7652d-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="7652d-111">[in] Указатель на экземпляр ASSEMBLYMETADATA, содержащий сведения о версии, платформы и языковой стандарт для сборки.</span><span class="sxs-lookup"><span data-stu-id="7652d-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="7652d-112">[in] Сочетание [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) значения, описывающие функции сборки.</span><span class="sxs-lookup"><span data-stu-id="7652d-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="7652d-113">[out] Указатель на токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="7652d-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7652d-114">Примечания</span><span class="sxs-lookup"><span data-stu-id="7652d-114">Remarks</span></span>  
 <span data-ttu-id="7652d-115">Только один `Assembly` структуру метаданных можно определить в манифесте.</span><span class="sxs-lookup"><span data-stu-id="7652d-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7652d-116">Требования</span><span class="sxs-lookup"><span data-stu-id="7652d-116">Requirements</span></span>  
 <span data-ttu-id="7652d-117">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7652d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7652d-118">**Заголовок:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7652d-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7652d-119">**Библиотека:** включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7652d-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7652d-120">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7652d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7652d-121">См. также</span><span class="sxs-lookup"><span data-stu-id="7652d-121">See Also</span></span>  
 [<span data-ttu-id="7652d-122">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="7652d-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)