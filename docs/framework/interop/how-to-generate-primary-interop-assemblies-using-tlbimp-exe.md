---
title: "Como gerar assemblies de interoperabilidade primários usando Tlbimp.exe"
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
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 253fb49742cc1969a5412248b01be295a45c282f
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a><span data-ttu-id="1d7f7-102">Como gerar assemblies de interoperabilidade primários usando Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="1d7f7-102">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>
<span data-ttu-id="1d7f7-103">Há duas maneiras de gerar um assembly de interoperabilidade primário:</span><span class="sxs-lookup"><span data-stu-id="1d7f7-103">There are two ways to generate a primary interop assembly:</span></span>  
  
-   <span data-ttu-id="1d7f7-104">Usando o [Importador de Biblioteca de Tipos (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) fornecido pelo [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1d7f7-104">Using the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
     <span data-ttu-id="1d7f7-105">A maneira mais simples de gerar assemblies de interoperabilidade primários é usar o [Tlbimp.exe (Importador de Biblioteca de Tipos)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="1d7f7-105">The most straightforward way to produce primary interop assemblies is to use the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="1d7f7-106">O Tlbimp.exe fornece as seguintes garantias:</span><span class="sxs-lookup"><span data-stu-id="1d7f7-106">Tlbimp.exe provides the following safeguards:</span></span>  
  
    -   <span data-ttu-id="1d7f7-107">Verifica se há outros assemblies de interoperabilidade primários registrados antes de criar novos assemblies de interoperabilidade para quaisquer referências aninhadas de biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-107">Checks for other registered primary interop assemblies before creating new interop assemblies for any nested type library references.</span></span>  
  
    -   <span data-ttu-id="1d7f7-108">Falhará ao emitir o assembly de interoperabilidade primário se você não especificar o contêiner ou o nome de arquivo para dar um nome forte ao assembly de interoperabilidade primário.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-108">Fails to emit the primary interop assembly if you do not specify either the container or file name to give the primary interop assembly a strong name.</span></span>  
  
    -   <span data-ttu-id="1d7f7-109">Falhará ao emitir um assembly de interoperabilidade primário se você omitir referências a assemblies dependentes.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-109">Fails to emit a primary interop assembly if you omit references to dependent assemblies.</span></span>  
  
    -   <span data-ttu-id="1d7f7-110">Falhará ao emitir um assembly de interoperabilidade primário se você adicionar referências a assemblies dependentes que não forem assemblies de interoperabilidade primários.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-110">Fails to emit a primary interop assembly if you add references to dependent assemblies that are not primary interop assemblies.</span></span>  
  
-   <span data-ttu-id="1d7f7-111">Criando assemblies de interoperabilidade primários manualmente no código-fonte usando uma linguagem em conformidade com CLS (Common Language Specification), tal como C#.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-111">Creating primary interop assemblies manually in source code by using a language that is compliant with the Common Language Specification (CLS), such as C#.</span></span> <span data-ttu-id="1d7f7-112">Essa abordagem é útil quando uma biblioteca de tipos não está disponível.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-112">This approach is useful when a type library is unavailable.</span></span>  
  
 <span data-ttu-id="1d7f7-113">Você deve ter um par de chaves de criptografia para assinar o assembly com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-113">You must have a cryptographic key pair to sign the assembly with a strong name.</span></span> <span data-ttu-id="1d7f7-114">Para obter detalhes, consulte [Criando um par de chaves](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="1d7f7-114">For details, see [Creating A Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a><span data-ttu-id="1d7f7-115">Para gerar um assembly de interoperabilidade primário usando Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="1d7f7-115">To generate a primary interop assembly using Tlbimp.exe</span></span>  
  
1.  <span data-ttu-id="1d7f7-116">No prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="1d7f7-116">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="1d7f7-117">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span><span class="sxs-lookup"><span data-stu-id="1d7f7-117">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span></span>  
  
     <span data-ttu-id="1d7f7-118">Neste comando, *tlbfile* é o arquivo que contém a biblioteca de tipo COM, *filename* é o nome do contêiner ou arquivo que contém o par de chaves e *assemblyname* é o nome do assembly a assinar com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-118">In this command, *tlbfile* is the file containing the COM type library, *filename* is the name of the container or file that contains the key pair, and *assemblyname* is the name of the assembly to sign with a strong name.</span></span>  
  
 <span data-ttu-id="1d7f7-119">Assemblies de interoperabilidade primários podem referenciar somente outros assemblies de interoperabilidade primários.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-119">Primary interop assemblies can reference only other primary interop assemblies.</span></span> <span data-ttu-id="1d7f7-120">Se seu assembly faz referência a tipos de uma biblioteca de tipos COM de terceiros, você deve obter um assembly de interoperabilidade primário do editor antes de gerar o assembly de interoperabilidade primário.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-120">If your assembly references types from a third-party COM type library, you must obtain a primary interop assembly from the publisher before you can generate your primary interop assembly.</span></span> <span data-ttu-id="1d7f7-121">Se você for o editor, você deverá gerar um assembly de interoperabilidade primário para a biblioteca de tipos dependentes antes de gerar o assembly de interoperabilidade primário que fará referência.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-121">If you are the publisher, you must generate a primary interop assembly for the dependent type library before generating the referencing primary interop assembly.</span></span>  
  
 <span data-ttu-id="1d7f7-122">Um assembly de interoperabilidade primário dependente com um número de versão diferente daquele da biblioteca de tipos original não pode ser descoberto quando instalado no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-122">A dependent primary interop assembly with a version number that differs from that of the original type library is not discoverable when installed in the current directory.</span></span> <span data-ttu-id="1d7f7-123">Você deverá registrar o assembly de interoperabilidade primário dependente no Registro do Windows ou usar a opção **/Reference** para certificar-se de que Tlbimp.exe localizará a DLL dependente.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-123">You must either register the dependent primary interop assembly in the Windows registry or use the **/reference** option to be sure that Tlbimp.exe finds the dependent DLL.</span></span>  
  
 <span data-ttu-id="1d7f7-124">Você também pode encapsular várias versões de uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-124">You can also wrap multiple versions of a type library.</span></span> <span data-ttu-id="1d7f7-125">Para obter instruções, consulte [Como encapsular várias versões de bibliotecas de tipos](http://msdn.microsoft.com/en-us/79eefe04-a770-4bc3-8ea2-e90ddb8ec31f).</span><span class="sxs-lookup"><span data-stu-id="1d7f7-125">For instructions, see [How to: Wrap Multiple Versions of Type Libraries](http://msdn.microsoft.com/en-us/79eefe04-a770-4bc3-8ea2-e90ddb8ec31f).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d7f7-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1d7f7-126">Example</span></span>  
 <span data-ttu-id="1d7f7-127">O exemplo a seguir importa a biblioteca de tipos COM `LibUtil.tlb` e assina o assembly `LibUtil.dll` com um nome forte usando o arquivo de chave `CompanyA.snk`.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-127">The following example imports the COM type library `LibUtil.tlb` and signs the assembly `LibUtil.dll` with a strong name using the key file `CompanyA.snk`.</span></span> <span data-ttu-id="1d7f7-128">Omitindo um nome de namespace específico, este exemplo produz o namespace padrão, `LibUtil`.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-128">By omitting a specific namespace name, this example produces the default namespace, `LibUtil`.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll  
```  
  
 <span data-ttu-id="1d7f7-129">Para um nome mais descritivo (usando a diretriz de nomenclatura *VendorName*.*LibraryName*), o exemplo a seguir substitui o nome do arquivo do assembly padrão e o nome do namespace.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-129">For a more descriptive name (using the *VendorName*.*LibraryName* naming guideline), the following example overrides the default assembly file name and namespace name.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll  
```  
  
 <span data-ttu-id="1d7f7-130">O exemplo a seguir importa `MyLib.tlb`, que referencia `CompanyA.LibUtil.dll` e assina o assembly `CompanyB.MyLib.dll` com um nome forte usando o arquivo de chave `CompanyB.snk`.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-130">The following example imports `MyLib.tlb`, which references `CompanyA.LibUtil.dll`, and signs the assembly `CompanyB.MyLib.dll` with a strong name using the key file `CompanyB.snk`.</span></span> <span data-ttu-id="1d7f7-131">O namespace `CompanyB.MyLib` substitui o nome do namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="1d7f7-131">The namespace, `CompanyB.MyLib`, overrides the default namespace name.</span></span>  
  
```  
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d7f7-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d7f7-132">See Also</span></span>  
 [<span data-ttu-id="1d7f7-133">Como registrar assemblies de interoperabilidade primários</span><span class="sxs-lookup"><span data-stu-id="1d7f7-133">How to: Register Primary Interop Assemblies</span></span>](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
