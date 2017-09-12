---
title: Elemento &lt;Subtypes&gt; (.NET Nativo)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e945c4c6a6b56422fc1aa228bc7a5f388406f16d
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="ltsubtypesgt-element-net-native"></a><span data-ttu-id="a6638-102">Elemento &lt;Subtypes&gt; (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="a6638-102">&lt;Subtypes&gt; Element (.NET Native)</span></span>
<span data-ttu-id="a6638-103">Aplica a política de tempo de execução a todas as classes herdadas do tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="a6638-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6638-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6638-104">Syntax</span></span>  
  
```xml  
<Subtypes Activate="policy_type"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type"   
          DataContractSerializer="policy_setting"  
          DataContractJsonSerializer="policy_setting"  
          XmlSerializer="policy_setting"  
          MarshalObject="policy_setting"  
          MarshalDelegate="policy_setting"  
          MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6638-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a6638-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a6638-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a6638-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6638-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a6638-107">Attributes</span></span>  
  
|<span data-ttu-id="a6638-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="a6638-108">Attribute</span></span>|<span data-ttu-id="a6638-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="a6638-109">Attribute type</span></span>|<span data-ttu-id="a6638-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6638-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="a6638-111">Reflexão</span><span class="sxs-lookup"><span data-stu-id="a6638-111">Reflection</span></span>|<span data-ttu-id="a6638-112">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a6638-112">Optional attribute.</span></span> <span data-ttu-id="a6638-113">Controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="a6638-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="a6638-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="a6638-114">Reflection</span></span>|<span data-ttu-id="a6638-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a6638-115">Optional attribute.</span></span> <span data-ttu-id="a6638-116">Controla a consulta para obter informações sobre elementos do programa, mas não permite qualquer acesso de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a6638-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="a6638-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="a6638-117">Reflection</span></span>|<span data-ttu-id="a6638-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a6638-118">Optional attribute.</span></span> <span data-ttu-id="a6638-119">Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="a6638-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="a6638-120">Serialização</span><span class="sxs-lookup"><span data-stu-id="a6638-120">Serialization</span></span>|<span data-ttu-id="a6638-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a6638-121">Optional attribute.</span></span> <span data-ttu-id="a6638-122">Controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="a6638-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="a6638-123">Serialização</span><span class="sxs-lookup"><span data-stu-id="a6638-123">Serialization</span></span>|<span data-ttu-id="a6638-124">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a6638-124">Optional attribute.</span></span> <span data-ttu-id="a6638-125">Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="a6638-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="a6638-126">Serialização</span><span class="sxs-lookup"><span data-stu-id="a6638-126">Serialization</span></span>|<span data-ttu-id="a6638-127">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a6638-127">Optional attribute.</span></span> <span data-ttu-id="a6638-128">Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="a6638-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="a6638-129">Serialização</span><span class="sxs-lookup"><span data-stu-id="a6638-129">Serialization</span></span>|<span data-ttu-id="a6638-130">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a6638-130">Optional attribute.</span></span> <span data-ttu-id="a6638-131">Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="a6638-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="a6638-132">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="a6638-132">Interop</span></span>|<span data-ttu-id="a6638-133">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a6638-133">Optional attribute.</span></span> <span data-ttu-id="a6638-134">Política de controles de marshaling de tipos de referência para o Tempo de Execução do Windows e COM.</span><span class="sxs-lookup"><span data-stu-id="a6638-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="a6638-135">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="a6638-135">Interop</span></span>|<span data-ttu-id="a6638-136">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a6638-136">Optional attribute.</span></span> <span data-ttu-id="a6638-137">Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.</span><span class="sxs-lookup"><span data-stu-id="a6638-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="a6638-138">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="a6638-138">Interop</span></span>|<span data-ttu-id="a6638-139">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a6638-139">Optional attribute.</span></span> <span data-ttu-id="a6638-140">Controla a política de marshaling de tipos de valor para código nativo.</span><span class="sxs-lookup"><span data-stu-id="a6638-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="a6638-141">Todos os atributos</span><span class="sxs-lookup"><span data-stu-id="a6638-141">All attributes</span></span>  
  
|<span data-ttu-id="a6638-142">Valor</span><span class="sxs-lookup"><span data-stu-id="a6638-142">Value</span></span>|<span data-ttu-id="a6638-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6638-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a6638-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="a6638-144">*policy_setting*</span></span>|<span data-ttu-id="a6638-145">A configuração a ser aplicada a este tipo de política.</span><span class="sxs-lookup"><span data-stu-id="a6638-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="a6638-146">Os valores possíveis são `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`.</span><span class="sxs-lookup"><span data-stu-id="a6638-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="a6638-147">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a6638-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6638-148">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a6638-148">Child Elements</span></span>  
 <span data-ttu-id="a6638-149">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a6638-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6638-150">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a6638-150">Parent Elements</span></span>  
  
|<span data-ttu-id="a6638-151">Elemento</span><span class="sxs-lookup"><span data-stu-id="a6638-151">Element</span></span>|<span data-ttu-id="a6638-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6638-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6638-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="a6638-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="a6638-154">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="a6638-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6638-155">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6638-155">Remarks</span></span>  
 <span data-ttu-id="a6638-156">O elemento `<Subtypes>` aplica a política a todos os subtipos de seu tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="a6638-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="a6638-157">Use-o quando desejar aplicar políticas diferentes a tipos derivados e suas classes base.</span><span class="sxs-lookup"><span data-stu-id="a6638-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="a6638-158">Os atributos de reflexão, serialização e interoperabilidade são todos opcionais, embora pelo menos um deve estar presente.</span><span class="sxs-lookup"><span data-stu-id="a6638-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6638-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a6638-159">Example</span></span>  
 <span data-ttu-id="a6638-160">O exemplo a seguir define uma classe chamada `BaseClass` e uma subclasse denominada `Derived1`.</span><span class="sxs-lookup"><span data-stu-id="a6638-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 <span data-ttu-id="a6638-161">[!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]</span><span class="sxs-lookup"><span data-stu-id="a6638-161">[!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]</span></span>  
  
 <span data-ttu-id="a6638-162">Conforme mostrado no código a seguir, o arquivo de diretivas de tempo de execução define explicitamente o `Dynamic` e `Activate` políticas para `BaseClass` para `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="a6638-162">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="a6638-163">Devido a isso, objetos do tipo `BaseClass` não pode ser instanciada dinamicamente ou por chamadas para o construtor da classe `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="a6638-163">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="a6638-164">No entanto, o elemento `<Subtypes>` permite que classes derivadas de `BaseClass` sejam instanciadas dinamicamente e por meio de chamadas para seus construtores de classe.</span><span class="sxs-lookup"><span data-stu-id="a6638-164">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 <span data-ttu-id="a6638-165">Devido à diretiva `<Subtypes>`, o seguinte código instancia uma instância `Derived1` dinamicamente chamando o método <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=fullName>, que é executado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a6638-165">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=fullName> method executes successfully.</span></span>  <span data-ttu-id="a6638-166">A variável de bloco aqui é um objeto <xref:System.Windows.Controls.TextBlock> em um aplicativo da Windows Store em branco.</span><span class="sxs-lookup"><span data-stu-id="a6638-166">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 <span data-ttu-id="a6638-167">[!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]</span><span class="sxs-lookup"><span data-stu-id="a6638-167">[!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6638-168">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6638-168">See Also</span></span>  
 <span data-ttu-id="a6638-169">[\<Elemento Type>](../../../docs/framework/net-native/type-element-net-native.md) </span><span class="sxs-lookup"><span data-stu-id="a6638-169">[\<Type> Element](../../../docs/framework/net-native/type-element-net-native.md) </span></span>  
 <span data-ttu-id="a6638-170">[Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a6638-170">[Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) </span></span>  
 <span data-ttu-id="a6638-171">[Elementos da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-elements.md) </span><span class="sxs-lookup"><span data-stu-id="a6638-171">[Runtime Directive Elements](../../../docs/framework/net-native/runtime-directive-elements.md) </span></span>  
 [<span data-ttu-id="a6638-172">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a6638-172">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
