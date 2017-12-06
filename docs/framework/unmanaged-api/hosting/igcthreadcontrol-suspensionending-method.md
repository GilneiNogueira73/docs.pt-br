---
title: "Método IGCThreadControl::SuspensionEnding"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCThreadControl.SuspensionEnding
api_location: mscoree.dll
api_type: COM
f1_keywords: SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e4460d2b0eaf10d20ddd0c3641279a8ffc05c245
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="244c4-102">Método IGCThreadControl::SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="244c4-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="244c4-103">Notifica o host que o tempo de execução está retomando threads após uma coleta de lixo ou outros suspensão.</span><span class="sxs-lookup"><span data-stu-id="244c4-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="244c4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="244c4-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="244c4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="244c4-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="244c4-106">[in] A geração na qual uma coleta de lixo foi executada.</span><span class="sxs-lookup"><span data-stu-id="244c4-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="244c4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="244c4-107">Remarks</span></span>  
 <span data-ttu-id="244c4-108">Não reagendar qualquer threads durante o `SuspensionEnding` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="244c4-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="244c4-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="244c4-109">Requirements</span></span>  
 <span data-ttu-id="244c4-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="244c4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="244c4-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="244c4-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="244c4-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="244c4-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="244c4-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="244c4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244c4-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="244c4-114">See Also</span></span>  
 [<span data-ttu-id="244c4-115">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="244c4-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)