---
title: "Método IHostMemoryManager::CreateMAlloc"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.CreateMAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::CreateMAlloc
helpviewer_keywords:
- CreateAlloc method [.NET Framework hosting]
- IHostMemoryManager::CreateMAlloc method [.NET Framework hosting]
ms.assetid: 9ee6e052-bef7-4350-9e4f-edfffd99ad6f
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25b4f8a23d03b3d839aeab5d2f571cb4f98f1ec5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="0d04b-102">Método IHostMemoryManager::CreateMAlloc</span><span class="sxs-lookup"><span data-stu-id="0d04b-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="0d04b-103">Obtém um ponteiro de interface para um [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instância que é usada para fazer solicitações de alocação de um heap criado pelo host.</span><span class="sxs-lookup"><span data-stu-id="0d04b-103">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d04b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d04b-104">Syntax</span></span>  
  
```  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d04b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0d04b-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="0d04b-106">[in] Uma combinação de [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) sinalizadores que especifica as características da memória alocada.</span><span class="sxs-lookup"><span data-stu-id="0d04b-106">[in] A combination of [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="0d04b-107">[out] Um ponteiro para o endereço de um `IHostMAlloc` instância fornecida pelo host.</span><span class="sxs-lookup"><span data-stu-id="0d04b-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d04b-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0d04b-108">Return Value</span></span>  
  
|<span data-ttu-id="0d04b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0d04b-109">HRESULT</span></span>|<span data-ttu-id="0d04b-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d04b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0d04b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0d04b-111">S_OK</span></span>|<span data-ttu-id="0d04b-112">`CreateMAlloc`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="0d04b-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="0d04b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0d04b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0d04b-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0d04b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0d04b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0d04b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0d04b-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="0d04b-116">The call timed out.</span></span>|  
|<span data-ttu-id="0d04b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0d04b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0d04b-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0d04b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0d04b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0d04b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0d04b-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="0d04b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0d04b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0d04b-121">E_FAIL</span></span>|<span data-ttu-id="0d04b-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0d04b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0d04b-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="0d04b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0d04b-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0d04b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0d04b-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0d04b-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0d04b-126">Não há memória física estava disponível para concluir a solicitação de alocação.</span><span class="sxs-lookup"><span data-stu-id="0d04b-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d04b-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d04b-127">Remarks</span></span>  
 <span data-ttu-id="0d04b-128">`CreateMAlloc`Retorna um objeto que permite que o CLR fazer solicitações de alocação por meio do host em vez de usar as funções padrão do Win32.</span><span class="sxs-lookup"><span data-stu-id="0d04b-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d04b-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d04b-129">Requirements</span></span>  
 <span data-ttu-id="0d04b-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d04b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d04b-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0d04b-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d04b-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0d04b-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d04b-133">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d04b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d04b-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d04b-134">See Also</span></span>  
 [<span data-ttu-id="0d04b-135">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="0d04b-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [<span data-ttu-id="0d04b-136">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="0d04b-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)