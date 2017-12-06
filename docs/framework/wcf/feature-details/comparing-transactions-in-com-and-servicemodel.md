---
title: "Comparando transações em COM+ e ServiceModel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5229c872c4843df916cf538b7f2e88e451dc6b9d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a><span data-ttu-id="f5899-102">Comparando transações em COM+ e ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f5899-102">Comparing Transactions in COM+ and ServiceModel</span></span>
<span data-ttu-id="f5899-103">Este tópico discute como simular o comportamento de uma transação COM+ serviço usando o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] atributos o <xref:System.ServiceModel> namespace fornece.</span><span class="sxs-lookup"><span data-stu-id="f5899-103">This topic discusses how to simulate the behavior of a transactional COM+ service using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
## <a name="emulating-com-using-servicemodel-attributes"></a><span data-ttu-id="f5899-104">Emulando COM+ usando atributos de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f5899-104">Emulating COM+ Using ServiceModel Attributes</span></span>  
 <span data-ttu-id="f5899-105">A tabela a seguir compara o <xref:System.EnterpriseServices.TransactionOption> enumeração usada para criar um `EnterpriseServices` transações e como eles se correlacionam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] atributos o <xref:System.ServiceModel> namespace fornece.</span><span class="sxs-lookup"><span data-stu-id="f5899-105">The following table compares the <xref:System.EnterpriseServices.TransactionOption> enumeration used to create an `EnterpriseServices` transaction and how they correlate to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
|<span data-ttu-id="f5899-106">Atributo de COM+</span><span class="sxs-lookup"><span data-stu-id="f5899-106">COM+ attribute</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f5899-107">atributos</span><span class="sxs-lookup"><span data-stu-id="f5899-107"> attributes</span></span>|  
|---------------------|------------------------------------------------------------------------|  
|<span data-ttu-id="f5899-108">RequiresNew</span><span class="sxs-lookup"><span data-stu-id="f5899-108">RequiresNew</span></span>|<span data-ttu-id="f5899-109"><xref:System.ServiceModel.TransactionFlowAttribute> é definido como <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span><span class="sxs-lookup"><span data-stu-id="f5899-109"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span></span><br /><br /> <span data-ttu-id="f5899-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> é `true`.</span><span class="sxs-lookup"><span data-stu-id="f5899-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="f5899-111">O `TransactionFlow` atributo no elemento de associação é `false`.</span><span class="sxs-lookup"><span data-stu-id="f5899-111">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="f5899-112">Necessária</span><span class="sxs-lookup"><span data-stu-id="f5899-112">Required</span></span>|<span data-ttu-id="f5899-113"><xref:System.ServiceModel.TransactionFlowAttribute> é definido como <xref:System.ServiceModel.TransactionFlowOption.Allowed>.</span><span class="sxs-lookup"><span data-stu-id="f5899-113"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.Allowed>.</span></span><br /><br /> <span data-ttu-id="f5899-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> é `true`.</span><span class="sxs-lookup"><span data-stu-id="f5899-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="f5899-115">O `TransactionFlow` atributo no elemento de associação é `true`.</span><span class="sxs-lookup"><span data-stu-id="f5899-115">The `TransactionFlow` attribute in the binding element is `true`.</span></span>|  
|<span data-ttu-id="f5899-116">Com suporte</span><span class="sxs-lookup"><span data-stu-id="f5899-116">Supported</span></span>|<span data-ttu-id="f5899-117">Não há nenhum equivalente direto.</span><span class="sxs-lookup"><span data-stu-id="f5899-117">There is no direct equivalent.</span></span> <span data-ttu-id="f5899-118">Em geral, você deve adotar o comportamento especificado para `Required` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f5899-118">In general, you should adopt the behavior specified for `Required` instead.</span></span>|  
|<span data-ttu-id="f5899-119">Não suportado</span><span class="sxs-lookup"><span data-stu-id="f5899-119">NotSupported</span></span>|<span data-ttu-id="f5899-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> é `false`.</span><span class="sxs-lookup"><span data-stu-id="f5899-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `false`.</span></span><br /><br /> <span data-ttu-id="f5899-121">O `TransactionFlow` atributo no elemento de associação é `false`.</span><span class="sxs-lookup"><span data-stu-id="f5899-121">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="f5899-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="f5899-122">Disabled</span></span>|<span data-ttu-id="f5899-123">Não há nenhum equivalente direto.</span><span class="sxs-lookup"><span data-stu-id="f5899-123">There is no direct equivalent.</span></span> <span data-ttu-id="f5899-124">Em geral, você deve adotar o comportamento especificado para `NotSupported` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f5899-124">In general, you should adopt the behavior specified for `NotSupported` instead.</span></span>|