---
title: 218 - ClientOperationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d5b6fcc1c7ec4dd2f2c008e9d8bcfb58b2b4991
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="5adad-102">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="5adad-102">218 - ClientOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="5adad-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5adad-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5adad-104">ID</span><span class="sxs-lookup"><span data-stu-id="5adad-104">ID</span></span>|<span data-ttu-id="5adad-105">218</span><span class="sxs-lookup"><span data-stu-id="5adad-105">218</span></span>|  
|<span data-ttu-id="5adad-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="5adad-106">Keywords</span></span>|<span data-ttu-id="5adad-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5adad-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="5adad-108">Nível</span><span class="sxs-lookup"><span data-stu-id="5adad-108">Level</span></span>|<span data-ttu-id="5adad-109">Informações</span><span class="sxs-lookup"><span data-stu-id="5adad-109">Information</span></span>|  
|<span data-ttu-id="5adad-110">Canal</span><span class="sxs-lookup"><span data-stu-id="5adad-110">Channel</span></span>|<span data-ttu-id="5adad-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="5adad-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5adad-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5adad-112">Description</span></span>  
 <span data-ttu-id="5adad-113">Esse evento é emitido por clientes depois que uma operação é concluída.</span><span class="sxs-lookup"><span data-stu-id="5adad-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="5adad-114">Para operações unidirecionais, isso é apenas depois que a mensagem é enviada com êxito.</span><span class="sxs-lookup"><span data-stu-id="5adad-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="5adad-115">Para operações de solicitação-resposta, isso é após o recebimento da resposta.</span><span class="sxs-lookup"><span data-stu-id="5adad-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5adad-116">Mensagem</span><span class="sxs-lookup"><span data-stu-id="5adad-116">Message</span></span>  
 <span data-ttu-id="5adad-117">O cliente concluiu a execução da ação '%1' associada ao contrato '%2'.</span><span class="sxs-lookup"><span data-stu-id="5adad-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="5adad-118">A mensagem foi enviada para '%3'.</span><span class="sxs-lookup"><span data-stu-id="5adad-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5adad-119">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5adad-119">Details</span></span>  
  
|<span data-ttu-id="5adad-120">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="5adad-120">Data Item Name</span></span>|<span data-ttu-id="5adad-121">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="5adad-121">Data Item Type</span></span>|<span data-ttu-id="5adad-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="5adad-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5adad-123">Ação</span><span class="sxs-lookup"><span data-stu-id="5adad-123">Action</span></span>|<span data-ttu-id="5adad-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="5adad-124">xs:string</span></span>|<span data-ttu-id="5adad-125">O cabeçalho de ação SOAP da mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="5adad-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="5adad-126">Nome do contrato</span><span class="sxs-lookup"><span data-stu-id="5adad-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="5adad-127">O nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="5adad-127">The name of the contract.</span></span> <span data-ttu-id="5adad-128">Exemplo: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="5adad-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="5adad-129">Destino</span><span class="sxs-lookup"><span data-stu-id="5adad-129">Destination</span></span>|`xs:string`|<span data-ttu-id="5adad-130">O endereço do ponto de extremidade de serviço que a mensagem foi enviada ao.</span><span class="sxs-lookup"><span data-stu-id="5adad-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="5adad-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="5adad-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="5adad-132">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="5adad-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="5adad-133">O formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="5adad-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="5adad-134">Exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="5adad-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="5adad-135">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5adad-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5adad-136">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5adad-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|