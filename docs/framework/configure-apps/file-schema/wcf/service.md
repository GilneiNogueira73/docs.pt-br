---
title: "&lt;serviço&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 61c8d8451e271e756fce6f83a4f8b8fd4c8b9f77
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicegt"></a><span data-ttu-id="ca43f-102">&lt;serviço&gt;</span><span class="sxs-lookup"><span data-stu-id="ca43f-102">&lt;service&gt;</span></span>
<span data-ttu-id="ca43f-103">O `service` elemento contém as configurações para um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ca43f-103">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="ca43f-104">Ele também contém pontos de extremidade que expõem o serviço.</span><span class="sxs-lookup"><span data-stu-id="ca43f-104">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="ca43f-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ca43f-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ca43f-106">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="ca43f-106">\<services></span></span>  
<span data-ttu-id="ca43f-107">\<serviço ></span><span class="sxs-lookup"><span data-stu-id="ca43f-107">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca43f-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca43f-108">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration=String"  
        name="String"  
</service>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca43f-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ca43f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ca43f-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ca43f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca43f-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="ca43f-111">Attributes</span></span>  
  
|<span data-ttu-id="ca43f-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="ca43f-112">Attribute</span></span>|<span data-ttu-id="ca43f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca43f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ca43f-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="ca43f-114">behaviorConfiguration</span></span>|<span data-ttu-id="ca43f-115">Uma cadeia de caracteres que contém o nome do comportamento do comportamento a ser usado para instanciar o serviço.</span><span class="sxs-lookup"><span data-stu-id="ca43f-115">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="ca43f-116">O nome do comportamento deve estar no escopo no ponto em que o serviço está definido.</span><span class="sxs-lookup"><span data-stu-id="ca43f-116">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="ca43f-117">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="ca43f-117">The default value is an empty string.</span></span>|  
|<span data-ttu-id="ca43f-118">name</span><span class="sxs-lookup"><span data-stu-id="ca43f-118">name</span></span>|<span data-ttu-id="ca43f-119">Necessário um atributo de cadeia de caracteres que especifica o tipo de serviço a ser instanciado.</span><span class="sxs-lookup"><span data-stu-id="ca43f-119">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="ca43f-120">Essa configuração deve serão iguais a um tipo válido.</span><span class="sxs-lookup"><span data-stu-id="ca43f-120">This setting must equate to a valid type.</span></span> <span data-ttu-id="ca43f-121">O formato deve ser`Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="ca43f-121">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca43f-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ca43f-122">Child Elements</span></span>  
  
|<span data-ttu-id="ca43f-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="ca43f-123">Element</span></span>|<span data-ttu-id="ca43f-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca43f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca43f-125">\<ponto de extremidade ></span><span class="sxs-lookup"><span data-stu-id="ca43f-125">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|<span data-ttu-id="ca43f-126">Uma coleção de `endpoint` elementos que expõem este serviço.</span><span class="sxs-lookup"><span data-stu-id="ca43f-126">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="ca43f-127">\<host ></span><span class="sxs-lookup"><span data-stu-id="ca43f-127">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="ca43f-128">Especifica o host desta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="ca43f-128">Specifies the host of this service instance.</span></span> <span data-ttu-id="ca43f-129">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="ca43f-129">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca43f-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ca43f-130">Parent Elements</span></span>  
  
|<span data-ttu-id="ca43f-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="ca43f-131">Element</span></span>|<span data-ttu-id="ca43f-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca43f-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca43f-133">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="ca43f-133">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="ca43f-134">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="ca43f-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca43f-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca43f-135">Remarks</span></span>  
 <span data-ttu-id="ca43f-136">Os serviços são definidos no `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ca43f-136">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="ca43f-137">Um assembly pode conter qualquer número de serviços.</span><span class="sxs-lookup"><span data-stu-id="ca43f-137">An assembly can contain any number of services.</span></span> <span data-ttu-id="ca43f-138">Cada serviço tem seu próprio `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="ca43f-138">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="ca43f-139">Esta seção e seu conteúdo definem o contrato de serviço, o comportamento e os pontos de extremidade do serviço em questão.</span><span class="sxs-lookup"><span data-stu-id="ca43f-139">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="ca43f-140">O `behaviorConfiguration` elemento também é opcional.</span><span class="sxs-lookup"><span data-stu-id="ca43f-140">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="ca43f-141">Ele identifica o comportamento de serviço usa.</span><span class="sxs-lookup"><span data-stu-id="ca43f-141">It identifies the behavior the service uses.</span></span> <span data-ttu-id="ca43f-142">O comportamento especificado neste atributo deve vincular a um comportamento no escopo no mesmo arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ca43f-142">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="ca43f-143">Cada serviço expõe um ou mais pontos de extremidade, que tem seu próprio endereço e associação.</span><span class="sxs-lookup"><span data-stu-id="ca43f-143">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="ca43f-144">Todas as associações usadas no arquivo de configuração devem ser definidas no escopo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="ca43f-144">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="ca43f-145">Associação são vinculados aos pontos de extremidade pela combinação dos atributos `name` e `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="ca43f-145">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="ca43f-146">O `name` atributo descreve a seção a associação é definida no.</span><span class="sxs-lookup"><span data-stu-id="ca43f-146">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="ca43f-147">O `bindingConfiguration` atributo define qual configuração dentro da seção de associação é usada.</span><span class="sxs-lookup"><span data-stu-id="ca43f-147">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="ca43f-148">Uma seção de associação pode definir várias configurações.</span><span class="sxs-lookup"><span data-stu-id="ca43f-148">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca43f-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca43f-149">Example</span></span>  
 <span data-ttu-id="ca43f-150">Este é um exemplo de uma configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="ca43f-150">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"   
     name="HelloWorld">  
     <endpoint   
        address="/HelloWorld2/"  
        name="test"  
        bindingNamespace="http://www.cohowinery.com/"  
        binding="basicHttpBinding"  
        contract="IHelloWorld" />  
</service>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca43f-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca43f-151">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceElement>  
 <span data-ttu-id="ca43f-152">[Configuring Services](../../../../../docs/framework/wcf/configuring-services.md) (Configurando serviços)</span><span class="sxs-lookup"><span data-stu-id="ca43f-152">[Configuring Services](../../../../../docs/framework/wcf/configuring-services.md)</span></span>