---
title: Como executar um fluxo de trabalho
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a3467b9319a883445d95978e0c167a5552211afe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="44b0e-102">Como executar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="44b0e-102">How to: Run a Workflow</span></span>
<span data-ttu-id="44b0e-103">Este tópico é uma continuação do tutorial do guia de Introdução do Windows Workflow Foundation e discute como criar um host de fluxo de trabalho e executar o fluxo de trabalho definido anteriormente na [como: criar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="44b0e-103">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44b0e-104">Cada tópico do tutorial de Introdução depende dos tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="44b0e-104">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="44b0e-105">Para concluir este tópico, você deve completar [como: criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) e [como: criar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="44b0e-105">To complete this topic you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) and [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44b0e-106">Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="44b0e-106">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="44b0e-107">Para criar o projeto de host de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="44b0e-107">To create the workflow host project</span></span>  
  
1.  <span data-ttu-id="44b0e-108">Abra a solução do anterior [como: criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tópico usando [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="44b0e-108">Open the solution from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic by using [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="44b0e-109">Com o botão direito do **WF45GettingStartedTutorial** solução **Solution Explorer** e selecione **adicionar**, **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="44b0e-109">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="44b0e-110">Se o **Solution Explorer** janela não for exibida, selecione **Solution Explorer** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="44b0e-110">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="44b0e-111">No **instalado** nó, selecione **Visual C#**, **fluxo de trabalho** (ou **Visual Basic**, **fluxo de trabalho**).</span><span class="sxs-lookup"><span data-stu-id="44b0e-111">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="44b0e-112">Dependendo da linguagem de programação que é configurada como linguagem primária no Visual Studio, o **Visual C#** ou **Visual Basic** nó pode estar sob o **outras linguagens** nó de **instalado** nó.</span><span class="sxs-lookup"><span data-stu-id="44b0e-112">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
     <span data-ttu-id="44b0e-113">Certifique-se de que **.NET Framework 4.5** está selecionado na lista suspensa de versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44b0e-113">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="44b0e-114">Selecione **aplicativo de Console do fluxo de trabalho** do **fluxo de trabalho** lista.</span><span class="sxs-lookup"><span data-stu-id="44b0e-114">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="44b0e-115">Tipo `NumberGuessWorkflowHost` para o **nome** caixa e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="44b0e-115">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="44b0e-116">Isso cria um aplicativo de fluxo de trabalho inicial com suporte básico de hospedagem de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="44b0e-116">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="44b0e-117">Esse código básico de hospedagem é modificado e usado para executar o aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="44b0e-117">This basic hosting code is modified and used to run the workflow application.</span></span>  
  
4.  <span data-ttu-id="44b0e-118">Clique com botão direito recém-adicionado **NumberGuessWorkflowHost** project no **Solution Explorer** e selecione **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="44b0e-118">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="44b0e-119">Selecione **solução** do **adicionar referência** lista, marque a caixa de seleção ao lado de **NumberGuessWorkflowActivities**e, em seguida, clique em **Okey** .</span><span class="sxs-lookup"><span data-stu-id="44b0e-119">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="44b0e-120">Clique com botão direito **Workflow1.xaml** na **Solution Explorer** e escolha **excluir**.</span><span class="sxs-lookup"><span data-stu-id="44b0e-120">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="44b0e-121">Clique em **Okey** para confirmar.</span><span class="sxs-lookup"><span data-stu-id="44b0e-121">Click **OK** to confirm.</span></span>  
  
### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="44b0e-122">Para modificar o código de hospedagem do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="44b0e-122">To modify the workflow hosting code</span></span>  
  
1.  <span data-ttu-id="44b0e-123">Clique duas vezes em **Program.cs** ou **Module1. vb** na **Solution Explorer** para exibir o código.</span><span class="sxs-lookup"><span data-stu-id="44b0e-123">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="44b0e-124">Se o **Solution Explorer** janela não for exibida, selecione **Solution Explorer** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="44b0e-124">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
     <span data-ttu-id="44b0e-125">Como este projeto foi criado usando o **aplicativo de Console do fluxo de trabalho** modelo, **Program.cs** ou **Module1. vb** contém o seguinte fluxo de trabalho básico hospedagem código.</span><span class="sxs-lookup"><span data-stu-id="44b0e-125">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>  
  
    ```vb  
    ' Create and cache the workflow definition  
    Activity workflow1 = new Workflow1()  
    WorkflowInvoker.Invoke(workflow1)  
    ```  
  
    ```csharp  
    // Create and cache the workflow definition  
    Activity workflow1 = new Workflow1();  
    WorkflowInvoker.Invoke(workflow1);  
    ```  
  
     <span data-ttu-id="44b0e-126">Esse código de hospedagem gerado usa <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="44b0e-126">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="44b0e-127"><xref:System.Activities.WorkflowInvoker> fornece uma maneira simples para chamar um fluxo de trabalho como se fosse uma chamada de método e pode ser usado somente para os fluxos de trabalho que não usam persistência.</span><span class="sxs-lookup"><span data-stu-id="44b0e-127"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="44b0e-128"><xref:System.Activities.WorkflowApplication> fornece um modelo mais avançado para executar fluxos de trabalho que incluem a notificação de eventos de ciclo de vida, o controle de execução, o reinício do indicador e a persistência.</span><span class="sxs-lookup"><span data-stu-id="44b0e-128"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="44b0e-129">Este exemplo usa indicadores e o <xref:System.Activities.WorkflowApplication> é usado para hospedar o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="44b0e-129">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="44b0e-130">Adicione o seguinte `using` ou **Imports** instrução na parte superior do **Program.cs** ou **Module1. vb** abaixo existente **usando** ou **Imports** instruções.</span><span class="sxs-lookup"><span data-stu-id="44b0e-130">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Threading  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Threading;  
    ```  
  
     <span data-ttu-id="44b0e-131">Substituir as linhas de código que usam <xref:System.Activities.WorkflowInvoker> com o código de hospedagem básica <xref:System.Activities.WorkflowApplication> a seguir.</span><span class="sxs-lookup"><span data-stu-id="44b0e-131">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="44b0e-132">Este código de hospedagem de exemplo demonstra as etapas básicas para hospedar e chamar um fluxo de trabalho, mas ainda não contém a funcionalidade para executar com êxito o fluxo de trabalho a partir deste tópico.</span><span class="sxs-lookup"><span data-stu-id="44b0e-132">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="44b0e-133">Nas etapas a seguir, esse código básico é modificado e os recursos adicionais são adicionados até que o aplicativo esteja concluído.</span><span class="sxs-lookup"><span data-stu-id="44b0e-133">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="44b0e-134">Substitua `Workflow1` nesses exemplos com `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, ou `StateMachineNumberGuessWorkflow`, dependendo de qual fluxo de trabalho concluída anteriormente na [como: criar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) etapa.</span><span class="sxs-lookup"><span data-stu-id="44b0e-134">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="44b0e-135">Se você não substituir `Workflow1`, receberá erros de compilação quando tentar criar ou executar o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="44b0e-135">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]  
  
     <span data-ttu-id="44b0e-136">Esse código cria um <xref:System.Activities.WorkflowApplication>, assina três eventos do ciclo de vida de fluxo de trabalho, inicia o fluxo de trabalho com uma chamada para <xref:System.Activities.WorkflowApplication.Run%2A> e aguarda que o fluxo de trabalho seja concluído.</span><span class="sxs-lookup"><span data-stu-id="44b0e-136">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="44b0e-137">Quando o fluxo de trabalho estiver concluído, o <xref:System.Threading.AutoResetEvent> é definido e o aplicativo host é concluído.</span><span class="sxs-lookup"><span data-stu-id="44b0e-137">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>  
  
### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="44b0e-138">Para definir argumentos de entrada de um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="44b0e-138">To set input arguments of a workflow</span></span>  
  
1.  <span data-ttu-id="44b0e-139">Adicione a seguinte instrução na parte superior do **Program.cs** ou **Module1. vb** abaixo existente `using` ou `Imports` instruções.</span><span class="sxs-lookup"><span data-stu-id="44b0e-139">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]  
  
2.  <span data-ttu-id="44b0e-140">Substitua a linha de código que cria uma nova <xref:System.Activities.WorkflowApplication> pelo código a seguir que cria e passa um dicionário dos parâmetros para o fluxo de trabalho quando ele é criado.</span><span class="sxs-lookup"><span data-stu-id="44b0e-140">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="44b0e-141">Substitua `Workflow1` nesses exemplos com `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, ou `StateMachineNumberGuessWorkflow`, dependendo de qual fluxo de trabalho concluída anteriormente na [como: criar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) etapa.</span><span class="sxs-lookup"><span data-stu-id="44b0e-141">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="44b0e-142">Se você não substituir `Workflow1`, receberá erros de compilação quando tentar criar ou executar o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="44b0e-142">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     <span data-ttu-id="44b0e-143">Este dicionário contém um elemento com uma chave `MaxNumber`.</span><span class="sxs-lookup"><span data-stu-id="44b0e-143">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="44b0e-144">As chaves do dicionário de entrada correspondem a argumentos de entrada na atividade raiz do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="44b0e-144">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="44b0e-145">`MaxNumber` é usado pelo fluxo de trabalho para determinar o limite superior para o número gerado aleatoriamente.</span><span class="sxs-lookup"><span data-stu-id="44b0e-145">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>  
  
### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="44b0e-146">Para recuperar argumentos de saída de um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="44b0e-146">To retrieve output arguments of a workflow</span></span>  
  
1.  <span data-ttu-id="44b0e-147">Modifique o manipulador <xref:System.Activities.WorkflowApplication.Completed%2A> para recuperar e exibir o número de sequências usadas pelo fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="44b0e-147">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#7](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]  
  
### <a name="to-resume-a-bookmark"></a><span data-ttu-id="44b0e-148">Para retomar um indicador</span><span class="sxs-lookup"><span data-stu-id="44b0e-148">To resume a bookmark</span></span>  
  
1.  <span data-ttu-id="44b0e-149">Adicione o código a seguir na parte superior do método `Main` imediatamente após a instrução <xref:System.Threading.AutoResetEvent> existente.</span><span class="sxs-lookup"><span data-stu-id="44b0e-149">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#8](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]  
  
2.  <span data-ttu-id="44b0e-150">Adicione o manipulador <xref:System.Activities.WorkflowApplication.Idle%2A> a seguir abaixo dos manipuladores existentes do ciclo de vida de fluxo de trabalho em `Main`.</span><span class="sxs-lookup"><span data-stu-id="44b0e-150">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#9](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]  
  
     <span data-ttu-id="44b0e-151">Cada vez que o fluxo de trabalho se torna ocioso aguardando a próxima estimativa, esse manipulador é chamado e o `idleAction` <xref:System.Threading.AutoResetEvent> está definido.</span><span class="sxs-lookup"><span data-stu-id="44b0e-151">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="44b0e-152">O código na etapa a seguir usa `idleEvent` e `syncEvent` para determinar se o fluxo de trabalho está esperando o próximo palpite ou está concluído.</span><span class="sxs-lookup"><span data-stu-id="44b0e-152">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="44b0e-153">Neste exemplo, o aplicativo host usa eventos de redefinição automática nos manipuladores <xref:System.Activities.WorkflowApplication.Completed%2A> e de <xref:System.Activities.WorkflowApplication.Idle%2A> para sincronizar o aplicativo host com o progresso do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="44b0e-153">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="44b0e-154">Não é necessário bloquear e esperar que o fluxo de trabalho fique inativo antes de retomar um indicador, mas, nesse exemplo, os eventos de sincronização são necessários para que o host saiba se o fluxo de trabalho está concluído ou se está aguardando mais entrada do usuário usando o <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="44b0e-154">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="44b0e-155">[Indicadores](../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="44b0e-155"> [Bookmarks](../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span></span>  
  
3.  <span data-ttu-id="44b0e-156">Remova a chamada para `WaitOne` e substitua-a pelo código para coletar entrada do usuário e retomar o <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="44b0e-156">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>  
  
     <span data-ttu-id="44b0e-157">Remova a seguinte linha de código.</span><span class="sxs-lookup"><span data-stu-id="44b0e-157">Remove the following line of code.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#10](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]  
  
     <span data-ttu-id="44b0e-158">Substitua-a pelo exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="44b0e-158">Replace it with the following example.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#11](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]  
  
##  <span data-ttu-id="44b0e-159"><a name="BKMK_ToRunTheApplication"></a>Para compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="44b0e-159"><a name="BKMK_ToRunTheApplication"></a> To build and run the application</span></span>  
  
1.  <span data-ttu-id="44b0e-160">Clique com botão direito **NumberGuessWorkflowHost** na **Solution Explorer** e selecione **definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="44b0e-160">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>  
  
2.  <span data-ttu-id="44b0e-161">Pressione CTRL+F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="44b0e-161">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="44b0e-162">Tente determinar o número no menor número de sequências possível.</span><span class="sxs-lookup"><span data-stu-id="44b0e-162">Try to guess the number in as few turns as possible.</span></span>  
  
     <span data-ttu-id="44b0e-163">Para testar o aplicativo com um dos outros estilos de fluxo de trabalho, substitua `Workflow1` no código que cria o <xref:System.Activities.WorkflowApplication> por `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow` ou `StateMachineNumberGuessWorkflow`, dependendo de qual estilo de fluxo de trabalho você deseja.</span><span class="sxs-lookup"><span data-stu-id="44b0e-163">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     <span data-ttu-id="44b0e-164">Para obter instruções sobre como adicionar a persistência de um aplicativo de fluxo de trabalho, consulte o próximo tópico, [como: criar e executar um fluxo de trabalho de execução longa](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="44b0e-164">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44b0e-165">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44b0e-165">Example</span></span>  
 <span data-ttu-id="44b0e-166">O exemplo a seguir é a listagem de código completa para o método `Main`.</span><span class="sxs-lookup"><span data-stu-id="44b0e-166">The following example is the complete code listing for the `Main` method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44b0e-167">Substitua `Workflow1` nesses exemplos com `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, ou `StateMachineNumberGuessWorkflow`, dependendo de qual fluxo de trabalho concluída anteriormente na [como: criar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) etapa.</span><span class="sxs-lookup"><span data-stu-id="44b0e-167">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="44b0e-168">Se você não substituir `Workflow1`, receberá erros de compilação quando tentar criar ou executar o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="44b0e-168">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>  
  
 [!code-csharp[CFX_WF_GettingStarted#12](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="44b0e-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44b0e-169">See Also</span></span>  
 <xref:System.Activities.WorkflowApplication>  
 <xref:System.Activities.Bookmark>  
 [<span data-ttu-id="44b0e-170">Programação do Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="44b0e-170">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="44b0e-171">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="44b0e-171">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="44b0e-172">Como criar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="44b0e-172">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [<span data-ttu-id="44b0e-173">Como criar e executar um fluxo de trabalho de execução longa</span><span class="sxs-lookup"><span data-stu-id="44b0e-173">How to: Create and Run a Long Running Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)  
 [<span data-ttu-id="44b0e-174">Esperando entrada em um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="44b0e-174">Waiting for Input in a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/waiting-for-input-in-a-workflow.md)  
 [<span data-ttu-id="44b0e-175">Hospedando fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="44b0e-175">Hosting Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/hosting-workflows.md)