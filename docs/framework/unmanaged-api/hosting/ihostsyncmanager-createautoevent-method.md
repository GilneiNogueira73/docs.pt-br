---
title: "Método IHostSyncManager::CreateAutoEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateAutoEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e6a792ca9075e48a8092d92e1adf870174dd1af6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="819f7-102">Método IHostSyncManager::CreateAutoEvent</span><span class="sxs-lookup"><span data-stu-id="819f7-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="819f7-103">Cria um objeto de evento de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="819f7-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="819f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="819f7-104">Syntax</span></span>  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="819f7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="819f7-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="819f7-106">[out] Um ponteiro para o endereço de um [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instância implementada pelo host, ou nula se não foi possível criar o objeto de evento.</span><span class="sxs-lookup"><span data-stu-id="819f7-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="819f7-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="819f7-107">Return Value</span></span>  
  
|<span data-ttu-id="819f7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="819f7-108">HRESULT</span></span>|<span data-ttu-id="819f7-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="819f7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="819f7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="819f7-110">S_OK</span></span>|<span data-ttu-id="819f7-111">`CreateAutoEvent`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="819f7-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="819f7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="819f7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="819f7-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="819f7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="819f7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="819f7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="819f7-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="819f7-115">The call timed out.</span></span>|  
|<span data-ttu-id="819f7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="819f7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="819f7-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="819f7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="819f7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="819f7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="819f7-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="819f7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="819f7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="819f7-120">E_FAIL</span></span>|<span data-ttu-id="819f7-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="819f7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="819f7-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="819f7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="819f7-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="819f7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="819f7-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="819f7-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="819f7-125">Não havia memória suficiente disponível para criar o objeto de evento solicitado.</span><span class="sxs-lookup"><span data-stu-id="819f7-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="819f7-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="819f7-126">Remarks</span></span>  
 <span data-ttu-id="819f7-127">`CreateAutoEvent`cria um objeto de evento auto cujo estado é alterado automaticamente para não-sinalizado depois que o thread de espera foi liberado.</span><span class="sxs-lookup"><span data-stu-id="819f7-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="819f7-128">Esse método reflete o Win32 `CreateEvent` função com um valor de `false` especificado para o `bManualReset` parâmetro</span><span class="sxs-lookup"><span data-stu-id="819f7-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="819f7-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="819f7-129">Requirements</span></span>  
 <span data-ttu-id="819f7-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="819f7-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="819f7-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="819f7-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="819f7-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="819f7-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="819f7-133">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="819f7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="819f7-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="819f7-134">See Also</span></span>  
 [<span data-ttu-id="819f7-135">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="819f7-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="819f7-136">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="819f7-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="819f7-137">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="819f7-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="819f7-138">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="819f7-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)