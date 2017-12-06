---
title: "Método IHostManualEvent::Set"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostManualEvent.Set
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostManualEvent::Set
helpviewer_keywords:
- Set method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Set method [.NET Framework hosting]
ms.assetid: e930c174-f71d-4faa-bb59-f0fb3df4d77b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f093e1278e74553ed78445e0cb83127a219e622
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="25e6c-102">Método IHostManualEvent::Set</span><span class="sxs-lookup"><span data-stu-id="25e6c-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="25e6c-103">Define o atual [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instância para um estado sinalizado.</span><span class="sxs-lookup"><span data-stu-id="25e6c-103">Sets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25e6c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25e6c-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="25e6c-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="25e6c-105">Return Value</span></span>  
  
|<span data-ttu-id="25e6c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25e6c-106">HRESULT</span></span>|<span data-ttu-id="25e6c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="25e6c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="25e6c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="25e6c-108">S_OK</span></span>|<span data-ttu-id="25e6c-109">`Set`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="25e6c-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="25e6c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="25e6c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="25e6c-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="25e6c-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="25e6c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="25e6c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="25e6c-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="25e6c-113">The call timed out.</span></span>|  
|<span data-ttu-id="25e6c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="25e6c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="25e6c-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="25e6c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="25e6c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="25e6c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="25e6c-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="25e6c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="25e6c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="25e6c-118">E_FAIL</span></span>|<span data-ttu-id="25e6c-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="25e6c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="25e6c-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="25e6c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="25e6c-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="25e6c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25e6c-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25e6c-122">Requirements</span></span>  
 <span data-ttu-id="25e6c-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25e6c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25e6c-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="25e6c-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25e6c-125">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="25e6c-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25e6c-126">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25e6c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25e6c-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25e6c-127">See Also</span></span>  
 [<span data-ttu-id="25e6c-128">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="25e6c-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="25e6c-129">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="25e6c-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="25e6c-130">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="25e6c-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="25e6c-131">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="25e6c-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="25e6c-132">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="25e6c-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)