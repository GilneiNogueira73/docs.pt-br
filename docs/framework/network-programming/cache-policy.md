---
title: "Política de cache"
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
- time-based cache policies
- location-based cache policies
- cache [.NET Framework], policies
- request cache policies
- freshness of cached resources
- content cache policies
- expired content
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
caps.latest.revision: 11
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7323c93ef89e340595f6b62947ea45867e651425
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="cache-policy"></a><span data-ttu-id="16630-102">Política de cache</span><span class="sxs-lookup"><span data-stu-id="16630-102">Cache Policy</span></span>
<span data-ttu-id="16630-103">Uma política de cache define as regras que são usadas para determinar se uma solicitação pode ser atendida usando uma cópia armazenada em cache do recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="16630-103">A cache policy defines rules that are used to determine whether a request can be satisfied using a cached copy of the requested resource.</span></span> <span data-ttu-id="16630-104">Os aplicativos especificam requisitos de cache de cliente para atualização, mas a política de cache efetiva é determinada pelos requisitos de cache de cliente, requisitos de expiração de conteúdo do servidor e requisitos de revalidação do servidor.</span><span class="sxs-lookup"><span data-stu-id="16630-104">Applications specify client cache requirements for freshness, but the effective cache policy is determined by the client cache requirements, the server's content expiration requirements, and the server's revalidation requirements.</span></span> <span data-ttu-id="16630-105">A interação dos requisitos da política de cache de cliente e do servidor sempre resulta na política de cache mais conservadora, para ajudar a garantir que o conteúdo mais atualizado é retornado para o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="16630-105">The interaction of client cache policy and server requirements always results in the most conservative cache policy, to help ensure that the freshest content is returned to the client application.</span></span>  
  
 <span data-ttu-id="16630-106">As políticas de cache são baseadas na localização ou em tempo.</span><span class="sxs-lookup"><span data-stu-id="16630-106">Cache policies are either location-based or time-based.</span></span> <span data-ttu-id="16630-107">Uma política de cache baseada na localização define a atualização das entradas armazenadas em cache de acordo com o local em que o recurso solicitado pode ser obtido.</span><span class="sxs-lookup"><span data-stu-id="16630-107">A location-based cache policy defines the freshness of cached entries based on where the requested resource can be taken from.</span></span> <span data-ttu-id="16630-108">Uma política de cache baseada em tempo define a atualização das entradas armazenadas em cache usando a hora em que o recurso foi recuperado, os cabeçalhos retornados com o recurso e a hora atual.</span><span class="sxs-lookup"><span data-stu-id="16630-108">A time-based cache policy defines the freshness of cached entries using the time the resource was retrieved, headers returned with the resource, and the current time.</span></span> <span data-ttu-id="16630-109">A maioria dos aplicativos pode usar a política de cache baseada em tempo padrão, que implementa a política de cache especificada no RFC 2616, disponível em [http://www.ietf.org](http://www.ietf.org/).</span><span class="sxs-lookup"><span data-stu-id="16630-109">Most applications can use the default time-based cache policy, which implements the caching policy specified in RFC 2616, available at [http://www.ietf.org](http://www.ietf.org/).</span></span>  
  
 <span data-ttu-id="16630-110">As classes descritas na tabela a seguir são usadas para especificar políticas de cache.</span><span class="sxs-lookup"><span data-stu-id="16630-110">The classes described in the following table are used to specify cache policies.</span></span>  
  
|<span data-ttu-id="16630-111">Nome da classe</span><span class="sxs-lookup"><span data-stu-id="16630-111">Class name</span></span>|<span data-ttu-id="16630-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="16630-112">Description</span></span>|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|<span data-ttu-id="16630-113">Representa as políticas de cache baseadas na localização e em tempo para recursos solicitados usando objetos <xref:System.Net.HttpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="16630-113">Represents location-based and time-based cache policies for resources requested using <xref:System.Net.HttpWebRequest> objects.</span></span>|  
|<xref:System.Net.Cache.RequestCachePolicy>|<span data-ttu-id="16630-114">Representa as políticas de cache baseadas na localização ou a política de cache baseada em tempo <xref:System.Net.Cache.RequestCacheLevel.Default> para recursos solicitados usando objetos <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="16630-114">Represents location-based cache policies or the <xref:System.Net.Cache.RequestCacheLevel.Default> time-based cache policy for resources requested using <xref:System.Net.WebRequest> objects.</span></span>|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|<span data-ttu-id="16630-115">Especifica os valores usados para criar objetos <xref:System.Net.Cache.HttpRequestCachePolicy> baseados em tempo.</span><span class="sxs-lookup"><span data-stu-id="16630-115">Specifies values used to create time-based <xref:System.Net.Cache.HttpRequestCachePolicy> objects.</span></span>|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|<span data-ttu-id="16630-116">Especifica os valores usados para criar objetos <xref:System.Net.Cache.HttpRequestCachePolicy> baseados na localização e em tempo.</span><span class="sxs-lookup"><span data-stu-id="16630-116">Specifies values used to create location-based and time-based <xref:System.Net.Cache.HttpRequestCachePolicy> objects.</span></span>|  
|<xref:System.Net.Cache.RequestCacheLevel>|<span data-ttu-id="16630-117">Especifica os valores usados para criar objetos <xref:System.Net.Cache.RequestCachePolicy> baseados na localização e em tempo <xref:System.Net.Cache.RequestCacheLevel.Default>.</span><span class="sxs-lookup"><span data-stu-id="16630-117">Specifies values used to create location-based or the <xref:System.Net.Cache.RequestCacheLevel.Default> time-based <xref:System.Net.Cache.RequestCachePolicy> objects.</span></span>|  
  
 <span data-ttu-id="16630-118">Defina uma política de cache para todas as solicitações feitas pelo aplicativo ou para solicitações individuais.</span><span class="sxs-lookup"><span data-stu-id="16630-118">You can define a cache policy for all requests made by your application or for individual requests.</span></span> <span data-ttu-id="16630-119">Ao especificar uma política de cache no nível do aplicativo e uma política de cache no nível da solicitação, a política no nível da solicitação é usada.</span><span class="sxs-lookup"><span data-stu-id="16630-119">When you specify both an application-level cache policy and a request-level cache policy, the request-level policy is used.</span></span> <span data-ttu-id="16630-120">Especifique uma política de cache no nível do aplicativo de forma programática ou usando os arquivos de configuração do aplicativo ou do computador.</span><span class="sxs-lookup"><span data-stu-id="16630-120">You can specify an application-level cache policy programmatically or by using the application or machine configuration files.</span></span> <span data-ttu-id="16630-121">Para obter mais informações, consulte Elemento [\<requestCaching> (configurações de rede)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="16630-121">For more information, see [\<requestCaching> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
 <span data-ttu-id="16630-122">Para criar uma política de cache, você deve criar um objeto de política criando uma instância da classe <xref:System.Net.Cache.RequestCachePolicy> ou <xref:System.Net.Cache.HttpRequestCachePolicy>.</span><span class="sxs-lookup"><span data-stu-id="16630-122">To create a cache policy, you must create a policy object by creating an instance of the <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> class.</span></span> <span data-ttu-id="16630-123">Para especificar a política em uma solicitação, defina a propriedade <xref:System.Net.WebRequest.CachePolicy%2A> da solicitação com o objeto de política.</span><span class="sxs-lookup"><span data-stu-id="16630-123">To specify the policy on a request, set the request's <xref:System.Net.WebRequest.CachePolicy%2A> property to the policy object.</span></span> <span data-ttu-id="16630-124">Ao definir uma política no nível do aplicativo de forma programática, defina a propriedade <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> com o objeto de política.</span><span class="sxs-lookup"><span data-stu-id="16630-124">When setting an application-level policy programmatically, set the <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> property to the policy object.</span></span>  
  
 <span data-ttu-id="16630-125">Para obter exemplos de código que demonstram como criar e usar políticas de cache, consulte [Configurando o cache em aplicativos de rede](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).</span><span class="sxs-lookup"><span data-stu-id="16630-125">For code examples that demonstrate creating and using cache policies, see [Configuring Caching in Network Applications](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16630-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16630-126">See Also</span></span>  
 <span data-ttu-id="16630-127">[Gerenciamento de cache para aplicativos de rede](../../../docs/framework/network-programming/cache-management-for-network-applications.md) </span><span class="sxs-lookup"><span data-stu-id="16630-127">[Cache Management for Network Applications](../../../docs/framework/network-programming/cache-management-for-network-applications.md) </span></span>  
 <span data-ttu-id="16630-128">[Políticas de cache baseadas na localização](../../../docs/framework/network-programming/location-based-cache-policies.md) </span><span class="sxs-lookup"><span data-stu-id="16630-128">[Location-Based Cache Policies](../../../docs/framework/network-programming/location-based-cache-policies.md) </span></span>  
 <span data-ttu-id="16630-129">[Políticas de cache baseadas em tempo](../../../docs/framework/network-programming/time-based-cache-policies.md) </span><span class="sxs-lookup"><span data-stu-id="16630-129">[Time-Based Cache Policies](../../../docs/framework/network-programming/time-based-cache-policies.md) </span></span>  
 [<span data-ttu-id="16630-130">Configurando o cache em aplicativos de rede</span><span class="sxs-lookup"><span data-stu-id="16630-130">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
