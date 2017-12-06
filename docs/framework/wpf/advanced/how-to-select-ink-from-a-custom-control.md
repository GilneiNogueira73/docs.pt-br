---
title: Como selecionar tinta em um controle personalizado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd9693209cc35ecd3c0473133b7c21639a239ff5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-select-ink-from-a-custom-control"></a><span data-ttu-id="fdc3a-102">Como selecionar tinta em um controle personalizado</span><span class="sxs-lookup"><span data-stu-id="fdc3a-102">How to: Select Ink from a Custom Control</span></span>
<span data-ttu-id="fdc3a-103">Adicionando um <xref:System.Windows.Ink.IncrementalLassoHitTester> para o controle personalizado, você pode habilitar o controle para que um usuário possa selecionar ink com a ferramenta de Laço, semelhante à forma como o <xref:System.Windows.Controls.InkCanvas> seleciona ink com um laço.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-103">By adding an <xref:System.Windows.Ink.IncrementalLassoHitTester> to your custom control, you can enable your control so that a user can select ink with a lasso tool, similar to the way the <xref:System.Windows.Controls.InkCanvas> selects ink with a lasso.</span></span>  
  
 <span data-ttu-id="fdc3a-104">Este exemplo pressupõe que você esteja familiarizado com a criação de um controle personalizado habilitado para tinta.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-104">This example assumes you are familiar with creating an ink-enabled custom control.</span></span>  <span data-ttu-id="fdc3a-105">Para criar um controle personalizado que aceite entrada de tinta, consulte [Criando um controle de entrada de tinta](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span><span class="sxs-lookup"><span data-stu-id="fdc3a-105">To create a custom control that accepts ink input, see [Creating an Ink Input Control](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdc3a-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fdc3a-106">Example</span></span>  
 <span data-ttu-id="fdc3a-107">Quando o usuário desenha um laço, o <xref:System.Windows.Ink.IncrementalLassoHitTester> prevê quais traços estarão dentro do laço após o usuário completá-lo.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-107">When the user draws a lasso, the <xref:System.Windows.Ink.IncrementalLassoHitTester> predicts which strokes will be within the lasso path's boundaries after the user completes the lasso.</span></span>  <span data-ttu-id="fdc3a-108">Traços determinados como estando dentro dos limites do caminho do laço podem ser pensados como selecionados.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-108">Strokes that are determined to be within the lasso path's boundaries can be thought of as being selected.</span></span>  <span data-ttu-id="fdc3a-109">Traços selecionados também podem se tornar não selecionados.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-109">Selected strokes can also become unselected.</span></span>  <span data-ttu-id="fdc3a-110">Por exemplo, se o usuário inverter a direção enquanto desenha o laço, o <xref:System.Windows.Ink.IncrementalLassoHitTester> pode selecionar alguns traços.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-110">For example, if the user reverses direction while drawing the lasso, the <xref:System.Windows.Ink.IncrementalLassoHitTester> may unselect some strokes.</span></span>  
  
 <span data-ttu-id="fdc3a-111">O <xref:System.Windows.Ink.IncrementalLassoHitTester> gera o <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> evento, que permite que o controle personalizado a responder enquanto o usuário está desenhando o laço.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-111">The <xref:System.Windows.Ink.IncrementalLassoHitTester> raises the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event, which enables your custom control to respond while the user is drawing the lasso.</span></span>  <span data-ttu-id="fdc3a-112">Por exemplo, você pode alterar a aparência dos traços conforme o usuário os marca e desmarca.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-112">For example, you can change the appearance of strokes as the user selects and unselects them.</span></span>  
  
## <a name="managing-the-ink-mode"></a><span data-ttu-id="fdc3a-113">Gerenciando o modo de tinta</span><span class="sxs-lookup"><span data-stu-id="fdc3a-113">Managing the Ink Mode</span></span>  
 <span data-ttu-id="fdc3a-114">É útil para o usuário que o laço apareça de modo diferente da tinta no seu controle.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-114">It is helpful to the user if the lasso appears differently than the ink on your control.</span></span> <span data-ttu-id="fdc3a-115">Para fazer isso, seu controle personalizado deve controlar de se o usuário está escrevendo ou selecionando tinta.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-115">To accomplish this, your custom control must keep track of whether the user is writing or selecting ink.</span></span> <span data-ttu-id="fdc3a-116">A maneira mais fácil de fazer isso é declarar uma enumeração com dois valores: um para indicar que o usuário está escrevendo tinta e outro para indicar que o usuário está selecionando tinta.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-116">The easiest way to do this is to declare an enumeration with two values: one to indicate that the user is writing ink and one to indicate that the user is selecting ink.</span></span>  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 <span data-ttu-id="fdc3a-117">Em seguida, adicione dois <xref:System.Windows.Ink.DrawingAttributes> à classe: um para utilizar quando o usuário escreve ink, um para utilizar quando o usuário seleciona ink.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-117">Next, add two <xref:System.Windows.Ink.DrawingAttributes> to the class: one to use when the user writes ink, one to use when the user selects ink.</span></span>  <span data-ttu-id="fdc3a-118">No construtor, inicialize o <xref:System.Windows.Ink.DrawingAttributes> e anexe ambos <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> eventos ao mesmo manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-118">In the constructor, initialize the <xref:System.Windows.Ink.DrawingAttributes> and attach both <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> events to the same event handler.</span></span> <span data-ttu-id="fdc3a-119">Em seguida, defina o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> propriedade o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> à tinta <xref:System.Windows.Ink.DrawingAttributes>.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-119">Then set the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> property of the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the ink <xref:System.Windows.Ink.DrawingAttributes>.</span></span>  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 <span data-ttu-id="fdc3a-120">Adicione uma propriedade que exponha o modo de seleção.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-120">Add a property that exposes the selection mode.</span></span> <span data-ttu-id="fdc3a-121">Quando o usuário altera o modo de seleção, defina o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> propriedade do <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ao apropriado <xref:System.Windows.Ink.DrawingAttributes> do objeto e, em seguida, anexe o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> propriedade para o <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-121">When the user changes the selection mode, set the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> property of the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the appropriate <xref:System.Windows.Ink.DrawingAttributes> object and then reattach the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> Property to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 <span data-ttu-id="fdc3a-122">Expor o <xref:System.Windows.Ink.DrawingAttributes> como propriedades para aplicativos possam determinar a aparência de traços de tinta e seleção.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-122">Expose the <xref:System.Windows.Ink.DrawingAttributes> as properties so applications can determine the appearance of the ink strokes and selection strokes.</span></span>  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 <span data-ttu-id="fdc3a-123">Quando uma propriedade de um <xref:System.Windows.Ink.DrawingAttributes> objeto alterações, o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> deve ser anexado novamente para o <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-123">When a property of a <xref:System.Windows.Ink.DrawingAttributes> object changes, the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> must be reattached to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  <span data-ttu-id="fdc3a-124">No manipulador de eventos para o <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> eventos, anexar novamente o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> para o <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-124">In the event handler for the <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> event, reattach the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a><span data-ttu-id="fdc3a-125">Usando o IncrementalLassoHitTester</span><span class="sxs-lookup"><span data-stu-id="fdc3a-125">Using the IncrementalLassoHitTester</span></span>  
 <span data-ttu-id="fdc3a-126">Criar e inicializar um <xref:System.Windows.Ink.StrokeCollection> que contém os traços selecionados.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-126">Create and initialize a <xref:System.Windows.Ink.StrokeCollection> that contains the selected strokes.</span></span>  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 <span data-ttu-id="fdc3a-127">Quando o usuário começa a desenhar um traço, seja com tinta ou laço, desmarque quaisquer traços selecionados.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-127">When the user starts to draw a stroke, either ink or the lasso, unselect any selected strokes.</span></span> <span data-ttu-id="fdc3a-128">Em seguida, se o usuário estiver desenhando um laço, crie um <xref:System.Windows.Ink.IncrementalLassoHitTester> chamando <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, assinar o <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> eventos e chamadas <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-128">Then, if the user is drawing a lasso, create an <xref:System.Windows.Ink.IncrementalLassoHitTester> by calling <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, subscribe to the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event, and call <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>.</span></span> <span data-ttu-id="fdc3a-129">Esse código pode ser um método separado e chamado a partir de <xref:System.Windows.UIElement.OnStylusDown%2A> e <xref:System.Windows.UIElement.OnMouseDown%2A> métodos.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-129">This code can be a separate method and called from the <xref:System.Windows.UIElement.OnStylusDown%2A> and <xref:System.Windows.UIElement.OnMouseDown%2A> methods.</span></span>  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 <span data-ttu-id="fdc3a-130">Adicione os pontos de caneta para o <xref:System.Windows.Ink.IncrementalLassoHitTester> enquanto o usuário desenha o laço.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-130">Add the stylus points to the <xref:System.Windows.Ink.IncrementalLassoHitTester> while the user draws the lasso.</span></span>  <span data-ttu-id="fdc3a-131">Chamar o método seguinte a partir de <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, e <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> métodos.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-131">Call the following method from the <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, and <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> methods.</span></span>  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 <span data-ttu-id="fdc3a-132">Manipular o <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> evento para responder quando o usuário seleciona e desmarca traços.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-132">Handle the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> event to respond when the user selects and unselects strokes.</span></span>  <span data-ttu-id="fdc3a-133">O <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> classe tem o <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> e <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> propriedades que pegam os traços que foram selecionadas e desmarcadas, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-133">The <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> class has the <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> and <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> properties that get the strokes that were selected and unselected, respectively.</span></span>  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 <span data-ttu-id="fdc3a-134">Quando o usuário termina de desenhar o laço, cancelar a inscrição a <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> eventos e chamadas <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-134">When the user finishes drawing the lasso, unsubscribe from the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event and call <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.</span></span>  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a><span data-ttu-id="fdc3a-135">Juntando as peças.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-135">Putting it All Together.</span></span>  
 <span data-ttu-id="fdc3a-136">O exemplo a seguir é um controle personalizado que permite que um usuário selecione tinta com um laço.</span><span class="sxs-lookup"><span data-stu-id="fdc3a-136">The following example is a custom control that enables a user to select ink with a lasso.</span></span>  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fdc3a-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fdc3a-137">See Also</span></span>  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>  
 <xref:System.Windows.Ink.StrokeCollection>  
 <xref:System.Windows.Input.StylusPointCollection>  
 [<span data-ttu-id="fdc3a-138">Criando um controle de entrada de tinta</span><span class="sxs-lookup"><span data-stu-id="fdc3a-138">Creating an Ink Input Control</span></span>](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)