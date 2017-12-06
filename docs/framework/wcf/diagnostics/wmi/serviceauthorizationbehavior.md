---
title: ServiceAuthorizationBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd22cd7e7783a67e7ad10371533eee680bd3af16
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="a9fc4-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="a9fc4-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="a9fc4-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="a9fc4-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9fc4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9fc4-104">Syntax</span></span>  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a9fc4-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a9fc4-105">Methods</span></span>  
 <span data-ttu-id="a9fc4-106">A classe ServiceAuthorizationBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="a9fc4-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a9fc4-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a9fc4-107">Properties</span></span>  
 <span data-ttu-id="a9fc4-108">A classe ServiceAuthorizationBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="a9fc4-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="a9fc4-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="a9fc4-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="a9fc4-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="a9fc4-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="a9fc4-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a9fc4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a9fc4-112">Um valor que controla se o serviço tenta representar usando as credenciais fornecidas pela mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="a9fc4-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="a9fc4-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="a9fc4-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="a9fc4-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a9fc4-114">Data type: string</span></span>  
  
 <span data-ttu-id="a9fc4-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a9fc4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a9fc4-116">O principal usado para realizar operações no servidor.</span><span class="sxs-lookup"><span data-stu-id="a9fc4-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="a9fc4-117">Propriedade RoleProvider</span><span class="sxs-lookup"><span data-stu-id="a9fc4-117">RoleProvider</span></span>  
 <span data-ttu-id="a9fc4-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a9fc4-118">Data type: string</span></span>  
  
 <span data-ttu-id="a9fc4-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a9fc4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a9fc4-120">O nome do provedor de função ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a9fc4-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="a9fc4-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="a9fc4-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="a9fc4-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a9fc4-122">Data type: string</span></span>  
  
 <span data-ttu-id="a9fc4-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a9fc4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a9fc4-124">O Gerenciador de autorização usado para autorização personalizada.</span><span class="sxs-lookup"><span data-stu-id="a9fc4-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9fc4-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9fc4-125">Requirements</span></span>  
  
|<span data-ttu-id="a9fc4-126">MOF</span><span class="sxs-lookup"><span data-stu-id="a9fc4-126">MOF</span></span>|<span data-ttu-id="a9fc4-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a9fc4-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a9fc4-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="a9fc4-128">Namespace</span></span>|<span data-ttu-id="a9fc4-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a9fc4-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a9fc4-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9fc4-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>