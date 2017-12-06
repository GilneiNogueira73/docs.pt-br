---
title: Como criar uma atividade
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
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26385d91b4201820a5f6ba77b512e7bcfd5372c3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="29ebb-102">Como criar uma atividade</span><span class="sxs-lookup"><span data-stu-id="29ebb-102">How to: Create an Activity</span></span>
<span data-ttu-id="29ebb-103">As atividades são a unidade principal de comportamento no [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="29ebb-103">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="29ebb-104">A lógica de execução de uma atividade pode ser implementada em código gerenciado ou pode ser implementada usando outras atividades.</span><span class="sxs-lookup"><span data-stu-id="29ebb-104">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="29ebb-105">Este tópico demonstra como criar duas atividades.</span><span class="sxs-lookup"><span data-stu-id="29ebb-105">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="29ebb-106">A primeira atividade é uma atividade simples que usa o código para implementar a sua lógica de execução.</span><span class="sxs-lookup"><span data-stu-id="29ebb-106">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="29ebb-107">A implementação da segunda atividade é definida usando outras atividades.</span><span class="sxs-lookup"><span data-stu-id="29ebb-107">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="29ebb-108">Essas atividades são usadas nas seguintes etapas no tutorial.</span><span class="sxs-lookup"><span data-stu-id="29ebb-108">These activities are used in following steps in the tutorial.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29ebb-109">Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="29ebb-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-activity-library-project"></a><span data-ttu-id="29ebb-110">Para criar o projeto de biblioteca de atividade</span><span class="sxs-lookup"><span data-stu-id="29ebb-110">To create the activity library project</span></span>  
  
1.  <span data-ttu-id="29ebb-111">Abra [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] e escolha **novo**, **projeto** do **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="29ebb-111">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and choose **New**,  **Project** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="29ebb-112">Expanda o **outros tipos de projetos** nó o **instalado**, **modelos** e selecione **soluções do Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="29ebb-112">Expand the **Other Project Types** node in the **Installed**, **Templates** list and select **Visual Studio Solutions**.</span></span>  
  
3.  <span data-ttu-id="29ebb-113">Selecione **solução em branco** do **soluções do Visual Studio** lista.</span><span class="sxs-lookup"><span data-stu-id="29ebb-113">Select **Blank Solution** from the **Visual Studio Solutions** list.</span></span> <span data-ttu-id="29ebb-114">Certifique-se de que **.NET Framework 4.5** está selecionado na lista suspensa de versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29ebb-114">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="29ebb-115">Tipo `WF45GettingStartedTutorial` no **nome** caixa e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="29ebb-115">Type `WF45GettingStartedTutorial` in the **Name** box and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="29ebb-116">Clique com botão direito **WF45GettingStartedTutorial** na **Solution Explorer** e escolha **adicionar**, **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="29ebb-116">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="29ebb-117">Se o **Solution Explorer** janela não for exibida, selecione **Solution Explorer** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="29ebb-117">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="29ebb-118">No **instalado** nó, selecione **Visual C#**, **fluxo de trabalho** (ou **Visual Basic**, **fluxo de trabalho**).</span><span class="sxs-lookup"><span data-stu-id="29ebb-118">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span> <span data-ttu-id="29ebb-119">Certifique-se de que **.NET Framework 4.5** está selecionado no [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] lista suspensa de versão.</span><span class="sxs-lookup"><span data-stu-id="29ebb-119">Ensure that **.NET Framework 4.5** is selected in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version drop-down list.</span></span> <span data-ttu-id="29ebb-120">Selecione **biblioteca de atividades** do **fluxo de trabalho** lista.</span><span class="sxs-lookup"><span data-stu-id="29ebb-120">Select **Activity Library** from the **Workflow** list.</span></span> <span data-ttu-id="29ebb-121">Tipo `NumberGuessWorkflowActivities` no **nome** caixa e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="29ebb-121">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29ebb-122">Dependendo da linguagem de programação que é configurada como linguagem primária no [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], o **Visual C#** ou **Visual Basic** nó pode estar sob o **outras linguagens**nó o **instalado** nó.</span><span class="sxs-lookup"><span data-stu-id="29ebb-122">Depending on which programming language is configured as the primary language in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
6.  <span data-ttu-id="29ebb-123">Clique com botão direito **activity1** na **Solution Explorer** e escolha **excluir**.</span><span class="sxs-lookup"><span data-stu-id="29ebb-123">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="29ebb-124">Clique em **Okey** para confirmar.</span><span class="sxs-lookup"><span data-stu-id="29ebb-124">Click **OK** to confirm.</span></span>  
  
### <a name="to-create-the-readint-activity"></a><span data-ttu-id="29ebb-125">Para criar a atividade de ReadInt</span><span class="sxs-lookup"><span data-stu-id="29ebb-125">To create the ReadInt activity</span></span>  
  
1.  <span data-ttu-id="29ebb-126">Escolha **Adicionar Novo Item** do **projeto** menu.</span><span class="sxs-lookup"><span data-stu-id="29ebb-126">Choose **Add New Item** from the **Project** menu.</span></span>  
  
2.  <span data-ttu-id="29ebb-127">No **instalado**, **itens comuns** nó, selecione **fluxo de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="29ebb-127">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="29ebb-128">Selecione **atividade de código** do **fluxo de trabalho** lista.</span><span class="sxs-lookup"><span data-stu-id="29ebb-128">Select **Code Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="29ebb-129">Tipo `ReadInt` para o **nome** caixa e, em seguida, clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="29ebb-129">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="29ebb-130">Substitua a definição existente de `ReadInt` pela seguinte definição.</span><span class="sxs-lookup"><span data-stu-id="29ebb-130">Replace the existing `ReadInt` definition with the following definition.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="29ebb-131">A atividade `ReadInt` é derivada de <xref:System.Activities.NativeActivity%601> em vez de <xref:System.Activities.CodeActivity>, que é o padrão para o modelo de atividade de código.</span><span class="sxs-lookup"><span data-stu-id="29ebb-131">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="29ebb-132"><xref:System.Activities.CodeActivity%601> poderá ser usado se a atividade fornecer um único resultado, que é exposto através do argumento <xref:System.Activities.Activity%601.Result%2A>, mas <xref:System.Activities.CodeActivity%601> não oferece suporte ao uso de indicadores, portanto <xref:System.Activities.NativeActivity%601> será usado.</span><span class="sxs-lookup"><span data-stu-id="29ebb-132"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>  
  
### <a name="to-create-the-prompt-activity"></a><span data-ttu-id="29ebb-133">Para criar a atividade de Prompt</span><span class="sxs-lookup"><span data-stu-id="29ebb-133">To create the Prompt activity</span></span>  
  
1.  <span data-ttu-id="29ebb-134">Pressione CTRL+SHIFT+B para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="29ebb-134">Press CTRL+SHIFT+B to build the project.</span></span> <span data-ttu-id="29ebb-135">Compilar o projeto permite que a atividade `ReadInt` neste projeto seja usada para criar a atividade personalizada dessa etapa.</span><span class="sxs-lookup"><span data-stu-id="29ebb-135">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>  
  
2.  <span data-ttu-id="29ebb-136">Escolha **Adicionar Novo Item** do **projeto** menu.</span><span class="sxs-lookup"><span data-stu-id="29ebb-136">Choose **Add New Item** from the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="29ebb-137">No **instalado**, **itens comuns** nó, selecione **fluxo de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="29ebb-137">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="29ebb-138">Selecione **atividade** do **fluxo de trabalho** lista.</span><span class="sxs-lookup"><span data-stu-id="29ebb-138">Select **Activity** from the **Workflow** list.</span></span>  
  
4.  <span data-ttu-id="29ebb-139">Tipo `Prompt` para o **nome** caixa e, em seguida, clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="29ebb-139">Type `Prompt` into the **Name** box and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="29ebb-140">Clique duas vezes em **Prompt.xaml** na **Solution Explorer** para exibi-lo no designer caso ainda não esteja sendo exibido.</span><span class="sxs-lookup"><span data-stu-id="29ebb-140">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>  
  
6.  <span data-ttu-id="29ebb-141">Clique em **argumentos** no lado inferior esquerdo do designer de atividade para exibir o **argumentos** painel.</span><span class="sxs-lookup"><span data-stu-id="29ebb-141">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>  
  
7.  <span data-ttu-id="29ebb-142">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="29ebb-142">Click **Create Argument**.</span></span>  
  
8.  <span data-ttu-id="29ebb-143">Tipo `BookmarkName` no **nome** caixa, selecione **na** do **direção** lista suspensa, selecione **cadeia de caracteres** da **Tipo de argumento** lista suspensa e, em seguida, pressione ENTER para salvar o argumento.</span><span class="sxs-lookup"><span data-stu-id="29ebb-143">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
9. <span data-ttu-id="29ebb-144">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="29ebb-144">Click **Create Argument**.</span></span>  
  
10. <span data-ttu-id="29ebb-145">Tipo `Result` para o **nome** caixa sob recém-adicionado `BookmarkName` argumento, selecione **Out** do **direção** lista suspensa, selecione **Int32** do **tipo de argumento** lista suspensa e, em seguida, pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="29ebb-145">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
11. <span data-ttu-id="29ebb-146">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="29ebb-146">Click **Create Argument**.</span></span>  
  
12. <span data-ttu-id="29ebb-147">Tipo `Text` no **nome** caixa, selecione **na** do **direção** lista suspensa, selecione **cadeia de caracteres** da **Tipo de argumento** lista suspensa e, em seguida, pressione ENTER para salvar o argumento.</span><span class="sxs-lookup"><span data-stu-id="29ebb-147">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
     <span data-ttu-id="29ebb-148">Esses três argumentos são associados aos argumentos correspondentes das atividades <xref:System.Activities.Statements.WriteLine> e `ReadInt` que são adicionadas à atividade `Prompt` nas seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="29ebb-148">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>  
  
13. <span data-ttu-id="29ebb-149">Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o **argumentos** painel.</span><span class="sxs-lookup"><span data-stu-id="29ebb-149">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
14. <span data-ttu-id="29ebb-150">Arraste um **sequência** atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-a para o **descartar atividade aqui** rótulo da **Prompt** designer de atividade.</span><span class="sxs-lookup"><span data-stu-id="29ebb-150">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="29ebb-151">Se o **caixa de ferramentas** janela não for exibida, selecione **caixa de ferramentas** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="29ebb-151">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
15. <span data-ttu-id="29ebb-152">Arraste um **WriteLine** atividade do **primitivos** seção o **caixa de ferramentas** e solte-a para o **descartar atividade aqui** rótulo da **Sequência** atividade.</span><span class="sxs-lookup"><span data-stu-id="29ebb-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>  
  
16. <span data-ttu-id="29ebb-153">Associar o **texto** argumento do **WriteLine** atividade para o **texto** argumento do **Prompt** atividade digitando `Text` para o **insira uma expressão de c#** ou **insira uma expressão VB** caixa o **propriedades** janela e, em seguida, pressione a guia chave duas vezes.</span><span class="sxs-lookup"><span data-stu-id="29ebb-153">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the TAB key two times.</span></span> <span data-ttu-id="29ebb-154">Isso fecha a janela dos membros da lista do IntelliSense e salva o valor da propriedade removendo a seleção da propriedade.</span><span class="sxs-lookup"><span data-stu-id="29ebb-154">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="29ebb-155">Essa propriedade também pode ser definida digitando `Text` para o **insira uma expressão de c#** ou **insira uma expressão VB** caixa sobre a atividade em si.</span><span class="sxs-lookup"><span data-stu-id="29ebb-155">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="29ebb-156">Se o **janela propriedades** não é exibida, selecione **janela propriedades** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="29ebb-156">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
17. <span data-ttu-id="29ebb-157">Arraste um **ReadInt** atividade do **NumberGuessWorkflowActivities** seção o **caixa de ferramentas** e solte-o no **sequência** atividade para que ela siga a **WriteLine** atividade.</span><span class="sxs-lookup"><span data-stu-id="29ebb-157">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>  
  
18. <span data-ttu-id="29ebb-158">Associar o **BookmarkName** argumento do **ReadInt** atividade para o **BookmarkName** argumento do **Prompt** atividade digitando `BookmarkName` no **insira uma expressão VB** caixa à direita do **BookmarkName** argumento o **janela propriedades**e, em seguida, pressione a tecla TAB duas vezes para fechar a janela de membros de lista do IntelliSense e salvar a propriedade.</span><span class="sxs-lookup"><span data-stu-id="29ebb-158">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the TAB key two times to close the IntelliSense list members window and save the property.</span></span>  
  
19. <span data-ttu-id="29ebb-159">Associar o **resultados** argumento do **ReadInt** atividade para o **resultados** argumento do **Prompt** atividade digitando `Result` no **insira uma expressão VB** caixa à direita do **resultados** argumento no **janela propriedades**e, em seguida, pressione a tecla TAB duas vezes.</span><span class="sxs-lookup"><span data-stu-id="29ebb-159">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the TAB key two times.</span></span>  
  
20. <span data-ttu-id="29ebb-160">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="29ebb-160">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="29ebb-161">Para obter instruções sobre como criar um fluxo de trabalho com essas atividades, consulte a próxima etapa no tutorial, [como: criar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="29ebb-161">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ebb-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29ebb-162">See Also</span></span>  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [<span data-ttu-id="29ebb-163">Criando e implementando atividades personalizadas</span><span class="sxs-lookup"><span data-stu-id="29ebb-163">Designing and Implementing Custom Activities</span></span>](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [<span data-ttu-id="29ebb-164">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="29ebb-164">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="29ebb-165">Como criar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="29ebb-165">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [<span data-ttu-id="29ebb-166">Usando o ExpressionTextBox em um Designer de atividade personalizada</span><span class="sxs-lookup"><span data-stu-id="29ebb-166">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)