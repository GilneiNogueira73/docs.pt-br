---
title: '&lt;userPrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 616eb07a76da93ff1019ea7e80b5ce3151e6e8a4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="72df8-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="72df8-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="72df8-103">Especifica o usuário nome Principal (UPN) de um serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="72df8-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="72df8-104">Para obter mais informações sobre como configurar o UPN, consulte [autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="72df8-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="72df8-105">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="72df8-105">\<identity></span></span>  
<span data-ttu-id="72df8-106">\<userPrincipalName ></span><span class="sxs-lookup"><span data-stu-id="72df8-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72df8-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72df8-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72df8-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="72df8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="72df8-109">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="72df8-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72df8-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="72df8-110">Attributes</span></span>  
  
|<span data-ttu-id="72df8-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="72df8-111">Attribute</span></span>|<span data-ttu-id="72df8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="72df8-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="72df8-113">Valor </span><span class="sxs-lookup"><span data-stu-id="72df8-113">value</span></span>|<span data-ttu-id="72df8-114">Um nome de conta de usuário (também conhecido como o nome de logon do usuário) e um nome de domínio identificando o domínio no qual a conta de usuário está localizada.</span><span class="sxs-lookup"><span data-stu-id="72df8-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="72df8-115">Este é o uso padrão para fazer logon em um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="72df8-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="72df8-116">O formato é: someone@example.com (como um endereço de email).</span><span class="sxs-lookup"><span data-stu-id="72df8-116">The format is: someone@example.com (as for an e-mail address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72df8-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="72df8-117">Child Elements</span></span>  
 <span data-ttu-id="72df8-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="72df8-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72df8-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="72df8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="72df8-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="72df8-120">Element</span></span>|<span data-ttu-id="72df8-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="72df8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72df8-122">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="72df8-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="72df8-123">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="72df8-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72df8-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="72df8-124">Remarks</span></span>  
 <span data-ttu-id="72df8-125">Seguro [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] cliente que se conecta a um ponto de extremidade com esta identidade usa o UPN ao executar a autenticação de SSPI com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="72df8-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72df8-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72df8-126">Example</span></span>  
 <span data-ttu-id="72df8-127">O código de configuração a seguir especifica o UPN do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="72df8-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="72df8-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72df8-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="72df8-129">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="72df8-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="72df8-130">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="72df8-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)