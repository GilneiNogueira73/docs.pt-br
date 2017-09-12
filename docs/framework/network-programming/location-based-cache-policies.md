---
title: "Políticas de cache baseadas na localização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Cache If Available policy
- reload policy
- location-based cache policies
- Cache Only policy
- local cache
- intermediate cache
- No Cache No Store policy
- cache [.NET Framework], location-based policies
- Revalidate policy
- freshness of cached resources
- Cache Or Next Cache Only policy
- Refresh policy
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
caps.latest.revision: 12
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a5b4bf67db3fcbb70d2a93f35976d8d9b4b3a028
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="location-based-cache-policies"></a><span data-ttu-id="d2fad-102">Políticas de cache baseadas na localização</span><span class="sxs-lookup"><span data-stu-id="d2fad-102">Location-Based Cache Policies</span></span>
<span data-ttu-id="d2fad-103">Uma política de cache baseada na localização define a atualização das entradas armazenadas em cache válidas de acordo com o local em que o recurso solicitado pode ser obtido.</span><span class="sxs-lookup"><span data-stu-id="d2fad-103">A location-based cache policy defines the freshness of valid cached entries based on where the requested resource can be taken from.</span></span> <span data-ttu-id="d2fad-104">Um recurso em cache é válido se usá-lo não viola os requisitos de revalidação especificados pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="d2fad-104">A cached resource is valid if using it does not does not violate server-specified revalidation requirements.</span></span> <span data-ttu-id="d2fad-105">Uma política de cache baseada na localização é criada programaticamente usando um construtor de classe <xref:System.Net.Cache.RequestCachePolicy> ou <xref:System.Net.Cache.HttpRequestCachePolicy>.</span><span class="sxs-lookup"><span data-stu-id="d2fad-105">A location-based cache policy is created programmatically by using a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> class constructor.</span></span> <span data-ttu-id="d2fad-106">O tipo de política baseada na localização é passado para o construtor usando um valor de enumeração <xref:System.Net.Cache.RequestCacheLevel> ou <xref:System.Net.Cache.HttpRequestCacheLevel>.</span><span class="sxs-lookup"><span data-stu-id="d2fad-106">The type of location-based policy is passed to the constructor using a <xref:System.Net.Cache.RequestCacheLevel> or <xref:System.Net.Cache.HttpRequestCacheLevel> enumeration value.</span></span> <span data-ttu-id="d2fad-107">Para obter exemplos de código que criam políticas de cache baseadas na localização, consulte [Como definir uma política de cache baseada na localização para um aplicativo](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="d2fad-107">For code examples that create location-based cache policies, see [How to: Set a Location-Based Cache Policy for an Application](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="d2fad-108">As seções a seguir explicam cada tipo de política de cache baseada na localização para recursos de protocolo HTTP (http e https).</span><span class="sxs-lookup"><span data-stu-id="d2fad-108">The following sections explain each type of location-based cache policy for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
## <a name="cache-if-available-policy"></a><span data-ttu-id="d2fad-109">Política de armazenar em cache se disponível</span><span class="sxs-lookup"><span data-stu-id="d2fad-109">Cache If Available Policy</span></span>  
 <span data-ttu-id="d2fad-110">Se um recurso solicitado válido estiver no cache local, o recurso armazenado em cache será usado; caso contrário, a solicitação para o recurso será enviada ao servidor.</span><span class="sxs-lookup"><span data-stu-id="d2fad-110">If a valid requested resource is in the local cache, the cached resource is used; otherwise, the request for the resource is sent to the server.</span></span> <span data-ttu-id="d2fad-111">Se o recurso solicitado estiver disponível em qualquer cache entre o cliente e o servidor, a solicitação poderá ser atendida por um cache intermediário.</span><span class="sxs-lookup"><span data-stu-id="d2fad-111">If the requested resource is available in any cache between the client and the server, the request can be satisfied by an intermediate cache.</span></span>  
  
## <a name="cache-only-policy"></a><span data-ttu-id="d2fad-112">Política de somente cache</span><span class="sxs-lookup"><span data-stu-id="d2fad-112">Cache Only Policy</span></span>  
 <span data-ttu-id="d2fad-113">Se um recurso solicitado válido estiver no cache local, o recurso armazenado em cache será usado.</span><span class="sxs-lookup"><span data-stu-id="d2fad-113">If a valid requested resource is in the local cache, the cached resource is used.</span></span> <span data-ttu-id="d2fad-114">Ao se especificar esse nível de política de cache, uma exceção <xref:System.Net.WebException> será lançada se o item não estiver no cache local.</span><span class="sxs-lookup"><span data-stu-id="d2fad-114">When this cache policy level is specified, a <xref:System.Net.WebException> exception is thrown if the item is not in the local cache.</span></span>  
  
## <a name="cache-or-next-cache-only-policy"></a><span data-ttu-id="d2fad-115">Política de somente cache ou próximo cache</span><span class="sxs-lookup"><span data-stu-id="d2fad-115">Cache Or Next Cache Only Policy</span></span>  
 <span data-ttu-id="d2fad-116">Se um recurso solicitado válido está no cache local ou em um cache intermediário na rede local, o recurso armazenado em cache é usado.</span><span class="sxs-lookup"><span data-stu-id="d2fad-116">If a valid requested resource is in the local cache or an intermediate cache on the local area network, the cached resource is used.</span></span> <span data-ttu-id="d2fad-117">Se não, uma exceção é lançada de <xref:System.Net.WebException> .</span><span class="sxs-lookup"><span data-stu-id="d2fad-117">Otherwise, a <xref:System.Net.WebException> exception is thrown.</span></span> <span data-ttu-id="d2fad-118">No protocolo de cache HTTP, isso é feito usando a diretiva de controle de cache somente se armazenado em cache.</span><span class="sxs-lookup"><span data-stu-id="d2fad-118">In the HTTP caching protocol, this is achieved using the only-if-cached cache control directive.</span></span>  
  
## <a name="no-cache-no-store-policy"></a><span data-ttu-id="d2fad-119">Política sem cache, sem repositório</span><span class="sxs-lookup"><span data-stu-id="d2fad-119">No Cache No Store Policy</span></span>  
 <span data-ttu-id="d2fad-120">Um recurso solicitado nunca é usado de nenhum cache e nunca é colocado em nenhum cache.</span><span class="sxs-lookup"><span data-stu-id="d2fad-120">A requested resource is never used from any cache and is never placed in any cache.</span></span> <span data-ttu-id="d2fad-121">Se um recurso solicitado estiver presente no cache local, ele será removido.</span><span class="sxs-lookup"><span data-stu-id="d2fad-121">If a requested resource is present in the local cache, it is removed.</span></span> <span data-ttu-id="d2fad-122">Esse nível de política indica aos caches intermediários que eles também devem remover o recurso.</span><span class="sxs-lookup"><span data-stu-id="d2fad-122">This policy level indicates to intermediate caches that they should also remove the resource.</span></span> <span data-ttu-id="d2fad-123">No protocolo de cache HTTP, isso é feito usando a diretiva de controle de cache sem repositório.</span><span class="sxs-lookup"><span data-stu-id="d2fad-123">In the HTTP caching protocol, this is achieved using the no-store cache control directive.</span></span>  
  
## <a name="refresh-policy"></a><span data-ttu-id="d2fad-124">Política de atualizar</span><span class="sxs-lookup"><span data-stu-id="d2fad-124">Refresh Policy</span></span>  
 <span data-ttu-id="d2fad-125">Um recurso solicitado pode ser usado se for obtido do servidor ou localizado em um cache que não seja o cache local.</span><span class="sxs-lookup"><span data-stu-id="d2fad-125">A requested resource can be used if it is obtained from the server or found in a cache other than the local cache.</span></span> <span data-ttu-id="d2fad-126">Antes de a solicitação poder ser atendida por um cache intermediário, esse cache deve revalidar sua entrada armazenada em cache com o servidor.</span><span class="sxs-lookup"><span data-stu-id="d2fad-126">Before the request can be satisfied by an intermediate cache, that cache must revalidate its cached entry with the server.</span></span> <span data-ttu-id="d2fad-127">No protocolo de cache HTTP, isso é feito usando a diretiva de controle de cache max-age = 0 no cabeçalho Pragma sem cache.</span><span class="sxs-lookup"><span data-stu-id="d2fad-127">In the HTTP caching protocol, this is achieved using the max-age = 0 cache control directive and the no-cache Pragma header.</span></span>  
  
## <a name="reload-policy"></a><span data-ttu-id="d2fad-128">Política de recarregar</span><span class="sxs-lookup"><span data-stu-id="d2fad-128">Reload Policy</span></span>  
 <span data-ttu-id="d2fad-129">Os recursos solicitados devem ser obtidos do servidor.</span><span class="sxs-lookup"><span data-stu-id="d2fad-129">Requested resources must be obtained from the server.</span></span> <span data-ttu-id="d2fad-130">A resposta pode ser salva no cache local.</span><span class="sxs-lookup"><span data-stu-id="d2fad-130">The response might be saved in the local cache.</span></span> <span data-ttu-id="d2fad-131">No protocolo de cache HTTP, isso é feito usando a diretiva de controle de cache sem cache e o cabeçalho Pragma sem cache.</span><span class="sxs-lookup"><span data-stu-id="d2fad-131">In the HTTP caching protocol, this is achieved using the no-cache cache control directive and the no-cache Pragma header.</span></span>  
  
## <a name="revalidate-policy"></a><span data-ttu-id="d2fad-132">Política de revalidar</span><span class="sxs-lookup"><span data-stu-id="d2fad-132">Revalidate Policy</span></span>  
 <span data-ttu-id="d2fad-133">Compara a cópia do recurso no cache com a cópia no servidor.</span><span class="sxs-lookup"><span data-stu-id="d2fad-133">Compares the copy of the resource in the cache with the copy on the server.</span></span> <span data-ttu-id="d2fad-134">Se a cópia no servidor for mais recente, ela será usada para atender à solicitação e substituirá a cópia em cache.</span><span class="sxs-lookup"><span data-stu-id="d2fad-134">If the copy on the server is newer, it is used to satisfy the request and replaces the copy in the cache.</span></span> <span data-ttu-id="d2fad-135">Se a cópia em cache for igual à cópia do servidor, a cópia armazenada em cache será usada.</span><span class="sxs-lookup"><span data-stu-id="d2fad-135">If the copy in the cache is the same as the server copy, the cached copy is used.</span></span> <span data-ttu-id="d2fad-136">No protocolo de cache HTTP, isso é feito usando uma solicitação condicional.</span><span class="sxs-lookup"><span data-stu-id="d2fad-136">In the HTTP caching protocol, this is achieved using a conditional request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2fad-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2fad-137">See Also</span></span>  
 <span data-ttu-id="d2fad-138">[Gerenciamento de cache para aplicativos de rede](../../../docs/framework/network-programming/cache-management-for-network-applications.md) </span><span class="sxs-lookup"><span data-stu-id="d2fad-138">[Cache Management for Network Applications](../../../docs/framework/network-programming/cache-management-for-network-applications.md) </span></span>  
 <span data-ttu-id="d2fad-139">[Política de cache](../../../docs/framework/network-programming/cache-policy.md) </span><span class="sxs-lookup"><span data-stu-id="d2fad-139">[Cache Policy](../../../docs/framework/network-programming/cache-policy.md) </span></span>  
 <span data-ttu-id="d2fad-140">[Políticas de cache baseadas em tempo](../../../docs/framework/network-programming/time-based-cache-policies.md) </span><span class="sxs-lookup"><span data-stu-id="d2fad-140">[Time-Based Cache Policies](../../../docs/framework/network-programming/time-based-cache-policies.md) </span></span>  
 <span data-ttu-id="d2fad-141">[Configurando o cache em aplicativos de rede](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md) </span><span class="sxs-lookup"><span data-stu-id="d2fad-141">[Configuring Caching in Network Applications](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md) </span></span>  
 [<span data-ttu-id="d2fad-142">\<Elemento requestCaching> (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="d2fad-142">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
