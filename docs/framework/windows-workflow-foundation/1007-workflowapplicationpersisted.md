---
title: 1007 - WorkflowApplicationPersisted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4ea4452-28e3-4e66-93c6-eb12ee29bcb1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cae6ba6f3d86fa0a7c123a82ee61b9d01cf352c5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="1007---workflowapplicationpersisted"></a><span data-ttu-id="3c62c-102">1007 - WorkflowApplicationPersisted</span><span class="sxs-lookup"><span data-stu-id="3c62c-102">1007 - WorkflowApplicationPersisted</span></span>
## <a name="properties"></a><span data-ttu-id="3c62c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3c62c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3c62c-104">ID</span><span class="sxs-lookup"><span data-stu-id="3c62c-104">ID</span></span>|<span data-ttu-id="3c62c-105">1007</span><span class="sxs-lookup"><span data-stu-id="3c62c-105">1007</span></span>|  
|<span data-ttu-id="3c62c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="3c62c-106">Keywords</span></span>|<span data-ttu-id="3c62c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3c62c-107">WFRuntime</span></span>|  
|<span data-ttu-id="3c62c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="3c62c-108">Level</span></span>|<span data-ttu-id="3c62c-109">Informações</span><span class="sxs-lookup"><span data-stu-id="3c62c-109">Information</span></span>|  
|<span data-ttu-id="3c62c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="3c62c-110">Channel</span></span>|<span data-ttu-id="3c62c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="3c62c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3c62c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c62c-112">Description</span></span>  
 <span data-ttu-id="3c62c-113">Indica que um aplicativo de fluxo de trabalho persistiu.</span><span class="sxs-lookup"><span data-stu-id="3c62c-113">Indicates a workflow application has persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3c62c-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="3c62c-114">Message</span></span>  
 <span data-ttu-id="3c62c-115">Identificação de WorkflowApplication: “%1 " foi persistente.</span><span class="sxs-lookup"><span data-stu-id="3c62c-115">WorkflowApplication Id: '%1' was Persisted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3c62c-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="3c62c-116">Details</span></span>  
  
|<span data-ttu-id="3c62c-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="3c62c-117">Data Item Name</span></span>|<span data-ttu-id="3c62c-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="3c62c-118">Data Item Type</span></span>|<span data-ttu-id="3c62c-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c62c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3c62c-120">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="3c62c-120">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="3c62c-121">A identificação do aplicativo de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3c62c-121">The workflow application id</span></span>|  
|<span data-ttu-id="3c62c-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3c62c-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3c62c-123">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3c62c-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|