---
title: "Como registrar assemblies de interoperabilidade primários"
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
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 81b57a73b8c5118af9cf2867902b849d73820e83
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-register-primary-interop-assemblies"></a><span data-ttu-id="07643-102">Como registrar assemblies de interoperabilidade primários</span><span class="sxs-lookup"><span data-stu-id="07643-102">How to: Register Primary Interop Assemblies</span></span>
<span data-ttu-id="07643-103">As classes podem ter o marshaling realizado somente pela interoperabilidade COM e sempre têm o marshaling realizado como interfaces.</span><span class="sxs-lookup"><span data-stu-id="07643-103">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="07643-104">Em alguns casos, a interface usada para realizar marshaling da classe é conhecida como a interface de classe.</span><span class="sxs-lookup"><span data-stu-id="07643-104">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="07643-105">Para obter informações sobre como substituir a interface de classe por uma interface de sua preferência, consulte [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md).</span><span class="sxs-lookup"><span data-stu-id="07643-105">For information about overriding the class interface with an interface of your choice, see [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md).</span></span>  
  
 <span data-ttu-id="07643-106">Embora qualquer desenvolvedor que deseje usar tipos COM de um aplicativo do .NET Framework possa gerar um assembly de interoperabilidade, fazer isso cria um problema.</span><span class="sxs-lookup"><span data-stu-id="07643-106">Although any developer who wants to use COM types from a .NET Framework application can generate an interop assembly, doing so creates a problem.</span></span> <span data-ttu-id="07643-107">Cada vez que um desenvolvedor importa e assina uma biblioteca de tipos COM, o desenvolvedor cria um conjunto de tipos exclusivos que são incompatíveis com aqueles importados e assinados por outro desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="07643-107">Each time a developer imports and signs a COM type library, that developer creates a set of unique types that are incompatible with those imported and signed by another developer.</span></span> <span data-ttu-id="07643-108">A solução para esse problema de incompatibilidade de tipo é que cada desenvolvedor obtenha o assembly de interoperabilidade primário assinado e fornecido pelo fornecedor.</span><span class="sxs-lookup"><span data-stu-id="07643-108">The solution to this type incompatibility problem is for each developer to obtain the vendor-supplied and signed primary interop assembly.</span></span>  
  
 <span data-ttu-id="07643-109">Se você pretende expor os tipos COM terceiros para outros aplicativos, use sempre o assembly de interoperabilidade primário fornecido pelo mesmo editor da biblioteca de tipos que esse assembly define.</span><span class="sxs-lookup"><span data-stu-id="07643-109">If you plan to expose third-party COM types to other applications, always use the primary interop assembly provided by the same publisher as the type library it defines.</span></span> <span data-ttu-id="07643-110">Além de fornecer compatibilidade garantida, os assemblies de interoperabilidade primários geralmente são personalizados pelo fornecedor para aprimorar a interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="07643-110">In addition to providing guaranteed type compatibility, primary interop assemblies are often customized by the vendor to enhance interoperability.</span></span>  
  
 <span data-ttu-id="07643-111">Mesmo se você não planeja expor os tipos COM terceiros, usar o assembly de interoperabilidade primário pode facilitar a tarefa de interoperar com componentes COM.</span><span class="sxs-lookup"><span data-stu-id="07643-111">Even if you do not plan to expose third-party COM types, using the primary interop assembly can ease the task of interoperating with COM components.</span></span> <span data-ttu-id="07643-112">No entanto, essa estratégia não fornece nenhum isolamento de alterações que um fornecedor possa fazer a tipos definidos em um assembly de interoperabilidade primário.</span><span class="sxs-lookup"><span data-stu-id="07643-112">However, this strategy provides no insulation from changes a vendor might make to types defined in a primary interop assembly.</span></span> <span data-ttu-id="07643-113">Quando seu aplicativo requer um isolamento desse tipo, gere seu próprio assembly de interoperabilidade em vez de usar o assembly de interoperabilidade primário.</span><span class="sxs-lookup"><span data-stu-id="07643-113">When your application requires such insulation, generate your own interop assembly instead of using the primary interop assembly.</span></span>  
  
 <span data-ttu-id="07643-114">Você deve registrar todos os assemblies de interoperabilidade primários adquiridos no computador de desenvolvimento antes que você possa referenciá-los com [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07643-114">You must register all acquired primary interop assemblies on your development computer before you can reference them with [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)].</span></span> <span data-ttu-id="07643-115">O Visual Studio procura e usa um assembly de interoperabilidade primário na primeira vez que você referenciar um tipo de uma biblioteca de tipos COM.</span><span class="sxs-lookup"><span data-stu-id="07643-115">Visual Studio looks for and uses a primary interop assembly the first time that you reference a type from a COM type library.</span></span> <span data-ttu-id="07643-116">Se o Visual Studio não puder localizar o assembly de interoperabilidade primário associado à biblioteca de tipos, ele solicitará que você o adquira ou oferecerá a possibilidade de criar um assembly de interoperabilidade em vez disso.</span><span class="sxs-lookup"><span data-stu-id="07643-116">If Visual Studio cannot locate the primary interop assembly associated with the type library, it prompts you to acquire it or offers to create an interop assembly instead.</span></span> <span data-ttu-id="07643-117">Da mesma forma, o [Importador de Biblioteca de Tipos (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) também usa o Registro para localizar assemblies de interoperabilidade primários.</span><span class="sxs-lookup"><span data-stu-id="07643-117">Likewise, the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) also uses the registry to locate primary interop assemblies.</span></span>  
  
 <span data-ttu-id="07643-118">Embora não seja necessário registrar assemblies de interoperabilidade primários a menos que você planeje usar o Visual Studio, o registro fornece duas vantagens:</span><span class="sxs-lookup"><span data-stu-id="07643-118">Although it is not necessary to register primary interop assemblies unless you plan to use Visual Studio, registration provides two advantages:</span></span>  
  
-   <span data-ttu-id="07643-119">Um assembly de interoperabilidade primário registrado é claramente marcado na chave do Registro da biblioteca de tipos original.</span><span class="sxs-lookup"><span data-stu-id="07643-119">A registered primary interop assembly is clearly marked under the registry key of the original type library.</span></span> <span data-ttu-id="07643-120">O registro é a melhor maneira de localizar um assembly de interoperabilidade primário em seu computador.</span><span class="sxs-lookup"><span data-stu-id="07643-120">Registration is the best way for you to locate a primary interop assembly on your computer.</span></span>  
  
-   <span data-ttu-id="07643-121">Você pode evitar gerar acidentalmente e usar um novo assembly de interoperabilidade se, em algum momento no futuro, você usar o Visual Studio para fazer referência a um tipo para o qual você tem um assembly de interoperabilidade primário não registrado.</span><span class="sxs-lookup"><span data-stu-id="07643-121">You can avoid accidentally generating and using a new interop assembly if, at some time in the future, you do use Visual Studio to reference a type for which you have an unregistered primary interop assembly.</span></span>  
  
 <span data-ttu-id="07643-122">Use a [Ferramenta de Registro do Assembly (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) para registrar um assembly de interoperabilidade primário.</span><span class="sxs-lookup"><span data-stu-id="07643-122">Use the [Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) to register a primary interop assembly.</span></span>  
  
### <a name="to-register-a-primary-interop-assembly"></a><span data-ttu-id="07643-123">Para registrar um assembly de interoperabilidade primário</span><span class="sxs-lookup"><span data-stu-id="07643-123">To register a primary interop assembly</span></span>  
  
1.  <span data-ttu-id="07643-124">No prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="07643-124">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="07643-125">**regasm** *nomedoassembly*</span><span class="sxs-lookup"><span data-stu-id="07643-125">**regasm** *assemblyname*</span></span>  
  
     <span data-ttu-id="07643-126">Nesse comando, *nomedoassembly* é o nome do arquivo do assembly que é registrado.</span><span class="sxs-lookup"><span data-stu-id="07643-126">In this command, *assemblyname* is the file name of the assembly that is registered.</span></span> <span data-ttu-id="07643-127">Regasm.exe adiciona uma entrada para o assembly de interoperabilidade primário sob a mesma chave do Registro da biblioteca de tipos original.</span><span class="sxs-lookup"><span data-stu-id="07643-127">Regasm.exe adds an entry for the primary interop assembly under the same registry key as the original type library.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07643-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07643-128">Example</span></span>  
 <span data-ttu-id="07643-129">O exemplo a seguir registra o assembly de interoperabilidade primário `CompanyA.UtilLib.dll`.</span><span class="sxs-lookup"><span data-stu-id="07643-129">The following example registers the `CompanyA.UtilLib.dll` primary interop assembly.</span></span>  
  
```  
regasm CompanyA.UtilLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="07643-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07643-130">See Also</span></span>  
 <span data-ttu-id="07643-131">[Programando com assemblies de interoperabilidade primários](http://msdn.microsoft.com/en-us/306fa1d6-0703-4004-9e93-d0a57f1be81e) </span><span class="sxs-lookup"><span data-stu-id="07643-131">[Programming with Primary Interop Assemblies](http://msdn.microsoft.com/en-us/306fa1d6-0703-4004-9e93-d0a57f1be81e) </span></span>  
 <span data-ttu-id="07643-132">[Localizando assemblies de interoperabilidade primários](http://msdn.microsoft.com/en-us/d6768e4b-cd80-414d-a4f8-05d979eb393b) </span><span class="sxs-lookup"><span data-stu-id="07643-132">[Locating Primary Interop Assemblies](http://msdn.microsoft.com/en-us/d6768e4b-cd80-414d-a4f8-05d979eb393b) </span></span>  
 [<span data-ttu-id="07643-133">Redistribuindo assemblies de interoperabilidade primários</span><span class="sxs-lookup"><span data-stu-id="07643-133">Redistributing Primary Interop Assemblies</span></span>](http://msdn.microsoft.com/en-us/e76384f0-d631-474c-bdbd-13884cba0265)
