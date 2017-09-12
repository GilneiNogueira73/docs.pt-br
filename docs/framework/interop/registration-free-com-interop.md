---
title: Interoperabilidade COM sem registro
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
- assemblies [.NET Framework], interop
- COM interop, registration-free COM interop
- registration-free COM interop
- manifests [.NET Framework]
- registration-free activation
- object activation
- registration-free COM interop, about registration-free COM interop
ms.assetid: 90f308b9-82dc-414a-bce1-77e0155e56bd
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: dd08f4d4466582b1e6ff1f80f586482cd3e2ec0c
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="registration-free-com-interop"></a><span data-ttu-id="9f2b3-102">Interoperabilidade COM sem registro</span><span class="sxs-lookup"><span data-stu-id="9f2b3-102">Registration-Free COM Interop</span></span>
<span data-ttu-id="9f2b3-103">A interoperabilidade COM sem registro ativa um componente sem usar o Registro do Windows para armazenar informações de assembly.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-103">Registration-free COM interop activates a component without using the Windows registry to store assembly information.</span></span> <span data-ttu-id="9f2b3-104">Em vez de registrar um componente em um computador durante a implantação, você pode criar arquivos de manifesto estilo Win32 em tempo de design que contêm informações sobre associação e a ativação.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-104">Instead of registering a component on a computer during deployment, you create Win32-style manifest files at design time that contain information about binding and activation.</span></span> <span data-ttu-id="9f2b3-105">Esses arquivos de manifesto, em vez de chaves do Registro, direcionam a ativação de um objeto.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-105">These manifest files, rather than registry keys, direct the activation of an object.</span></span>  
  
 <span data-ttu-id="9f2b3-106">Usar a ativação sem registro dos assemblies em vez de registrá-los durante a implantação oferece duas vantagens:</span><span class="sxs-lookup"><span data-stu-id="9f2b3-106">Using registration-free activation for your assemblies instead of registering them during deployment offers two advantages:</span></span>  
  
-   <span data-ttu-id="9f2b3-107">Você pode controlar qual versão DLL é ativada quando mais de uma versão é instalada em um computador.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-107">You can control which DLL version is activated when more than one version is installed on a computer.</span></span>  
  
-   <span data-ttu-id="9f2b3-108">Os usuários finais podem usar XCOPY ou FTP para copiar seu aplicativo para um diretório apropriado no computador deles.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-108">End users can use XCOPY or FTP to copy your application to an appropriate directory on their computer.</span></span> <span data-ttu-id="9f2b3-109">Assim, o aplicativo pode ser executado nesse diretório.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-109">The application can then be run from that directory.</span></span>  
  
 <span data-ttu-id="9f2b3-110">Esta seção descreve os dois tipos de manifestos necessários para a interoperação COM sem registro: manifestos de aplicativo e de componente.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-110">This section describes the two types of manifests needed for registration-free COM interop: application and component manifests.</span></span> <span data-ttu-id="9f2b3-111">Esses manifestos são arquivos XML.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-111">These manifests are XML files.</span></span> <span data-ttu-id="9f2b3-112">Um manifesto de aplicativo, que é criado por um desenvolvedor de aplicativos, contém metadados que descrevem os assemblies e as dependências de assembly.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-112">An application manifest, which is created by an application developer, contains metadata that describes assemblies and assembly dependencies.</span></span> <span data-ttu-id="9f2b3-113">Um manifesto do componente, criado por um desenvolvedor de componente, contém informações que residem no Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-113">A component manifest, created by a component developer, contains information otherwise located in the Windows registry.</span></span>  
  
### <a name="requirements-for-registration-free-com-interop"></a><span data-ttu-id="9f2b3-114">Requisitos da interoperabilidade COM sem registro</span><span class="sxs-lookup"><span data-stu-id="9f2b3-114">Requirements for registration-free COM interop</span></span>  
  
1.  <span data-ttu-id="9f2b3-115">O suporte para a interoperabilidade COM sem registro varia ligeiramente dependendo do tipo de assembly de biblioteca; especificamente, se o assembly é não gerenciado (COM lado a lado) ou gerenciado (baseado em .NET).</span><span class="sxs-lookup"><span data-stu-id="9f2b3-115">Support for registration-free COM interop varies slightly depending on the type of library assembly; specifically, whether the assembly is unmanaged (COM side-by-side) or managed (.NET-based).</span></span> <span data-ttu-id="9f2b3-116">A tabela a seguir mostra o sistema operacional e os requisitos de versão do .NET Framework para cada tipo de assembly.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-116">The following table shows the operating system and .NET Framework version requirements for each assembly type.</span></span>  
  
    |<span data-ttu-id="9f2b3-117">Tipo de assembly</span><span class="sxs-lookup"><span data-stu-id="9f2b3-117">Assembly type</span></span>|<span data-ttu-id="9f2b3-118">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="9f2b3-118">Operating system</span></span>|<span data-ttu-id="9f2b3-119">Versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9f2b3-119">.NET Framework version</span></span>|  
    |-------------------|----------------------|----------------------------|  
    |<span data-ttu-id="9f2b3-120">COM lado a lado</span><span class="sxs-lookup"><span data-stu-id="9f2b3-120">COM side-by-side</span></span>|<span data-ttu-id="9f2b3-121">Microsoft Windows XP</span><span class="sxs-lookup"><span data-stu-id="9f2b3-121">Microsoft Windows XP</span></span>|<span data-ttu-id="9f2b3-122">Não obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-122">Not required.</span></span>|  
    |<span data-ttu-id="9f2b3-123">Com base em .NET</span><span class="sxs-lookup"><span data-stu-id="9f2b3-123">.NET-based</span></span>|<span data-ttu-id="9f2b3-124">Windows XP com SP2</span><span class="sxs-lookup"><span data-stu-id="9f2b3-124">Windows XP with SP2</span></span>|<span data-ttu-id="9f2b3-125">.NET framework versão 1.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-125">NET Framework version 1.1 or later.</span></span>|  
  
     <span data-ttu-id="9f2b3-126">A família Windows Server 2003 também dá suporte à interoperabilidade COM sem registro para assemblies com base em .NET.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-126">The Windows Server 2003 family also supports registration-free COM interop for .NET-based assemblies.</span></span>  
  
     <span data-ttu-id="9f2b3-127">Para que uma classe com base em .NET seja compatível com a ativação sem registro do COM, a classe deve ter um construtor padrão e deve ser pública.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-127">For a .NET-based class to be compatible with registry-free activation from COM, the class must have a default constructor and must be public.</span></span>  
  
### <a name="configuring-com-components-for-registration-free-activation"></a><span data-ttu-id="9f2b3-128">Configurando componentes COM para ativação sem registro</span><span class="sxs-lookup"><span data-stu-id="9f2b3-128">Configuring COM components for registration-free activation</span></span>  
  
1.  <span data-ttu-id="9f2b3-129">Para um componente COM participar da ativação sem registro, ele deve ser implantado como um assembly lado a lado.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-129">For a COM component to participate in registration-free activation, it must be deployed as a side-by-side assembly.</span></span> <span data-ttu-id="9f2b3-130">Assemblies de lado a lado são não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-130">Side-by-side assemblies are unmanaged assemblies.</span></span>  <span data-ttu-id="9f2b3-131">Para obter mais informações, veja “Assemblies lado a lado” na Biblioteca MSDN.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-131">For more information, see "Using Side-by-side Assemblies" in the MSDN Library.</span></span>  
  
     <span data-ttu-id="9f2b3-132">Para usar os assemblies com lado a lado COM, um desenvolvedor de aplicativos baseados em .NET em sua empresa deve fornecer um manifesto de aplicativo contendo as informações de associação e a ativação.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-132">To use COM side-by-side assemblies, a .NET-based application developer must provide an application manifest, which contains the binding and activation information.</span></span> <span data-ttu-id="9f2b3-133">O suporte para assemblies lado a lado não gerenciados é criado no sistema operacional Windows XP.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-133">Support for unmanaged side-by-side assemblies is built into the Windows XP operating system.</span></span> <span data-ttu-id="9f2b3-134">O tempo de execução de COM, com suporte pelo sistema operacional, verifica um manifesto de aplicativo para obter informações de ativação quando o componente está sendo ativado não está no Registro.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-134">The COM runtime, supported by the operating system, scans an application manifest for activation information when the component being activated is not in the registry.</span></span>  
  
     <span data-ttu-id="9f2b3-135">Ativação sem registro é opcional para componentes COM instalados no Windows XP.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-135">Registration-free activation is optional for COM components installed on Windows XP.</span></span> <span data-ttu-id="9f2b3-136">Para obter instruções detalhadas sobre como adicionar um assembly lado a lado para um aplicativo, pesquise por "Usando assemblies lado a lado" na biblioteca MSDN.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-136">For detailed instructions on adding a side-by-side assembly to an application, search for "Using Side-by-side Assemblies" in the MSDN Library.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9f2b3-137">A execução lado a lado é um recurso do .NET que habilita várias versões do tempo de execução e várias versões de aplicativos e componentes que usam uma versão do tempo de execução no mesmo computador, ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-137">Side-by-side execution is a .NET Framework feature that enables multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, to run on the same computer at the same time.</span></span> <span data-ttu-id="9f2b3-138">Execução lado a lado e assemblies lado a lado são mecanismos diferentes para fornecer funcionalidade de lado a lado.</span><span class="sxs-lookup"><span data-stu-id="9f2b3-138">Side-by-side execution and side-by-side assemblies are different mechanisms for providing side-by-side functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f2b3-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f2b3-139">See Also</span></span>  
 [<span data-ttu-id="9f2b3-140">Como configurar componentes do COM baseados no .NET Framework para ativação sem registro</span><span class="sxs-lookup"><span data-stu-id="9f2b3-140">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](../../../docs/framework/interop/configure-net-framework-based-com-components-for-reg.md)
