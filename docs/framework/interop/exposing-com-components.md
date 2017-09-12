---
title: Expondo componentes do COM para o .NET Framework
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
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c0fcf7bec289d64b1faceef00b01278fa45caab0
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="83ec1-102">Expondo componentes do COM para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="83ec1-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="83ec1-103">Esta seção resume o processo necessário para expor um componente COM existente ao código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="83ec1-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="83ec1-104">Para obter detalhes sobre como escrever servidores COM que são totalmente integrados ao .NET Framework, consulte [Considerações sobre design para interoperação](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689).</span><span class="sxs-lookup"><span data-stu-id="83ec1-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689).</span></span>  
  
 <span data-ttu-id="83ec1-105">Os componentes COM existentes são recursos valiosos no código gerenciado, como aplicativos de negócios de camada intermediária ou como uma funcionalidade isolada.</span><span class="sxs-lookup"><span data-stu-id="83ec1-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="83ec1-106">Um componente ideal tem um assembly de interoperabilidade primário e está em conformidade total com os padrões de programação impostos pelo COM.</span><span class="sxs-lookup"><span data-stu-id="83ec1-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="83ec1-107">Para expor componentes COM ao .NET Framework</span><span class="sxs-lookup"><span data-stu-id="83ec1-107">To expose COM components to the .NET Framework</span></span>  
  
1.  <span data-ttu-id="83ec1-108">[Importe uma biblioteca de tipos como um assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="83ec1-108">[Import a type library as an assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="83ec1-109">O Common Language Runtime exige metadados para todos os tipos, incluindo tipos COM.</span><span class="sxs-lookup"><span data-stu-id="83ec1-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="83ec1-110">Há várias maneiras de obter um assembly que contém tipos COM importados como metadados.</span><span class="sxs-lookup"><span data-stu-id="83ec1-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2.  <span data-ttu-id="83ec1-111">[Crie tipos COM em um código gerenciado](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).</span><span class="sxs-lookup"><span data-stu-id="83ec1-111">[Create COM types in managed Code](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).</span></span>  
  
     <span data-ttu-id="83ec1-112">É possível inspecionar tipos COM, ativar instâncias e invocar métodos no objeto COM da mesma maneira que você faria com qualquer tipo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="83ec1-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3.  <span data-ttu-id="83ec1-113">[Compile um projeto de interoperabilidade](../../../docs/framework/interop/compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="83ec1-113">[Compile an interop project](../../../docs/framework/interop/compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="83ec1-114">O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] fornece compiladores para várias linguagens em conformidade com CLS (Common Language Specification), incluindo [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# e C++.</span><span class="sxs-lookup"><span data-stu-id="83ec1-114">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides compilers for several languages compliant with the Common Language Specification (CLS), including [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++.</span></span>  
  
4.  <span data-ttu-id="83ec1-115">[Implante um aplicativo de interoperabilidade](../../../docs/framework/interop/deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="83ec1-115">[Deploy an interop application](../../../docs/framework/interop/deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="83ec1-116">Os aplicativos de interoperabilidade são mais bem implantados como assemblies assinados [de nome forte](../../../docs/framework/app-domains/strong-named-assemblies.md) no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="83ec1-116">Interop applications are best deployed as [strong-named](../../../docs/framework/app-domains/strong-named-assemblies.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83ec1-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83ec1-117">See Also</span></span>  
 <span data-ttu-id="83ec1-118">[Interoperação com código não gerenciado](../../../docs/framework/interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="83ec1-118">[Interoperating with Unmanaged Code](../../../docs/framework/interop/index.md) </span></span>  
 <span data-ttu-id="83ec1-119">[Considerações sobre design para interoperação](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689) </span><span class="sxs-lookup"><span data-stu-id="83ec1-119">[Design Considerations for Interoperation](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689) </span></span>  
 <span data-ttu-id="83ec1-120">[Amostra de interoperabilidade COM: cliente .NET e servidor COM](../../../docs/framework/interop/com-interop-sample-net-client-and-com-server.md) </span><span class="sxs-lookup"><span data-stu-id="83ec1-120">[COM Interop Sample: .NET Client and COM Server](../../../docs/framework/interop/com-interop-sample-net-client-and-com-server.md) </span></span>  
 <span data-ttu-id="83ec1-121">[Independência de linguagem e componentes independentes de linguagem](../../../docs/standard/language-independence-and-language-independent-components.md) </span><span class="sxs-lookup"><span data-stu-id="83ec1-121">[Language Independence and Language-Independent Components](../../../docs/standard/language-independence-and-language-independent-components.md) </span></span>  
 [<span data-ttu-id="83ec1-122">Gacutil.exe (Ferramenta Cache de Assembly Global)</span><span class="sxs-lookup"><span data-stu-id="83ec1-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
