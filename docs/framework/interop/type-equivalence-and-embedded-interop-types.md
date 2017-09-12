---
title: "Equivalência de tipos e tipos de interoperabilidade inseridos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
caps.latest.revision: 17
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e9a7b39047edcd8e2c770e17a33dd73e75ee5083
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="type-equivalence-and-embedded-interop-types"></a><span data-ttu-id="b2593-102">Equivalência de tipos e tipos de interoperabilidade inseridos</span><span class="sxs-lookup"><span data-stu-id="b2593-102">Type Equivalence and Embedded Interop Types</span></span>
<span data-ttu-id="b2593-103">A partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o Common Language Runtime dá suporte à inserção de informações de tipo para tipos COM diretamente em assemblies gerenciados, em vez de exigir que os assemblies gerenciados obtenham informações de tipo para tipos COM de assemblies de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="b2593-103">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the common language runtime supports embedding type information for COM types directly into managed assemblies, instead of requiring the managed assemblies to obtain type information for COM types from interop assemblies.</span></span> <span data-ttu-id="b2593-104">Como as informações de tipo inserido incluem somente os tipos e os membros que são realmente usados por um assembly gerenciado, dois assemblies gerenciados podem ter exibições muito diferentes do mesmo tipo COM.</span><span class="sxs-lookup"><span data-stu-id="b2593-104">Because the embedded type information includes only the types and members that are actually used by a managed assembly, two managed assemblies might have very different views of the same COM type.</span></span> <span data-ttu-id="b2593-105">Cada assembly gerenciado tem um objeto <xref:System.Type> diferente para representar sua exibição do tipo COM.</span><span class="sxs-lookup"><span data-stu-id="b2593-105">Each managed assembly has a different <xref:System.Type> object to represent its view of the COM type.</span></span> <span data-ttu-id="b2593-106">O Common Language Runtime dá suporte à equivalência de tipo entre essas exibições diferentes para interfaces, estruturas, enumerações e representantes.</span><span class="sxs-lookup"><span data-stu-id="b2593-106">The common language runtime supports type equivalence between these different views for interfaces, structures, enumerations, and delegates.</span></span>  
  
 <span data-ttu-id="b2593-107">Equivalência de tipo significa que um objeto COM que é passado de um assembly gerenciado para outro pode ser convertido no tipo gerenciado apropriado no assembly receptor.</span><span class="sxs-lookup"><span data-stu-id="b2593-107">Type equivalence means that a COM object that is passed from one managed assembly to another can be cast to the appropriate managed type in the receiving assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2593-108">Equivalência de tipo e tipos de interoperabilidade inseridos simplificam a implantação de aplicativos e suplementos que usam componentes COM, porque não é necessário implantar assemblies de interoperabilidade com os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b2593-108">Type equivalence and embedded interop types simplify the deployment of applications and add-ins that use COM components, because it is not necessary to deploy interop assemblies with the applications.</span></span> <span data-ttu-id="b2593-109">Os desenvolvedores de componentes COM compartilhados ainda precisam criar PIAs (assemblies de interoperabilidade primários) se desejam que seus componentes sejam usados por versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2593-109">Developers of shared COM components still have to create primary interop assemblies (PIAs) if they want their components to be used by earlier versions of the .NET Framework.</span></span>  
  
## <a name="type-equivalence"></a><span data-ttu-id="b2593-110">Equivalência de tipo</span><span class="sxs-lookup"><span data-stu-id="b2593-110">Type Equivalence</span></span>  
 <span data-ttu-id="b2593-111">Há suporte à equivalência de tipos COM em interfaces, estruturas, enumerações e representantes.</span><span class="sxs-lookup"><span data-stu-id="b2593-111">Equivalence of COM types is supported for interfaces, structures, enumerations, and delegates.</span></span> <span data-ttu-id="b2593-112">Os tipos COM se qualificarão como equivalentes se todas as seguintes afirmações forem verdadeiras:</span><span class="sxs-lookup"><span data-stu-id="b2593-112">COM types qualify as equivalent if all of the following are true:</span></span>  
  
-   <span data-ttu-id="b2593-113">Os tipos são ambas interfaces, ambas estruturas, ambas enumerações ou ambas representantes.</span><span class="sxs-lookup"><span data-stu-id="b2593-113">The types are both interfaces, or both structures, or both enumerations, or both delegates.</span></span>  
  
-   <span data-ttu-id="b2593-114">Os tipos têm a mesma identidade, conforme descrito na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="b2593-114">The types have the same identity, as described in the next section.</span></span>  
  
-   <span data-ttu-id="b2593-115">Ambos os tipos são qualificados para a equivalência de tipo, conforme descrito na seção [Marcando tipos COM para a equivalência de tipo](#type_equiv).</span><span class="sxs-lookup"><span data-stu-id="b2593-115">Both types are eligible for type equivalence, as described in the [Marking COM Types for Type Equivalence](#type_equiv) section.</span></span>  
  
### <a name="type-identity"></a><span data-ttu-id="b2593-116">Identidade de tipo</span><span class="sxs-lookup"><span data-stu-id="b2593-116">Type Identity</span></span>  
 <span data-ttu-id="b2593-117">Dois tipos são determinados como tendo a mesma identidade quando seus escopos e identidades correspondem. Em outras palavras, se cada um tem o atributo <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> e os dois atributos têm propriedades <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> e <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> correspondentes.</span><span class="sxs-lookup"><span data-stu-id="b2593-117">Two types are determined to have the same identity when their scopes and identities match, in other words, if they each have the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute, and the two attributes have matching <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> and <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> properties.</span></span> <span data-ttu-id="b2593-118">A comparação de <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> não diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="b2593-118">The comparison for <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> is case-insensitive.</span></span>  
  
 <span data-ttu-id="b2593-119">Se um tipo não tiver o atributo <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> ou se ele tiver um atributo <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> que não especifica o escopo e o identificador, o tipo ainda poderá ser considerado para equivalência da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b2593-119">If a type does not have the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute, or if it has a <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute that does not specify scope and identifier, the type can still be considered for equivalence as follows:</span></span>  
  
-   <span data-ttu-id="b2593-120">Para interfaces, o valor do <xref:System.Runtime.InteropServices.GuidAttribute> é usado em vez da propriedade <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=fullName> e a propriedade <xref:System.Type.FullName%2A?displayProperty=fullName> (ou seja, o nome do tipo, incluindo o namespace) é usado em vez da propriedade <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="b2593-120">For interfaces, the value of the <xref:System.Runtime.InteropServices.GuidAttribute> is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=fullName> property, and the <xref:System.Type.FullName%2A?displayProperty=fullName> property (that is, the type name, including the namespace) is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=fullName> property.</span></span>  
  
-   <span data-ttu-id="b2593-121">Para estruturas, enumerações e representantes, o <xref:System.Runtime.InteropServices.GuidAttribute> do assembly de contenção é usado em vez da propriedade <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> e a propriedade <xref:System.Type.FullName%2A?displayProperty=fullName> é usada em vez da propriedade <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2593-121">For structures, enumerations, and delegates, the <xref:System.Runtime.InteropServices.GuidAttribute> of the containing assembly is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> property, and the <xref:System.Type.FullName%2A?displayProperty=fullName> property is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> property.</span></span>  
  
<a name="type_equiv"></a>   
### <a name="marking-com-types-for-type-equivalence"></a><span data-ttu-id="b2593-122">Marcando tipos COM para a equivalência de tipo</span><span class="sxs-lookup"><span data-stu-id="b2593-122">Marking COM Types for Type Equivalence</span></span>  
 <span data-ttu-id="b2593-123">É possível marcar um tipo como qualificado para a equivalência de tipo de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="b2593-123">You can mark a type as eligible for type equivalence in two ways:</span></span>  
  
-   <span data-ttu-id="b2593-124">Aplicar o atributo <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> ao tipo.</span><span class="sxs-lookup"><span data-stu-id="b2593-124">Apply the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute to the type.</span></span>  
  
-   <span data-ttu-id="b2593-125">Tornar o tipo um tipo de importação COM.</span><span class="sxs-lookup"><span data-stu-id="b2593-125">Make the type a COM import type.</span></span> <span data-ttu-id="b2593-126">Uma interface é um tipo de importação COM se ela tem o atributo <xref:System.Runtime.InteropServices.ComImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b2593-126">An interface is a COM import type if it has the <xref:System.Runtime.InteropServices.ComImportAttribute> attribute.</span></span> <span data-ttu-id="b2593-127">Uma interface, uma estrutura, uma enumeração ou um representante é um tipo de importação COM se o assembly no qual ele é definido tem o atributo <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b2593-127">An interface, structure, enumeration, or delegate is a COM import type if the assembly in which it is defined has the <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2593-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2593-128">See Also</span></span>  
 <span data-ttu-id="b2593-129"><xref:System.Type.IsEquivalentTo%2A></span><span class="sxs-lookup"><span data-stu-id="b2593-129"><xref:System.Type.IsEquivalentTo%2A></span></span>   
 <span data-ttu-id="b2593-130">[Usando tipos COM em código gerenciado](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66) </span><span class="sxs-lookup"><span data-stu-id="b2593-130">[Using COM Types in Managed Code](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66) </span></span>  
 [<span data-ttu-id="b2593-131">Importando uma biblioteca de tipos como um assembly</span><span class="sxs-lookup"><span data-stu-id="b2593-131">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
