---
title: Elemento &lt;ImpliesType&gt; (.NET Nativo)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a4f131be8991b7e907c15aeaec888c418423f461
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="ltimpliestypegt-element-net-native"></a><span data-ttu-id="ce58f-102">Elemento &lt;ImpliesType&gt; (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="ce58f-102">&lt;ImpliesType&gt; Element (.NET Native)</span></span>
<span data-ttu-id="ce58f-103">Aplica a política a um tipo, se ela foi aplicada ao tipo recipiente ou do método.</span><span class="sxs-lookup"><span data-stu-id="ce58f-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce58f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce58f-104">Syntax</span></span>  
  
```vb  
<ImpliesType Name="type_name"  
             Activate="policy_type"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce58f-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ce58f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ce58f-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ce58f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce58f-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="ce58f-107">Attributes</span></span>  
  
|<span data-ttu-id="ce58f-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="ce58f-108">Attribute</span></span>|<span data-ttu-id="ce58f-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="ce58f-109">Attribute type</span></span>|<span data-ttu-id="ce58f-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce58f-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="ce58f-111">Geral</span><span class="sxs-lookup"><span data-stu-id="ce58f-111">General</span></span>|<span data-ttu-id="ce58f-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="ce58f-112">Required attribute.</span></span> <span data-ttu-id="ce58f-113">Especifica o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="ce58f-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="ce58f-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="ce58f-114">Reflection</span></span>|<span data-ttu-id="ce58f-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ce58f-115">Optional attribute.</span></span> <span data-ttu-id="ce58f-116">Controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="ce58f-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="ce58f-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="ce58f-117">Reflection</span></span>|<span data-ttu-id="ce58f-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ce58f-118">Optional attribute.</span></span> <span data-ttu-id="ce58f-119">Controla a consulta para obter informações sobre elementos do programa, mas não permite qualquer acesso de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ce58f-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="ce58f-120">Reflexão</span><span class="sxs-lookup"><span data-stu-id="ce58f-120">Reflection</span></span>|<span data-ttu-id="ce58f-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ce58f-121">Optional attribute.</span></span> <span data-ttu-id="ce58f-122">Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="ce58f-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="ce58f-123">Serialização</span><span class="sxs-lookup"><span data-stu-id="ce58f-123">Serialization</span></span>|<span data-ttu-id="ce58f-124">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ce58f-124">Optional attribute.</span></span> <span data-ttu-id="ce58f-125">Controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="ce58f-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="ce58f-126">Serialização</span><span class="sxs-lookup"><span data-stu-id="ce58f-126">Serialization</span></span>|<span data-ttu-id="ce58f-127">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ce58f-127">Optional attribute.</span></span> <span data-ttu-id="ce58f-128">Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ce58f-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="ce58f-129">Serialização</span><span class="sxs-lookup"><span data-stu-id="ce58f-129">Serialization</span></span>|<span data-ttu-id="ce58f-130">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ce58f-130">Optional attribute.</span></span> <span data-ttu-id="ce58f-131">Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ce58f-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="ce58f-132">Serialização</span><span class="sxs-lookup"><span data-stu-id="ce58f-132">Serialization</span></span>|<span data-ttu-id="ce58f-133">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ce58f-133">Optional attribute.</span></span> <span data-ttu-id="ce58f-134">Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ce58f-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="ce58f-135">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="ce58f-135">Interop</span></span>|<span data-ttu-id="ce58f-136">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ce58f-136">Optional attribute.</span></span> <span data-ttu-id="ce58f-137">Política de controles de marshaling de tipos de referência para o Tempo de Execução do Windows e COM.</span><span class="sxs-lookup"><span data-stu-id="ce58f-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="ce58f-138">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="ce58f-138">Interop</span></span>|<span data-ttu-id="ce58f-139">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ce58f-139">Optional attribute.</span></span> <span data-ttu-id="ce58f-140">Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.</span><span class="sxs-lookup"><span data-stu-id="ce58f-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="ce58f-141">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="ce58f-141">Interop</span></span>|<span data-ttu-id="ce58f-142">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ce58f-142">Optional attribute.</span></span> <span data-ttu-id="ce58f-143">Controla a política de marshaling de tipos de valor para código nativo.</span><span class="sxs-lookup"><span data-stu-id="ce58f-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="ce58f-144">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="ce58f-144">Name attribute</span></span>  
  
|<span data-ttu-id="ce58f-145">Valor</span><span class="sxs-lookup"><span data-stu-id="ce58f-145">Value</span></span>|<span data-ttu-id="ce58f-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce58f-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ce58f-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="ce58f-147">*type_name*</span></span>|<span data-ttu-id="ce58f-148">O nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="ce58f-148">The type name.</span></span> <span data-ttu-id="ce58f-149">Se o tipo representado por este elemento `<ImpliesType>` estiver localizado no mesmo namespace contendo seu elemento `<Type>`, o *type_name* poderá incluir o nome do tipo sem o respectivo namespace.</span><span class="sxs-lookup"><span data-stu-id="ce58f-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="ce58f-150">Caso contrário, o *type_name* deverá incluir o nome do tipo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="ce58f-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="ce58f-151">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="ce58f-151">All other attributes</span></span>  
  
|<span data-ttu-id="ce58f-152">Valor</span><span class="sxs-lookup"><span data-stu-id="ce58f-152">Value</span></span>|<span data-ttu-id="ce58f-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce58f-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ce58f-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="ce58f-154">*policy_setting*</span></span>|<span data-ttu-id="ce58f-155">A configuração a ser aplicada a este tipo de política.</span><span class="sxs-lookup"><span data-stu-id="ce58f-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="ce58f-156">Os valores possíveis são `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`.</span><span class="sxs-lookup"><span data-stu-id="ce58f-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="ce58f-157">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="ce58f-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce58f-158">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ce58f-158">Child Elements</span></span>  
 <span data-ttu-id="ce58f-159">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ce58f-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce58f-160">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ce58f-160">Parent Elements</span></span>  
  
|<span data-ttu-id="ce58f-161">Elemento</span><span class="sxs-lookup"><span data-stu-id="ce58f-161">Element</span></span>|<span data-ttu-id="ce58f-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce58f-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce58f-163">\<Type></span><span class="sxs-lookup"><span data-stu-id="ce58f-163">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="ce58f-164">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="ce58f-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="ce58f-165">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="ce58f-165">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="ce58f-166">Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="ce58f-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="ce58f-167">\<Method></span><span class="sxs-lookup"><span data-stu-id="ce58f-167">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="ce58f-168">Aplica a política de reflexão a um método.</span><span class="sxs-lookup"><span data-stu-id="ce58f-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce58f-169">Comentários</span><span class="sxs-lookup"><span data-stu-id="ce58f-169">Remarks</span></span>  
 <span data-ttu-id="ce58f-170">O elemento `<ImpliesType>` destina-se principalmente para uso por bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="ce58f-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="ce58f-171">Ele aborda o cenário a seguir:</span><span class="sxs-lookup"><span data-stu-id="ce58f-171">It addresses the following scenario:</span></span>  
  
-   <span data-ttu-id="ce58f-172">Se uma rotina precisa refletir em um tipo, ela necessariamente precisa refletir no segundo tipo.</span><span class="sxs-lookup"><span data-stu-id="ce58f-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
-   <span data-ttu-id="ce58f-173">Os metadados para a instanciação implícita do segundo tipo não estão disponíveis, pois a análise estática não indica que é necessário.</span><span class="sxs-lookup"><span data-stu-id="ce58f-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="ce58f-174">Geralmente, os dois tipos são instanciações genéricas com argumentos de tipo compartilhados.</span><span class="sxs-lookup"><span data-stu-id="ce58f-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="ce58f-175">O elemento `<ImpliesType>` foi definido presumindo que a necessidade de reflexão no tipo especificado pelo seu elemento pai implica a necessidade de reflexão no tipo especificado pelo elemento `<ImpliesType>`.</span><span class="sxs-lookup"><span data-stu-id="ce58f-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="ce58f-176">Por exemplo, as seguintes diretivas de reflexão aplicam-se a dois tipos, `Explicit<T>` e `Implicit<T>`.</span><span class="sxs-lookup"><span data-stu-id="ce58f-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="ce58f-177">Essa diretiva não tem efeito, a menos que uma instanciação de `Explicit` tenha uma configuração de política `Dynamic` definida.</span><span class="sxs-lookup"><span data-stu-id="ce58f-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="ce58f-178">Por exemplo, se for o caso de `Explicit<Int32>`, `Implicit<Int32>` é instanciado com seu membros públicos enraizados e seus metadados são disponibilizados por programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="ce58f-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="ce58f-179">Veja a seguir um exemplo real que se aplica a pelo menos um serializador.</span><span class="sxs-lookup"><span data-stu-id="ce58f-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="ce58f-180">As diretivas capturam o requisito de que a reflexão sobre algo digitado como `IList<`*algo*`>` também envolve reflexão sobre o tipo `List<`*algo*`>` correspondente sem exigir nenhuma anotação por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce58f-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="ce58f-181">O elemento `<ImpliesType>` também pode aparecer em um elemento `<Method>`, pois em alguns casos instanciar um método genérico implica refletir em uma instanciação de um tipo.</span><span class="sxs-lookup"><span data-stu-id="ce58f-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="ce58f-182">Por exemplo, imagine um método genérico `IEnumerable<T> MakeEnumerable<T>(string` `spelling``, T` `defaultValue``)` que uma determinada biblioteca acessará dinamicamente juntamente com os tipos <xref:System.Collections.Generic.List%601> e <xref:System.Array> associados.</span><span class="sxs-lookup"><span data-stu-id="ce58f-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string` `spelling``, T` `defaultValue``)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="ce58f-183">Isso pode ser expressado como:</span><span class="sxs-lookup"><span data-stu-id="ce58f-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce58f-184">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce58f-184">See Also</span></span>  
 <span data-ttu-id="ce58f-185">[Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ce58f-185">[Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) </span></span>  
 <span data-ttu-id="ce58f-186">[Elementos da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-elements.md) </span><span class="sxs-lookup"><span data-stu-id="ce58f-186">[Runtime Directive Elements](../../../docs/framework/net-native/runtime-directive-elements.md) </span></span>  
 [<span data-ttu-id="ce58f-187">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="ce58f-187">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
