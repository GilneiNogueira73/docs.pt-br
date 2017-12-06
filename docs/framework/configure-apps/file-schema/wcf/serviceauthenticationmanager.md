---
title: '&lt;serviceAuthenticationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 077878ae1746008532c3bee6b12913f98afc343f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="baf69-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="baf69-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="baf69-103">Fornece um elemento de configuração de fluxo de trabalho que estabelece o nível de serviço a validade de uma transmissão, a mensagem ou o originador.</span><span class="sxs-lookup"><span data-stu-id="baf69-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="baf69-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="baf69-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="baf69-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="baf69-105">\<behaviors></span></span>  
<span data-ttu-id="baf69-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="baf69-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="baf69-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="baf69-107">\<behavior></span></span>  
<span data-ttu-id="baf69-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="baf69-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baf69-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="baf69-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="baf69-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="baf69-110">Attributes and Elements</span></span>  
 <span data-ttu-id="baf69-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="baf69-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="baf69-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="baf69-112">Attributes</span></span>  
  
|<span data-ttu-id="baf69-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="baf69-113">Attribute</span></span>|<span data-ttu-id="baf69-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="baf69-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="baf69-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="baf69-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="baf69-116">Uma cadeia de caracteres que especifica o tipo de política de autenticação para o comportamento atual.</span><span class="sxs-lookup"><span data-stu-id="baf69-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="baf69-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="baf69-117">Child Elements</span></span>  
 <span data-ttu-id="baf69-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="baf69-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="baf69-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="baf69-119">Parent Elements</span></span>  
  
|<span data-ttu-id="baf69-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="baf69-120">Element</span></span>|<span data-ttu-id="baf69-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="baf69-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="baf69-122">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="baf69-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="baf69-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="baf69-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="baf69-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="baf69-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>