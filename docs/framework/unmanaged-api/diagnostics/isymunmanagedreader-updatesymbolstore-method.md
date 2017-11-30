---
title: "Метод ISymUnmanagedReader::UpdateSymbolStore"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.UpdateSymbolStore
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cfea77814069f6689f7492608548836fdafa591b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="5e0d2-102">Метод ISymUnmanagedReader::UpdateSymbolStore</span><span class="sxs-lookup"><span data-stu-id="5e0d2-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="5e0d2-103">Обновляет существующее хранилище символов разностным хранилищем символов.</span><span class="sxs-lookup"><span data-stu-id="5e0d2-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="5e0d2-104">Этот метод используется в сценариях edit and continue для обновления хранилища символов в соответствии с изменениями в исходном переносимом исполняемом (PE) файле.</span><span class="sxs-lookup"><span data-stu-id="5e0d2-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e0d2-105">Необходимо указать только одно из `filename` или `pIStream` параметров, не оба.</span><span class="sxs-lookup"><span data-stu-id="5e0d2-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="5e0d2-106">Если `filename` указан, обновляется в хранилище символов с символами в этом файле.</span><span class="sxs-lookup"><span data-stu-id="5e0d2-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="5e0d2-107">Если `pIStream` указан, хранилище будет обновлено с данными из <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="5e0d2-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e0d2-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5e0d2-108">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e0d2-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="5e0d2-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="5e0d2-110">[in] Имя файла, содержащего хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="5e0d2-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="5e0d2-111">[in] Файловый поток, используемый в качестве альтернативы для `filename` параметра.</span><span class="sxs-lookup"><span data-stu-id="5e0d2-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e0d2-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5e0d2-112">Return Value</span></span>  
 <span data-ttu-id="5e0d2-113">Значение S_OK, если метод выполнен успешно; в противном случае — значение E_FAIL или другим кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="5e0d2-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e0d2-114">Требования</span><span class="sxs-lookup"><span data-stu-id="5e0d2-114">Requirements</span></span>  
 <span data-ttu-id="5e0d2-115">**Заголовок:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5e0d2-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e0d2-116">См. также</span><span class="sxs-lookup"><span data-stu-id="5e0d2-116">See Also</span></span>  
 [<span data-ttu-id="5e0d2-117">ISymUnmanagedReader-интерфейс</span><span class="sxs-lookup"><span data-stu-id="5e0d2-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)