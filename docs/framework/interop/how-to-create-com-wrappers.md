---
title: Como criar wrappers COM
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
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e99b084ddb565a8ae00ee917eaf7fca2c659ab64
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="f9391-102">Como criar wrappers COM</span><span class="sxs-lookup"><span data-stu-id="f9391-102">How to: Create COM Wrappers</span></span>
<span data-ttu-id="f9391-103">Crie wrappers COM (Component Object Model) usando recursos do [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] ou as ferramentas Tlbimp.exe e Regasm.exe do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f9391-103">You can create Component Object Model (COM) wrappers by using [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="f9391-104">Ambos os métodos geram dois tipos de wrappers COM:</span><span class="sxs-lookup"><span data-stu-id="f9391-104">Both methods generate two types of COM wrappers:</span></span>  
  
-   <span data-ttu-id="f9391-105">Um [RCW (Runtime Callable Wrapper)](../../../docs/framework/interop/runtime-callable-wrapper.md) de uma biblioteca de tipos para executar um objeto COM em um código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f9391-105">A [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>  
  
-   <span data-ttu-id="f9391-106">Um [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md) com as configurações do Registro necessárias para executar um objeto gerenciado em um aplicativo nativo.</span><span class="sxs-lookup"><span data-stu-id="f9391-106">A [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>  
  
 <span data-ttu-id="f9391-107">No [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], você pode adicionar o wrapper COM como uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="f9391-107">In [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], you can add the COM wrapper as a reference to your project.</span></span>  
  
## <a name="wrapping-com-objects-in-a-managed-application"></a><span data-ttu-id="f9391-108">Encapsulando objetos COM em um aplicativo gerenciado</span><span class="sxs-lookup"><span data-stu-id="f9391-108">Wrapping COM Objects in a Managed Application</span></span>  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="f9391-109">Para criar um RCW (Runtime Callable Wrapper) usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f9391-109">To create a runtime callable wrapper using Visual Studio</span></span>  
  
1.  <span data-ttu-id="f9391-110">Abra o projeto do aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f9391-110">Open the project for your managed application.</span></span>  
  
2.  <span data-ttu-id="f9391-111">No menu **Projeto**, clique em **Mostrar Todos os Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="f9391-111">On the **Project** menu, click **Show All Files**.</span></span>  
  
3.  <span data-ttu-id="f9391-112">No menu **Projeto**, clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="f9391-112">On the **Project** menu, click **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="f9391-113">Na caixa de diálogo Adicionar Referência, clique na guia **COM**, selecione o componente que você deseja usar e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="f9391-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>  
  
     <span data-ttu-id="f9391-114">No **Gerenciador de Soluções**, observe que o componente COM é adicionado à pasta Referências do projeto.</span><span class="sxs-lookup"><span data-stu-id="f9391-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>  
  
 <span data-ttu-id="f9391-115">Agora você pode escrever o código para acessar o objeto COM.</span><span class="sxs-lookup"><span data-stu-id="f9391-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="f9391-116">Comece declarando o objeto, por exemplo, com uma instrução `Imports` para [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] ou uma instrução `Using` para [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9391-116">You can begin by declaring the object, such as with an `Imports` statement for [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] or a `Using` statement for [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9391-117">Caso deseje programar componentes do Microsoft Office, primeiro instale os [PIAs (Assemblies de Interoperabilidade Primários) do Microsoft Office](http://go.microsoft.com/fwlink/?LinkId=50479) no Centro de Download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f9391-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies](http://go.microsoft.com/fwlink/?LinkId=50479) (PIAs) from the Microsoft Download Center.</span></span> <span data-ttu-id="f9391-118">Na etapa 4, selecione a última versão da biblioteca de objetos disponível para o produto do Office desejado, como a **Biblioteca de Objetos do Microsoft Word 11.0**.</span><span class="sxs-lookup"><span data-stu-id="f9391-118">In step 4, select the latest version of the object library available for the Office product you want, such as the **Microsoft Word 11.0 Object Library**.</span></span>  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="f9391-119">Para criar um RCW (Runtime Callable Wrapper) usando ferramentas do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f9391-119">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
-   <span data-ttu-id="f9391-120">Execute a ferramenta [Tlbimp.exe (Importador da Biblioteca de Tipos)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="f9391-120">Run the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="f9391-121">Essa ferramenta cria um assembly que contém metadados em tempo de execução para os tipos definidos na biblioteca de tipos original.</span><span class="sxs-lookup"><span data-stu-id="f9391-121">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrapping-managed-objects-in-a-native-application"></a><span data-ttu-id="f9391-122">Encapsulando objetos gerenciados em um aplicativo nativo</span><span class="sxs-lookup"><span data-stu-id="f9391-122">Wrapping Managed Objects in a Native Application</span></span>  
  
#### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="f9391-123">Para criar um COM Callable Wrapper usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f9391-123">To create a COM callable wrapper using Visual Studio</span></span>  
  
1.  <span data-ttu-id="f9391-124">Crie um projeto de Biblioteca de Classes para a classe gerenciada que você deseja executar no código nativo.</span><span class="sxs-lookup"><span data-stu-id="f9391-124">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="f9391-125">A classe deve ter um construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="f9391-125">The class must have a default constructor.</span></span>  
  
     <span data-ttu-id="f9391-126">Verifique se você tem um número de versão de quatro partes completo para o assembly no arquivo AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="f9391-126">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="f9391-127">Esse número é necessário para manter o controle de versão no Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="f9391-127">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="f9391-128">Para obter mais informações sobre os números de versão, consulte [Controle de versão do assembly](../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="f9391-128">For more information about version numbers, see [Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
2.  <span data-ttu-id="f9391-129">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="f9391-129">On the **Project** menu, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="f9391-130">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="f9391-130">Click the **Compile** tab.</span></span>  
  
4.  <span data-ttu-id="f9391-131">Marque a caixa de seleção **Registrar para interoperabilidade COM**.</span><span class="sxs-lookup"><span data-stu-id="f9391-131">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="f9391-132">Quando você cria o projeto, o assembly é registrado automaticamente para a interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="f9391-132">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="f9391-133">Se estiver criando um aplicativo nativo no [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], use o assembly clicando em **Adicionar Referência** no menu **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="f9391-133">If you are building a native application in [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
#### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="f9391-134">Para criar um COM Callable Wrapper usando ferramentas do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f9391-134">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
-   <span data-ttu-id="f9391-135">Execute a ferramenta [Regasm.exe (Ferramenta de Registro de Assembly)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="f9391-135">Run the [Regasm.exe (Assembly Registration Tool)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
 <span data-ttu-id="f9391-136">Essa ferramenta lê os metadados do assembly e adiciona as entradas necessárias ao Registro.</span><span class="sxs-lookup"><span data-stu-id="f9391-136">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="f9391-137">Como resultado, os clientes COM podem criar classes do .NET Framework de forma transparente.</span><span class="sxs-lookup"><span data-stu-id="f9391-137">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="f9391-138">Use o assembly como se ele fosse uma classe COM nativa.</span><span class="sxs-lookup"><span data-stu-id="f9391-138">You can use the assembly as if it were a native COM class.</span></span>  
  
 <span data-ttu-id="f9391-139">Execute o Regasm.exe em um assembly localizado em qualquer diretório e, em seguida, execute o [Gacutil.exe (Ferramenta do Cache de Assembly Global)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) para movê-lo para o cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="f9391-139">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="f9391-140">A movimentação do assembly não invalida as entradas do Registro de local, porque o cache de assembly global sempre será examinado se o assembly não for encontrado em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="f9391-140">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9391-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9391-141">See Also</span></span>  
 <span data-ttu-id="f9391-142">[RCW (Runtime Callable Wrapper)](../../../docs/framework/interop/runtime-callable-wrapper.md) </span><span class="sxs-lookup"><span data-stu-id="f9391-142">[Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) </span></span>  
 [<span data-ttu-id="f9391-143">COM Callable Wrapper</span><span class="sxs-lookup"><span data-stu-id="f9391-143">COM Callable Wrapper</span></span>](../../../docs/framework/interop/com-callable-wrapper.md)
