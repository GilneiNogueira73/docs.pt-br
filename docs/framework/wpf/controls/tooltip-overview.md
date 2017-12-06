---
title: "Visão geral de ToolTip"
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
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31bd56323e90368f850ae54854e6f50b63d5f7fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-overview"></a><span data-ttu-id="6cf45-102">Visão geral de ToolTip</span><span class="sxs-lookup"><span data-stu-id="6cf45-102">ToolTip Overview</span></span>
<span data-ttu-id="6cf45-103">Uma dica de ferramenta é uma pequena janela pop-up que aparece quando um usuário pausa o ponteiro do mouse sobre um elemento, tal como em um <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="6cf45-103">A tooltip is a small pop-up window that appears when a user pauses the mouse pointer over an element, such as over a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="6cf45-104">Este tópico apresenta a dica de ferramenta e discute como criar e personalizar o conteúdo da dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="6cf45-104">This topic introduces the tooltip and discusses how to create and customize tooltip content.</span></span>  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a><span data-ttu-id="6cf45-105">O que é uma dica de ferramenta?</span><span class="sxs-lookup"><span data-stu-id="6cf45-105">What Is a Tooltip?</span></span>  
 <span data-ttu-id="6cf45-106">Quando um usuário move o ponteiro do mouse sobre um elemento que tem uma dica de ferramenta, aparecerá uma janela com conteúdo da dica de ferramenta (por exemplo, conteúdo de texto que descreve a função de um controle) por um período especificado.</span><span class="sxs-lookup"><span data-stu-id="6cf45-106">When a user moves the mouse pointer over an element that has a tooltip, a window that contains tooltip content (for example, text content that describes the function of a control) appears for a specified amount of time.</span></span> <span data-ttu-id="6cf45-107">Se o usuário mover o ponteiro do mouse para fora do controle, a janela desaparecerá, pois o conteúdo da dica de ferramenta não poderá receber foco.</span><span class="sxs-lookup"><span data-stu-id="6cf45-107">If the user moves the mouse pointer away from the control, the window disappears because the tooltip content cannot receive focus.</span></span>  
  
 <span data-ttu-id="6cf45-108">O conteúdo de uma dica de ferramenta pode conter uma ou mais linhas de texto, imagens, formas ou outros conteúdos visuais.</span><span class="sxs-lookup"><span data-stu-id="6cf45-108">The content of a tooltip can contain one or more lines of text, images, shapes, or other visual content.</span></span> <span data-ttu-id="6cf45-109">Você define uma dica de ferramenta para um controle definindo uma das seguintes propriedades para o conteúdo da dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="6cf45-109">You define a tooltip for a control by setting one of the following properties to the tooltip content.</span></span>  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="6cf45-110">Qual propriedade que você usa depende se o controle que define a dica de ferramenta herda o <xref:System.Windows.FrameworkContentElement> ou <xref:System.Windows.FrameworkElement> classe.</span><span class="sxs-lookup"><span data-stu-id="6cf45-110">Which property you use depends on whether the control that defines the tooltip inherits from the <xref:System.Windows.FrameworkContentElement> or <xref:System.Windows.FrameworkElement> class.</span></span>  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a><span data-ttu-id="6cf45-111">Criando uma ToolTip</span><span class="sxs-lookup"><span data-stu-id="6cf45-111">Creating a ToolTip</span></span>  
 <span data-ttu-id="6cf45-112">O exemplo a seguir mostra como criar uma dica de ferramenta simple, definindo o <xref:System.Windows.FrameworkElement.ToolTip%2A> propriedade para um <xref:System.Windows.Controls.Button> controle em uma cadeia de caracteres de texto.</span><span class="sxs-lookup"><span data-stu-id="6cf45-112">The following example shows how to create a simple tooltip by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A> property for a <xref:System.Windows.Controls.Button> control to a text string.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 <span data-ttu-id="6cf45-113">Você também pode definir uma dica de ferramenta como um <xref:System.Windows.Controls.ToolTip> objeto.</span><span class="sxs-lookup"><span data-stu-id="6cf45-113">You can also define a tooltip as a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="6cf45-114">O exemplo a seguir usa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para especificar um <xref:System.Windows.Controls.ToolTip> objeto como dica de ferramenta de um <xref:System.Windows.Controls.TextBox> elemento.</span><span class="sxs-lookup"><span data-stu-id="6cf45-114">The following example uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to specify a <xref:System.Windows.Controls.ToolTip> object as the tooltip of a <xref:System.Windows.Controls.TextBox> element.</span></span> <span data-ttu-id="6cf45-115">Observe que o exemplo especifica o <xref:System.Windows.Controls.ToolTip> definindo o <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="6cf45-115">Note that the example specifies the <xref:System.Windows.Controls.ToolTip> by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 <span data-ttu-id="6cf45-116">O exemplo a seguir usa o código para gerar um <xref:System.Windows.Controls.ToolTip> objeto.</span><span class="sxs-lookup"><span data-stu-id="6cf45-116">The following example uses code to generate a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="6cf45-117">O exemplo cria um <xref:System.Windows.Controls.ToolTip> (`tt`) e o associa um <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="6cf45-117">The example creates a <xref:System.Windows.Controls.ToolTip> (`tt`) and associates it with a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 <span data-ttu-id="6cf45-118">Você também pode criar conteúdo de dica de ferramenta que não está definido como um <xref:System.Windows.Controls.ToolTip> objeto colocando o conteúdo da dica de ferramenta em um elemento de layout, como um <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="6cf45-118">You can also create tooltip content that is not defined as a <xref:System.Windows.Controls.ToolTip> object by enclosing the tooltip content in a layout element, such as a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="6cf45-119">O exemplo a seguir mostra como definir o <xref:System.Windows.FrameworkElement.ToolTip%2A> propriedade de um <xref:System.Windows.Controls.TextBox> ao conteúdo que está contido em um <xref:System.Windows.Controls.DockPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="6cf45-119">The following example shows how to set the <xref:System.Windows.FrameworkElement.ToolTip%2A> property of a <xref:System.Windows.Controls.TextBox> to content that is enclosed in a <xref:System.Windows.Controls.DockPanel> control.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a><span data-ttu-id="6cf45-120">Usando as propriedades das classes ToolTip e ToolTipService</span><span class="sxs-lookup"><span data-stu-id="6cf45-120">Using the Properties of the ToolTip and ToolTipService Classes</span></span>  
 <span data-ttu-id="6cf45-121">Você pode personalizar o conteúdo da dica de ferramenta definindo propriedades visuais e aplicando estilos.</span><span class="sxs-lookup"><span data-stu-id="6cf45-121">You can customize tooltip content by setting visual properties and applying styles.</span></span> <span data-ttu-id="6cf45-122">Se você definir a dica de ferramenta com conteúdo como um <xref:System.Windows.Controls.ToolTip> do objeto, você pode definir as propriedades visuais do <xref:System.Windows.Controls.ToolTip> objeto.</span><span class="sxs-lookup"><span data-stu-id="6cf45-122">If you define the tooltip content as a <xref:System.Windows.Controls.ToolTip> object, you can set the visual properties of the <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="6cf45-123">Caso contrário, você deve definir propriedades anexadas equivalentes no <xref:System.Windows.Controls.ToolTipService> classe.</span><span class="sxs-lookup"><span data-stu-id="6cf45-123">Otherwise, you must set equivalent attached properties on the <xref:System.Windows.Controls.ToolTipService> class.</span></span>  
  
 <span data-ttu-id="6cf45-124">Para obter um exemplo de como definir propriedades para especificar a posição do conteúdo da dica de ferramenta usando o <xref:System.Windows.Controls.ToolTip> e <xref:System.Windows.Controls.ToolTipService> propriedades, consulte [posicionar uma dica de ferramenta](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).</span><span class="sxs-lookup"><span data-stu-id="6cf45-124">For an example of how to set properties in order to specify the position of tooltip content by using the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> properties, see [Position a ToolTip](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).</span></span>  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a><span data-ttu-id="6cf45-125">Definindo o estilo de uma ToolTip</span><span class="sxs-lookup"><span data-stu-id="6cf45-125">Styling a ToolTip</span></span>  
 <span data-ttu-id="6cf45-126">Você pode estilizar um <xref:System.Windows.Controls.ToolTip> definindo um personalizado <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="6cf45-126">You can style a <xref:System.Windows.Controls.ToolTip> by defining a custom <xref:System.Windows.Style>.</span></span> <span data-ttu-id="6cf45-127">O exemplo a seguir define uma <xref:System.Windows.Style> chamado `Simple` que mostra como deslocar o posicionamento do <xref:System.Windows.Controls.ToolTip> e alterar sua aparência, definindo o <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, e <xref:System.Windows.Controls.Control.FontWeight%2A>.</span><span class="sxs-lookup"><span data-stu-id="6cf45-127">The following example defines a <xref:System.Windows.Style> called `Simple` that shows how to offset the placement of the <xref:System.Windows.Controls.ToolTip> and change its appearance by setting the <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, and <xref:System.Windows.Controls.Control.FontWeight%2A>.</span></span>  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a><span data-ttu-id="6cf45-128">Usando as propriedades Intervalo de Tempo de ToolTipService</span><span class="sxs-lookup"><span data-stu-id="6cf45-128">Using the Time Interval Properties of ToolTipService</span></span>  
 <span data-ttu-id="6cf45-129">O <xref:System.Windows.Controls.ToolTipService> classe fornece as seguintes propriedades para definir a dica de ferramenta exibem tempos: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, e <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span><span class="sxs-lookup"><span data-stu-id="6cf45-129">The <xref:System.Windows.Controls.ToolTipService> class provides the following properties for you to set tooltip display times: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span></span>  
  
 <span data-ttu-id="6cf45-130">Use o <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> e <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> propriedades para especificar um intervalo, normalmente breve, antes um <xref:System.Windows.Controls.ToolTip> aparece e também para especificar por quanto tempo um <xref:System.Windows.Controls.ToolTip> permanece visível.</span><span class="sxs-lookup"><span data-stu-id="6cf45-130">Use the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> properties to specify a delay, typically brief, before a <xref:System.Windows.Controls.ToolTip> appears and also to specify how long a <xref:System.Windows.Controls.ToolTip> remains visible.</span></span> <span data-ttu-id="6cf45-131">Para obter mais informações, consulte [Como adiar a exibição de uma ToolTip](http://msdn.microsoft.com/en-us/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).</span><span class="sxs-lookup"><span data-stu-id="6cf45-131">For more information, see [How to: Delay the Display of a ToolTip](http://msdn.microsoft.com/en-us/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).</span></span>  
  
 <span data-ttu-id="6cf45-132">O <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> propriedade determina se as dicas de ferramentas para controles diferentes aparecem sem um atraso inicial quando você move o ponteiro do mouse rapidamente entre eles.</span><span class="sxs-lookup"><span data-stu-id="6cf45-132">The <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property determines if tooltips for different controls appear without an initial delay when you move the mouse pointer quickly between them.</span></span> <span data-ttu-id="6cf45-133">Para obter mais informações sobre o <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> propriedade, consulte [usar a propriedade BetweenShowDelay](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).</span><span class="sxs-lookup"><span data-stu-id="6cf45-133">For more information about the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property, see [Use the BetweenShowDelay Property](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).</span></span>  
  
 <span data-ttu-id="6cf45-134">O exemplo a seguir mostra como definir essas propriedades para uma dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="6cf45-134">The following example shows how to set these properties for a tooltip.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="6cf45-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cf45-135">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTipService>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipEventArgs>  
 <xref:System.Windows.Controls.ToolTipEventHandler>  
 [<span data-ttu-id="6cf45-136">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="6cf45-136">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)