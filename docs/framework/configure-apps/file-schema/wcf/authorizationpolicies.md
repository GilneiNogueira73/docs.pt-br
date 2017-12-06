---
title: '&lt;authorizationPolicies&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 94bbf10ad093c6b99d586f9aaacb7faffc097cee
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltauthorizationpoliciesgt"></a><span data-ttu-id="68d97-102">&lt;authorizationPolicies&gt;</span><span class="sxs-lookup"><span data-stu-id="68d97-102">&lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="68d97-103">Esta seção de configuração contém uma coleção de tipos de política de autorização, que pode ser adicionado usando o `add` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="68d97-103">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="68d97-104">Cada política de autorização contém um único necessário `policyType` atributo que é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="68d97-104">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="68d97-105">O atributo especifica uma política de autorização, que permite que a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="68d97-105">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="68d97-106">Controle de acesso pode ser concedido ou negado com base no que.</span><span class="sxs-lookup"><span data-stu-id="68d97-106">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="68d97-107">Para obter mais informações sobre como funciona a uma política de autorização, consulte <xref:System.IdentityModel.Policy.IAuthorizationPolicy> e [política de autorização](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-107">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68d97-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68d97-108">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="68d97-109">Autorizando o acesso a operações de serviço</span><span class="sxs-lookup"><span data-stu-id="68d97-109">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="68d97-110">Como: criar um Gerenciador de autorização personalizada para um serviço</span><span class="sxs-lookup"><span data-stu-id="68d97-110">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="68d97-111">\<add></span><span class="sxs-lookup"><span data-stu-id="68d97-111">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="68d97-112">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="68d97-112">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)