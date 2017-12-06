---
title: '&lt;adicionar&gt; &lt;protocolMapping&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 255cd8518bd9c6c6c199c75aa32ca086c801d23f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltprotocolmappinggt"></a><span data-ttu-id="0b94a-102">&lt;adicionar&gt; &lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="0b94a-102">&lt;add&gt; of &lt;protocolMapping&gt;</span></span>
<span data-ttu-id="0b94a-103">Representa um mapeamento de protocolo padrão entre um esquema de protocolo de transporte (por exemplo, http, net.tcp, NET. pipe, etc.) e um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] associação.</span><span class="sxs-lookup"><span data-stu-id="0b94a-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] binding.</span></span> <span data-ttu-id="0b94a-104">Durante a criação de pontos de extremidade padrão em tempo de execução, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] examina os mapeamentos configurados e decide em qual associação a ser usado para um determinado com base em endereço.</span><span class="sxs-lookup"><span data-stu-id="0b94a-104">When creating default endpoints at runtime, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="0b94a-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0b94a-105">\<system.serviceModel></span></span>  
<span data-ttu-id="0b94a-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="0b94a-106">\<protocolMapping></span></span>  
<span data-ttu-id="0b94a-107">\<add></span><span class="sxs-lookup"><span data-stu-id="0b94a-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b94a-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b94a-108">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0b94a-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0b94a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0b94a-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0b94a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b94a-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="0b94a-111">Attributes</span></span>  
  
|<span data-ttu-id="0b94a-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="0b94a-112">Element</span></span>|<span data-ttu-id="0b94a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b94a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b94a-114">associação</span><span class="sxs-lookup"><span data-stu-id="0b94a-114">binding</span></span>|<span data-ttu-id="0b94a-115">Uma cadeia de caracteres que especifica o tipo de associação a ser usado para um ponto de extremidade durante a criação do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="0b94a-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="0b94a-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="0b94a-116">bindingConfiguration</span></span>|<span data-ttu-id="0b94a-117">Uma cadeia de caracteres que especifica o nome da seção de configuração de associação a ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="0b94a-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="0b94a-118">esquema</span><span class="sxs-lookup"><span data-stu-id="0b94a-118">scheme</span></span>|<span data-ttu-id="0b94a-119">O esquema de protocolo de transporte a ser usado para o ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="0b94a-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b94a-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0b94a-120">Child Elements</span></span>  
 <span data-ttu-id="0b94a-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0b94a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b94a-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0b94a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="0b94a-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="0b94a-123">Element</span></span>|<span data-ttu-id="0b94a-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b94a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b94a-125">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="0b94a-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="0b94a-126">Representa uma seção de configuração para definir mapeamentos de protocolo padrão entre esquemas de protocolo de transporte (por exemplo, http, net.tcp, NET. pipe, etc.) e [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] associações.</span><span class="sxs-lookup"><span data-stu-id="0b94a-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0b94a-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0b94a-127">Example</span></span>  
 <span data-ttu-id="0b94a-128">O exemplo de configuração a seguir mostra o mapeamento de padrão de protocolo no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="0b94a-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="0b94a-129">Você pode substituir esse mapeamento padrão no nível do computador, modificando o arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="0b94a-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="0b94a-130">Ou, se você apenas deseja substituí-la dentro do escopo de um aplicativo, você pode substituir esta seção dentro de seu arquivo de configuração do aplicativo e alterar o mapeamento para esquemas de protocolo individual.</span><span class="sxs-lookup"><span data-stu-id="0b94a-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b94a-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b94a-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    