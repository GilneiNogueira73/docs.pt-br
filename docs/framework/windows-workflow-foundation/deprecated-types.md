---
title: "Substituído em Windows Workflow Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 422e95a105978749cc56dfe6601fb4518cc11509
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="7801e-102">Substituído em Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="7801e-102">Deprecated types in Windows Workflow Foundation</span></span>
<span data-ttu-id="7801e-103">Em .NET 4 a equipe de fluxo de trabalho liberou qualquer novo mecanismo de fluxo de trabalho no espaço de <xref:System.Activities> .</span><span class="sxs-lookup"><span data-stu-id="7801e-103">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="7801e-104">Com o lançamento da versão Beta do .NET 4.5, marcar a maioria dos tipos de "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, e <xref:System.Workflow.Runtime> namespaces como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="7801e-104">With the release of .NET 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>  
  
## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="7801e-105">Namespaces e ferramentas obsoletas</span><span class="sxs-lookup"><span data-stu-id="7801e-105">Obsolete namespaces and tools</span></span>  
 <span data-ttu-id="7801e-106">Os seguintes conjuntos possuem um ou mais tipos públicos que serão substituídos:</span><span class="sxs-lookup"><span data-stu-id="7801e-106">The following assemblies have one or more public types that will be deprecated:</span></span>  
  
-   <span data-ttu-id="7801e-107">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="7801e-107">System.Workflow.Activities.dll</span></span>  
  
-   <span data-ttu-id="7801e-108">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="7801e-108">System.Workflow.ComponentModel.dll</span></span>  
  
-   <span data-ttu-id="7801e-109">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="7801e-109">System.Workflow.Runtime.dll</span></span>  
  
-   <span data-ttu-id="7801e-110">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="7801e-110">System.WorkflowServices.dll</span></span>  
  
-   <span data-ttu-id="7801e-111">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="7801e-111">Microsoft.Workflow.DebugController.dll</span></span>  
  
-   <span data-ttu-id="7801e-112">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="7801e-112">Microsoft.Workflow.Compiler.exe</span></span>  
  
-   <span data-ttu-id="7801e-113">Wfc.exe</span><span class="sxs-lookup"><span data-stu-id="7801e-113">Wfc.exe</span></span>  
  
 <span data-ttu-id="7801e-114">Como resultado, os clientes que são substituídos usando APIs de WF 3 encontrarão avisos de compilação com uma mensagem semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="7801e-114">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>  
  
 <span data-ttu-id="7801e-115">**Aviso BC40000: X é obsoleta: WF 3 tipos são preteridos. Use o WF 4.**</span><span class="sxs-lookup"><span data-stu-id="7801e-115">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="7801e-116">Nós removeremos os tipos do.NET Framework em uma versão futura, mas nós não determinamos ainda esse o prazo (não em 4,5).</span><span class="sxs-lookup"><span data-stu-id="7801e-116">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="7801e-117">Esta etapa atual permite que nós comuniquem a direção a nossos clientes e permitam-lhes a abundância hora de mover para o novo modelo WF4.</span><span class="sxs-lookup"><span data-stu-id="7801e-117">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="7801e-118">Obviamente, continuaremos a dar suporte a esses tipos de WF 3 no [política de ciclo de vida do suporte da Microsoft](http://aka.ms/MicrosoftSupportLifecycle).</span><span class="sxs-lookup"><span data-stu-id="7801e-118">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](http://aka.ms/MicrosoftSupportLifecycle).</span></span> <span data-ttu-id="7801e-119">Os aplicativos WF3 existentes serão executados sem problema no .NET 4.5, e [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ele novos e existentes de soluções WF3-based.</span><span class="sxs-lookup"><span data-stu-id="7801e-119">Existing WF3 applications will run without issue on .NET 4.5, and [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] will support new and existing WF3-based solutions.</span></span>  
  
 <span data-ttu-id="7801e-120">As regras tipos relacionados ao espaço de <xref:System.Workflow.Activities.Rules> , que não têm uma substituição em WF 4,5, não foram substituídas dentro.</span><span class="sxs-lookup"><span data-stu-id="7801e-120">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>  
  
 <span data-ttu-id="7801e-121">Os clientes que desejam migrar seus aplicativos para o WF 4 encontrará ajuda a [orientação de migração do fluxo de trabalho 4](migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="7801e-121">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>