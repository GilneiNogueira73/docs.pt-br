---
title: "Segurança"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0063497bc500a11d59dd88e0cb7d738d5c4bb6e5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="security"></a><span data-ttu-id="523c1-102">Segurança</span><span class="sxs-lookup"><span data-stu-id="523c1-102">Security</span></span>
<span data-ttu-id="523c1-103">A instância Store de fluxo de trabalho do SQL usa as seguintes funções de segurança de base de dados para proteger o acesso a informações do estado da instância na base de dados de persistência.</span><span class="sxs-lookup"><span data-stu-id="523c1-103">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
-   <span data-ttu-id="523c1-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span><span class="sxs-lookup"><span data-stu-id="523c1-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="523c1-105">Essa função tem acesso de leitura e gravação para a exibição e a direita públicas de execução procedimentos armazenados que estão envolvidos na criação, em carregar e salvar em instâncias.</span><span class="sxs-lookup"><span data-stu-id="523c1-105">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
-   <span data-ttu-id="523c1-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span><span class="sxs-lookup"><span data-stu-id="523c1-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="523c1-107">Essa função tem acesso somente leitura modos de exibição públicas.</span><span class="sxs-lookup"><span data-stu-id="523c1-107">This role has read-only access to public views.</span></span>  
  
-   <span data-ttu-id="523c1-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span><span class="sxs-lookup"><span data-stu-id="523c1-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="523c1-109">Essa função tem direitos de execução procedimentos armazenados que estão envolvidos no processo de ativação da instância.</span><span class="sxs-lookup"><span data-stu-id="523c1-109">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="523c1-110">Para obter mais informações sobre a ativação de instância, consulte [ativação de instância](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span><span class="sxs-lookup"><span data-stu-id="523c1-110">For more information about instance activation, see [Instance Activation](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span></span> <span data-ttu-id="523c1-111">A conta de usuário em que um host genérico (como o serviço de gerenciamento de fluxo de trabalho [!INCLUDE[dublin](../../../includes/dublin-md.md)]) executa deve ser adicionada à essa função de base de dados.</span><span class="sxs-lookup"><span data-stu-id="523c1-111">The user account under which a generic host (such as the Workflow Management Service of [!INCLUDE[dublin](../../../includes/dublin-md.md)]) runs should be added to this database role.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="523c1-112">segurança de persistência lojas com a malha de aplicativos do Windows Server, consulte [configuração de segurança para os armazenamentos de persistência na malha de aplicativos](http://go.microsoft.com/fwlink/?LinkId=201208)</span><span class="sxs-lookup"><span data-stu-id="523c1-112"> security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](http://go.microsoft.com/fwlink/?LinkId=201208)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="523c1-113">Um cliente que tenha acesso a seus próprios dados de instância no armazenamento de instância tem acesso a todas as outras instâncias no mesmo armazenamento de instância.</span><span class="sxs-lookup"><span data-stu-id="523c1-113">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="523c1-114">O armazenamento de instância não suporta especificar permissões de segurança no nível da instância.</span><span class="sxs-lookup"><span data-stu-id="523c1-114">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="523c1-115">Você deve criar armazenamentos separados de instância e mapear grupos/usuários diferentes para ter acesso aos armazenamentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="523c1-115">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>