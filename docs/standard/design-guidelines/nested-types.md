---
title: Tipos aninhados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ae09df49b97cc2fe84285c3a37e1562da185f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="nested-types"></a><span data-ttu-id="617cd-102">Tipos aninhados</span><span class="sxs-lookup"><span data-stu-id="617cd-102">Nested Types</span></span>
<span data-ttu-id="617cd-103">Um tipo aninhado é um tipo definido dentro do escopo de outro tipo, que é chamado o tipo de delimitador.</span><span class="sxs-lookup"><span data-stu-id="617cd-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="617cd-104">Um tipo aninhado tem acesso a todos os membros do seu tipo delimitador.</span><span class="sxs-lookup"><span data-stu-id="617cd-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="617cd-105">Por exemplo, ele tem acesso a campos particulares definidos no tipo de delimitador e protegido campos definidos em todos os ascendentes do tipo delimitador.</span><span class="sxs-lookup"><span data-stu-id="617cd-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>  
  
 <span data-ttu-id="617cd-106">Em geral, os tipos aninhados devem ser usados com moderação.</span><span class="sxs-lookup"><span data-stu-id="617cd-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="617cd-107">Há vários motivos para isso.</span><span class="sxs-lookup"><span data-stu-id="617cd-107">There are several reasons for this.</span></span> <span data-ttu-id="617cd-108">Alguns desenvolvedores não são totalmente familiarizados com o conceito.</span><span class="sxs-lookup"><span data-stu-id="617cd-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="617cd-109">Esses desenvolvedores podem, por exemplo, ter problemas com a sintaxe de declaração de variáveis de tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="617cd-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="617cd-110">Tipos aninhados são também muito acoplados com seus tipos de delimitadores e como tal, não são adequados para tipos de uso geral.</span><span class="sxs-lookup"><span data-stu-id="617cd-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>  
  
 <span data-ttu-id="617cd-111">Tipos aninhados são mais adequados para modelar os detalhes de implementação dos seus tipos de delimitadores.</span><span class="sxs-lookup"><span data-stu-id="617cd-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="617cd-112">O usuário final deve ter raramente para declarar variáveis de um tipo aninhado e quase nunca deve ter que instanciar explicitamente os tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="617cd-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="617cd-113">Por exemplo, o enumerador de uma coleção pode ser um tipo aninhado de coleção.</span><span class="sxs-lookup"><span data-stu-id="617cd-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="617cd-114">Enumeradores são instanciados geralmente por seu tipo delimitador e como muitos idiomas oferecem suporte a instrução foreach, variáveis de enumerador raramente têm de ser declarada pelo usuário final.</span><span class="sxs-lookup"><span data-stu-id="617cd-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>  
  
 <span data-ttu-id="617cd-115">**FAZER ✓** usar tipos aninhados quando a relação entre o tipo aninhado e seu tipo externo é tal que a semântica de acessibilidade de membros é desejável.</span><span class="sxs-lookup"><span data-stu-id="617cd-115">**✓ DO** use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>  
  
 <span data-ttu-id="617cd-116">**X não** tipos aninhados públicos em uso como um agrupamento lógico construir; use namespaces para isso.</span><span class="sxs-lookup"><span data-stu-id="617cd-116">**X DO NOT** use public nested types as a logical grouping construct; use namespaces for this.</span></span>  
  
 <span data-ttu-id="617cd-117">**X Evite** exposto publicamente tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="617cd-117">**X AVOID** publicly exposed nested types.</span></span> <span data-ttu-id="617cd-118">A única exceção a isso é se as variáveis do tipo aninhado precisam ser declarado apenas em cenários raros, como subclasses ou outros cenários de personalização avançada.</span><span class="sxs-lookup"><span data-stu-id="617cd-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>  
  
 <span data-ttu-id="617cd-119">**X não** usar tipos aninhados, se o tipo é provavelmente serão mencionados fora do tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="617cd-119">**X DO NOT** use nested types if the type is likely to be referenced outside of the containing type.</span></span>  
  
 <span data-ttu-id="617cd-120">Por exemplo, um enum passado para um método definido em uma classe não deve ser definido como um tipo aninhado na classe.</span><span class="sxs-lookup"><span data-stu-id="617cd-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>  
  
 <span data-ttu-id="617cd-121">**X não** usar tipos aninhados se eles precisam ser instanciado pelo código do cliente.</span><span class="sxs-lookup"><span data-stu-id="617cd-121">**X DO NOT** use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="617cd-122">Se um tipo tem um construtor público, ele provavelmente não deve ser aninhado.</span><span class="sxs-lookup"><span data-stu-id="617cd-122">If a type has a public constructor, it should probably not be nested.</span></span>  
  
 <span data-ttu-id="617cd-123">Se um tipo pode ser instanciado, parece que indicam o tipo tem um lugar no framework em seu próprio (você pode criá-lo, trabalhar com ele e destruí-lo sem nunca usando o tipo externo) e, portanto, não devem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="617cd-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="617cd-124">Tipos internos não devem ser reutilizados amplamente fora do tipo externo sem qualquer relação qualquer que seja o tipo externo.</span><span class="sxs-lookup"><span data-stu-id="617cd-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>  
  
 <span data-ttu-id="617cd-125">**X não** definir um tipo aninhado como um membro de uma interface.</span><span class="sxs-lookup"><span data-stu-id="617cd-125">**X DO NOT** define a nested type as a member of an interface.</span></span> <span data-ttu-id="617cd-126">Muitos idiomas não dão suporte a esse uma construção.</span><span class="sxs-lookup"><span data-stu-id="617cd-126">Many languages do not support such a construct.</span></span>  
  
 <span data-ttu-id="617cd-127">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="617cd-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="617cd-128">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="617cd-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="617cd-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="617cd-129">See Also</span></span>  
 [<span data-ttu-id="617cd-130">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="617cd-130">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="617cd-131">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="617cd-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)