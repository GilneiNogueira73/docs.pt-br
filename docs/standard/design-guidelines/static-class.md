---
title: "Design de classe estática"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 28fe3756a2881e8f746616f8275b505b1a01eada
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="static-class-design"></a><span data-ttu-id="b138b-102">Design de classe estática</span><span class="sxs-lookup"><span data-stu-id="b138b-102">Static Class Design</span></span>
<span data-ttu-id="b138b-103">Uma classe estática é definida como uma classe que contém somente os membros estáticos (obviamente além os membros de instância herdados de <xref:System.Object?displayProperty=nameWithType> e possivelmente um construtor particular).</span><span class="sxs-lookup"><span data-stu-id="b138b-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="b138b-104">Alguns idiomas dão suporte interno para classes estáticas.</span><span class="sxs-lookup"><span data-stu-id="b138b-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="b138b-105">No c# 2.0 e posterior, quando uma classe é declarada como estático, é lacrado, abstrata e nenhum membro de instância pode ser substituído ou declarado.</span><span class="sxs-lookup"><span data-stu-id="b138b-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>  
  
 <span data-ttu-id="b138b-106">Classes static são um meio-termo entre design simples e orientada a objeto e simplicidade.</span><span class="sxs-lookup"><span data-stu-id="b138b-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="b138b-107">Eles são usados para fornecer atalhos para outras operações (como <xref:System.IO.File?displayProperty=nameWithType>), os proprietários de métodos de extensão ou a funcionalidade para a qual um wrapper completo orientada a objeto é injustificado (como <xref:System.Environment?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="b138b-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="b138b-108">**FAZER ✓** usam classes estáticas com moderação.</span><span class="sxs-lookup"><span data-stu-id="b138b-108">**✓ DO** use static classes sparingly.</span></span>  
  
 <span data-ttu-id="b138b-109">Classes static devem ser usados apenas como classes de suporte para o núcleo orientada a objeto do framework.</span><span class="sxs-lookup"><span data-stu-id="b138b-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>  
  
 <span data-ttu-id="b138b-110">**X não** tratar classes estáticas como um bucket diverso.</span><span class="sxs-lookup"><span data-stu-id="b138b-110">**X DO NOT** treat static classes as a miscellaneous bucket.</span></span>  
  
 <span data-ttu-id="b138b-111">**X não** declarar ou substituir membros de instância em classes estáticas.</span><span class="sxs-lookup"><span data-stu-id="b138b-111">**X DO NOT** declare or override instance members in static classes.</span></span>  
  
 <span data-ttu-id="b138b-112">**FAZER ✓** declarar classes estáticas como lacrado, abstract e adicione um construtor de instância privada se a linguagem de programação não tem suporte interno para classes estáticas.</span><span class="sxs-lookup"><span data-stu-id="b138b-112">**✓ DO** declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>  
  
 <span data-ttu-id="b138b-113">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="b138b-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b138b-114">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="b138b-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b138b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b138b-115">See Also</span></span>  
 [<span data-ttu-id="b138b-116">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="b138b-116">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="b138b-117">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="b138b-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)