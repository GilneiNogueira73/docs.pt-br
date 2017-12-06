---
title: "Controles com suporte de desenho do proprietário interno"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8fb699a93effcdf0b5f88606419479d51754125b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="controls-with-built-in-owner-drawing-support"></a><span data-ttu-id="1cda7-102">Controles com suporte de desenho do proprietário interno</span><span class="sxs-lookup"><span data-stu-id="1cda7-102">Controls with Built-In Owner-Drawing Support</span></span>
<span data-ttu-id="1cda7-103">Proprietário do desenho nos Windows Forms, que é também conhecido como desenho personalizado, é uma técnica para alterar a aparência visual de certos controles.</span><span class="sxs-lookup"><span data-stu-id="1cda7-103">Owner drawing in Windows Forms, which is also known as custom drawing, is a technique for changing the visual appearance of certain controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cda7-104">A palavra "control" neste tópico é usada para indicar as classes que derivam do <xref:System.Windows.Forms.Control> ou <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="1cda7-104">The word "control" in this topic is used to mean classes that derive from either <xref:System.Windows.Forms.Control> or <xref:System.ComponentModel.Component>.</span></span>  
  
 <span data-ttu-id="1cda7-105">Normalmente, Windows manipula pintura automaticamente usando as configurações de propriedade, como <xref:System.Windows.Forms.Control.BackColor%2A> para determinar a aparência de um controle.</span><span class="sxs-lookup"><span data-stu-id="1cda7-105">Typically, Windows handles painting automatically by using property settings such as <xref:System.Windows.Forms.Control.BackColor%2A> to determine the appearance of a control.</span></span> <span data-ttu-id="1cda7-106">Com o desenho do proprietário, assumir o processo de pintura, alterando os elementos que não estão disponíveis usando propriedades de aparência.</span><span class="sxs-lookup"><span data-stu-id="1cda7-106">With owner drawing, you take over the painting process, changing elements of appearance that are not available by using properties.</span></span> <span data-ttu-id="1cda7-107">Por exemplo, muitos controles permitem que você defina a cor do texto que é exibido, mas você está limitado a uma única cor.</span><span class="sxs-lookup"><span data-stu-id="1cda7-107">For example, many controls let you set the color of the text that is displayed, but you are limited to a single color.</span></span> <span data-ttu-id="1cda7-108">Desenho do proprietário permite que você faça coisas como parte do texto de exibição em preto e parte em vermelho.</span><span class="sxs-lookup"><span data-stu-id="1cda7-108">Owner drawing enables you to do things like display part of the text in black and part in red.</span></span>  
  
 <span data-ttu-id="1cda7-109">Na prática, o desenho do proprietário é semelhante ao desenho de gráficos em um formulário.</span><span class="sxs-lookup"><span data-stu-id="1cda7-109">In practice, owner drawing is similar to drawing graphics on a form.</span></span> <span data-ttu-id="1cda7-110">Por exemplo, você pode usar métodos gráficos em um manipulador para o formulário <xref:System.Windows.Forms.Control.Paint> evento para emular uma `ListBox` controle, mas você teria de escrever seu próprio código para lidar com todas as interações do usuário.</span><span class="sxs-lookup"><span data-stu-id="1cda7-110">For example, you could use graphics methods in a handler for the form's <xref:System.Windows.Forms.Control.Paint> event to emulate a `ListBox` control, but you would have to write your own code to handle all user interaction.</span></span> <span data-ttu-id="1cda7-111">Com o desenho do proprietário, o controle usa seu código para desenhar seu conteúdo, mas caso contrário retém todos os seus recursos intrínsecos.</span><span class="sxs-lookup"><span data-stu-id="1cda7-111">With owner drawing, the control uses your code to draw its contents but otherwise retains all its intrinsic capabilities.</span></span> <span data-ttu-id="1cda7-112">Você pode usar métodos gráficos para desenhar cada item no controle ou personalizar alguns aspectos de cada item enquanto você usa a aparência padrão para outros aspectos de cada item.</span><span class="sxs-lookup"><span data-stu-id="1cda7-112">You can use graphics methods to draw each item in the control or to customize some aspects of each item while you use the default appearance for other aspects of each item.</span></span>  
  
## <a name="owner-drawing-in-windows-forms-controls"></a><span data-ttu-id="1cda7-113">Desenho do proprietário no Controle dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1cda7-113">Owner Drawing in Windows Forms Controls</span></span>  
 <span data-ttu-id="1cda7-114">Para executar o desenho do proprietário na controles que oferecem suporte a ele, você normalmente define uma propriedade e manipular um ou mais eventos.</span><span class="sxs-lookup"><span data-stu-id="1cda7-114">To perform owner drawing in controls that support it, you will typically set one property and handle one or more events.</span></span>  
  
 <span data-ttu-id="1cda7-115">A maioria dos controles têm de desenho do proprietário que suporte uma propriedade `OwnerDraw` ou `DrawMode` que indica se o controle será aumentará seu evento ou eventos de desenho quando ela pinta a si mesma.</span><span class="sxs-lookup"><span data-stu-id="1cda7-115">Most controls that support owner drawing have an `OwnerDraw` or `DrawMode` property that indicates whether the control will raise its drawing-related event or events when it paints itself.</span></span>  
  
 <span data-ttu-id="1cda7-116">Controles que não têm uma propriedade `OwnerDraw` ou `DrawMode`, incluem o `DataGridView` controle, que fornece eventos de desenho que ocorrem automaticamente e o `ToolStrip` controle, que é desenhado usando uma classe de renderização externa que tem seus próprios eventos relacionados ao desenho.</span><span class="sxs-lookup"><span data-stu-id="1cda7-116">Controls that do not have an `OwnerDraw` or `DrawMode` property include the `DataGridView` control, which provides drawing events that occur automatically, and the `ToolStrip` control, which is drawn using an external rendering class that has its own drawing-related events.</span></span>  
  
 <span data-ttu-id="1cda7-117">Há muitos tipos diferentes de eventos de desenho, mas ocorre um evento típico de desenho para desenhar um único item em um controle.</span><span class="sxs-lookup"><span data-stu-id="1cda7-117">There are many different kinds of drawing events, but a typical drawing event occurs in order to draw a single item within a control.</span></span> <span data-ttu-id="1cda7-118">O manipulador de eventos recebe um `EventArgs` objeto que contém informações sobre o item que está sendo desenhado e ferramentas que você pode usar para desenhá-lo.</span><span class="sxs-lookup"><span data-stu-id="1cda7-118">The event handler receives an `EventArgs` object that contains information about the item being drawn and tools you can use to draw it.</span></span> <span data-ttu-id="1cda7-119">Por exemplo, esse objeto normalmente contém o número de índice do item dentro de sua coleção pai, uma <xref:System.Drawing.Rectangle> que indica o item exibe limites e um <xref:System.Drawing.Graphics> objeto para chamar métodos de pintura.</span><span class="sxs-lookup"><span data-stu-id="1cda7-119">For example, this object typically contains the item's index number within its parent collection, a <xref:System.Drawing.Rectangle> that indicates the item's display boundaries, and a <xref:System.Drawing.Graphics> object for calling paint methods.</span></span> <span data-ttu-id="1cda7-120">Em alguns casos, o `EventArgs` objeto fornece informações adicionais sobre o item e os métodos que você pode chamar para pintar alguns aspectos do item por padrão, como a tela de fundo ou um retângulo de foco.</span><span class="sxs-lookup"><span data-stu-id="1cda7-120">For some events, the `EventArgs` object provides additional information about the item and methods that you can call to paint some aspects of the item by default, such as the background or a focus rectangle.</span></span>  
  
 <span data-ttu-id="1cda7-121">Para criar um controle reutilizável que contém as personalizações desenhados pelo proprietário, crie uma nova classe que deriva de uma classe de controle que dá suporte ao desenho do proprietário.</span><span class="sxs-lookup"><span data-stu-id="1cda7-121">To create a reusable control that contains your owner-drawn customizations, create a new class that derives from a control class that supports owner drawing.</span></span> <span data-ttu-id="1cda7-122">Em vez de manipular eventos de desenho, incluir o código de desenho do proprietário em substituições de método ou métodos apropriados de `On` *EventName* na nova classe.</span><span class="sxs-lookup"><span data-stu-id="1cda7-122">Rather than handling drawing events, include your owner-drawing code in overrides for the appropriate `On`*EventName* method or methods in the new class.</span></span> <span data-ttu-id="1cda7-123">Certifique-se de que você chamar o método ou métodos da classe base `On` *EventName* nesse caso, para que os usuários de seu controle possam manipular eventos de desenho do proprietário e fornecer personalização adicional.</span><span class="sxs-lookup"><span data-stu-id="1cda7-123">Make sure that you call the base class `On`*EventName* method or methods in this case so that users of your control can handle owner-drawing events and provide additional customization.</span></span>  
  
 <span data-ttu-id="1cda7-124">O Windows Forms a seguir controla desenho do proprietário em todas as versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1cda7-124">The following Windows Forms controls support owner drawing in all versions of the .NET Framework:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <span data-ttu-id="1cda7-125"><xref:System.Windows.Forms.MenuItem>(usado pelo <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu>)</span><span class="sxs-lookup"><span data-stu-id="1cda7-125"><xref:System.Windows.Forms.MenuItem> (used by <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu>)</span></span>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 <span data-ttu-id="1cda7-126">Os seguintes controles oferecem suporte apenas no desenho do proprietário [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="1cda7-126">The following controls support owner drawing only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 <span data-ttu-id="1cda7-127">Os seguintes controles dão suporte ao desenho do proprietário e são novos no [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="1cda7-127">The following controls support owner drawing and are new in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 <span data-ttu-id="1cda7-128">As seções a seguir fornecem detalhes adicionais para cada um desses controles.</span><span class="sxs-lookup"><span data-stu-id="1cda7-128">The following sections provide additional details for each of these controls.</span></span>  
  
### <a name="listbox-and-combobox-controls"></a><span data-ttu-id="1cda7-129">Controles de Caixa de Combinação e Caixa de listagem</span><span class="sxs-lookup"><span data-stu-id="1cda7-129">ListBox and ComboBox Controls</span></span>  
 <span data-ttu-id="1cda7-130">O <xref:System.Windows.Forms.ListBox> e <xref:System.Windows.Forms.ComboBox> controles permitem que você desenhar itens individuais no controle em um tamanho ou em diferentes tamanhos.</span><span class="sxs-lookup"><span data-stu-id="1cda7-130">The <xref:System.Windows.Forms.ListBox> and <xref:System.Windows.Forms.ComboBox> controls enable you to draw individual items in the control either all in one size, or in varying sizes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cda7-131">Embora o <xref:System.Windows.Forms.CheckedListBox> controle é derivado de <xref:System.Windows.Forms.ListBox> controle, ele não suporta desenho do proprietário.</span><span class="sxs-lookup"><span data-stu-id="1cda7-131">Although the <xref:System.Windows.Forms.CheckedListBox> control is derived from the <xref:System.Windows.Forms.ListBox> control, it does not support owner drawing.</span></span>  
  
 <span data-ttu-id="1cda7-132">Para desenhar cada item do mesmo tamanho, defina o `DrawMode` propriedade <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> e tratar o `DrawItem` evento.</span><span class="sxs-lookup"><span data-stu-id="1cda7-132">To draw each item the same size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="1cda7-133">Para desenhar cada item usando um tamanho diferente, defina o `DrawMode` propriedade <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> e lidar com ambos os `MeasureItem` e `DrawItem` eventos.</span><span class="sxs-lookup"><span data-stu-id="1cda7-133">To draw each item using a different size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> and handle both the `MeasureItem` and `DrawItem` events.</span></span> <span data-ttu-id="1cda7-134">O evento `MeasureItem` permite indicar o tamanho de um item antes do evento `DrawItem` ocorrer para aquele item.</span><span class="sxs-lookup"><span data-stu-id="1cda7-134">The `MeasureItem` event lets you indicate the size of an item before the `DrawItem` event occurs for that item.</span></span>  
  
 <span data-ttu-id="1cda7-135">Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="1cda7-135">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [<span data-ttu-id="1cda7-136">Como criar texto dimensionado da variável em um controle ComboBox</span><span class="sxs-lookup"><span data-stu-id="1cda7-136">How to: Create Variable Sized Text in a ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a><span data-ttu-id="1cda7-137">Componente do MenuItem</span><span class="sxs-lookup"><span data-stu-id="1cda7-137">MenuItem Component</span></span>  
 <span data-ttu-id="1cda7-138">O <xref:System.Windows.Forms.MenuItem> componente representa um item de menu único em uma <xref:System.Windows.Forms.MainMenu> ou <xref:System.Windows.Forms.ContextMenu> componente.</span><span class="sxs-lookup"><span data-stu-id="1cda7-138">The <xref:System.Windows.Forms.MenuItem> component represents a single menu item in a <xref:System.Windows.Forms.MainMenu> or <xref:System.Windows.Forms.ContextMenu> component.</span></span>  
  
 <span data-ttu-id="1cda7-139">Para desenhar uma <xref:System.Windows.Forms.MenuItem>, defina seu `OwnerDraw` propriedade `true` e manipular seu `DrawItem` eventos.</span><span class="sxs-lookup"><span data-stu-id="1cda7-139">To draw a <xref:System.Windows.Forms.MenuItem>, set its `OwnerDraw` property to `true` and handle its `DrawItem` event.</span></span> <span data-ttu-id="1cda7-140">Para personalizar o tamanho do item de menu antes do evento `DrawItem` ocorrer, identifique os eventos `MeasureItem` do item.</span><span class="sxs-lookup"><span data-stu-id="1cda7-140">To customize the size of the menu item before the `DrawItem` event occurs, handle the item's `MeasureItem` event.</span></span>  
  
 <span data-ttu-id="1cda7-141">Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos de referência:</span><span class="sxs-lookup"><span data-stu-id="1cda7-141">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a><span data-ttu-id="1cda7-142">Controle TabControl</span><span class="sxs-lookup"><span data-stu-id="1cda7-142">TabControl Control</span></span>  
 <span data-ttu-id="1cda7-143">O <xref:System.Windows.Forms.TabControl> controle permite que você desenhe guias individuais no controle.</span><span class="sxs-lookup"><span data-stu-id="1cda7-143">The <xref:System.Windows.Forms.TabControl> control enables you to draw individual tabs in the control.</span></span> <span data-ttu-id="1cda7-144">Desenho proprietário afeta somente as guias; o <xref:System.Windows.Forms.TabPage> conteúdo não é afetado.</span><span class="sxs-lookup"><span data-stu-id="1cda7-144">Owner drawing affects only the tabs; the <xref:System.Windows.Forms.TabPage> contents are not affected.</span></span>  
  
 <span data-ttu-id="1cda7-145">Para desenhar cada guia um <xref:System.Windows.Forms.TabControl>, defina o `DrawMode` propriedade <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> e lidar com o `DrawItem` evento.</span><span class="sxs-lookup"><span data-stu-id="1cda7-145">To draw each tab in a <xref:System.Windows.Forms.TabControl>, set the `DrawMode` property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span> <span data-ttu-id="1cda7-146">Esse evento ocorre uma vez para cada guia somente quando a guia estiver visível no controle.</span><span class="sxs-lookup"><span data-stu-id="1cda7-146">This event occurs once for each tab only when the tab is visible in the control.</span></span>  
  
 <span data-ttu-id="1cda7-147">Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos de referência:</span><span class="sxs-lookup"><span data-stu-id="1cda7-147">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a><span data-ttu-id="1cda7-148">Componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="1cda7-148">ToolTip Component</span></span>  
 <span data-ttu-id="1cda7-149">O <xref:System.Windows.Forms.ToolTip> componente permite que você desenhe a dica de ferramenta inteira quando ele for exibido.</span><span class="sxs-lookup"><span data-stu-id="1cda7-149">The <xref:System.Windows.Forms.ToolTip> component enables you to draw the entire ToolTip when it is displayed.</span></span>  
  
 <span data-ttu-id="1cda7-150">Para desenhar uma <xref:System.Windows.Forms.ToolTip>, defina seu `OwnerDraw` propriedade `true` e manipular seu `Draw` eventos.</span><span class="sxs-lookup"><span data-stu-id="1cda7-150">To draw a <xref:System.Windows.Forms.ToolTip>, set its `OwnerDraw` property to `true` and handle its `Draw` event.</span></span> <span data-ttu-id="1cda7-151">Para personalizar o tamanho do <xref:System.Windows.Forms.ToolTip> antes do `Draw` evento ocorrer, lidar com o `Popup` evento e defina o <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> propriedade no manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="1cda7-151">To customize the size of the <xref:System.Windows.Forms.ToolTip> before the `Draw` event occurs, handle the `Popup` event and set the <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> property in the event handler.</span></span>  
  
 <span data-ttu-id="1cda7-152">Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos de referência:</span><span class="sxs-lookup"><span data-stu-id="1cda7-152">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a><span data-ttu-id="1cda7-153">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="1cda7-153">ListView Control</span></span>  
 <span data-ttu-id="1cda7-154">O <xref:System.Windows.Forms.ListView> controle permite que você desenhar itens individuais, subitens e cabeçalhos de coluna no controle.</span><span class="sxs-lookup"><span data-stu-id="1cda7-154">The <xref:System.Windows.Forms.ListView> control enables you to draw individual items, subitems, and column headers in the control.</span></span>  
  
 <span data-ttu-id="1cda7-155">Para habilitar o controle de desenho do proprietário, defina a propriedade `OwnerDraw` para `true`.</span><span class="sxs-lookup"><span data-stu-id="1cda7-155">To enable owner drawing in the control, set the `OwnerDraw` property to `true`.</span></span>  
  
 <span data-ttu-id="1cda7-156">Para desenhar cada item no controle, identifique o evento `DrawItem`.</span><span class="sxs-lookup"><span data-stu-id="1cda7-156">To draw each item in the control, handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="1cda7-157">Para desenhar cada cabeçalho de coluna ou subitem no controle quando o <xref:System.Windows.Forms.ListView.View%2A> está definida como <xref:System.Windows.Forms.View.Details>, tratar o `DrawSubItem` e `DrawColumnHeader` eventos.</span><span class="sxs-lookup"><span data-stu-id="1cda7-157">To draw each subitem or column header in the control when the <xref:System.Windows.Forms.ListView.View%2A> property is set to <xref:System.Windows.Forms.View.Details>, handle the `DrawSubItem` and `DrawColumnHeader` events.</span></span>  
  
 <span data-ttu-id="1cda7-158">Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos de referência:</span><span class="sxs-lookup"><span data-stu-id="1cda7-158">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a><span data-ttu-id="1cda7-159">Controle TreeView</span><span class="sxs-lookup"><span data-stu-id="1cda7-159">TreeView Control</span></span>  
 <span data-ttu-id="1cda7-160">O <xref:System.Windows.Forms.TreeView> controle permite que você desenhe nós individuais no controle.</span><span class="sxs-lookup"><span data-stu-id="1cda7-160">The <xref:System.Windows.Forms.TreeView> control enables you to draw individual nodes in the control.</span></span>  
  
 <span data-ttu-id="1cda7-161">Para desenhar apenas o texto exibido em cada nó, defina o `DrawMode` propriedade <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> e tratar o `DrawNode` evento para desenhar o texto.</span><span class="sxs-lookup"><span data-stu-id="1cda7-161">To draw only the text displayed in each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> and handle the `DrawNode` event to draw the text.</span></span>  
  
 <span data-ttu-id="1cda7-162">Para desenhar todos os elementos de cada nó, defina o `DrawMode` propriedade <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> e tratar o `DrawNode` evento para desenhar o elementos necessários, como caixas, adição e subtração sinais de seleção de texto, ícones e linhas que conectam os nós.</span><span class="sxs-lookup"><span data-stu-id="1cda7-162">To draw all elements of each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> and handle the `DrawNode` event to draw whichever elements you need, such as text, icons, check boxes, plus and minus signs, and lines connecting the nodes.</span></span>  
  
 <span data-ttu-id="1cda7-163">Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos de referência:</span><span class="sxs-lookup"><span data-stu-id="1cda7-163">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a><span data-ttu-id="1cda7-164">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="1cda7-164">DataGridView Control</span></span>  
 <span data-ttu-id="1cda7-165">O <xref:System.Windows.Forms.DataGridView> controle permite que você desenhar linhas e células individuais no controle.</span><span class="sxs-lookup"><span data-stu-id="1cda7-165">The <xref:System.Windows.Forms.DataGridView> control enables you to draw individual cells and rows in the control.</span></span>  
  
 <span data-ttu-id="1cda7-166">Para desenhar células individuais, identifique o evento `CellPainting`.</span><span class="sxs-lookup"><span data-stu-id="1cda7-166">To draw individual cells, handle the `CellPainting` event.</span></span>  
  
 <span data-ttu-id="1cda7-167">Para desenhar linhas individuais ou elementos de linhas, identifique um ou ambos os eventos `RowPrePaint` e `RowPostPaint`.</span><span class="sxs-lookup"><span data-stu-id="1cda7-167">To draw individual rows or elements of rows, handle one or both of the `RowPrePaint` and `RowPostPaint` events.</span></span> <span data-ttu-id="1cda7-168">O evento `RowPrePaint` ocorre antes das células em uma linha serem pintadas e o evento `RowPostPaint` ocorre depois que as células são pintadas.</span><span class="sxs-lookup"><span data-stu-id="1cda7-168">The `RowPrePaint` event occurs before the cells in a row are painted, and the `RowPostPaint` event occurs after the cells are painted.</span></span> <span data-ttu-id="1cda7-169">Você pode identificar ambos os eventos e o evento `CellPainting` para pintar a tela de fundo de linha, células individuais e primeiro plano linha separadamente ou você pode fornecer personalizações específicas em que você precisa deles e use a exibição padrão para outros elementos da linha.</span><span class="sxs-lookup"><span data-stu-id="1cda7-169">You can handle both events and the `CellPainting` event to paint row background, individual cells, and row foreground separately, or you can provide specific customizations where you need them and use the default display for other elements of the row.</span></span>  
  
 <span data-ttu-id="1cda7-170">Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="1cda7-170">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [<span data-ttu-id="1cda7-171">Como personalizar a aparência de células no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1cda7-171">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [<span data-ttu-id="1cda7-172">Como personalizar a aparência de linhas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1cda7-172">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a><span data-ttu-id="1cda7-173">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1cda7-173">ToolStrip Control</span></span>  
 <span data-ttu-id="1cda7-174"><xref:System.Windows.Forms.ToolStrip>e controles derivados permitem personalizar todos os aspectos de sua aparência.</span><span class="sxs-lookup"><span data-stu-id="1cda7-174"><xref:System.Windows.Forms.ToolStrip> and derived controls enable you to customize any aspect of their appearance.</span></span>  
  
 <span data-ttu-id="1cda7-175">Para fornecer processamento personalizado para <xref:System.Windows.Forms.ToolStrip> controles, defina o `Renderer` propriedade de um <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, ou <xref:System.Windows.Forms.ToolStripContentPanel> para um `ToolStripRenderer` de objeto e lidar com um ou mais dos muitos eventos de desenho fornecidos pelo `ToolStripRenderer` classe.</span><span class="sxs-lookup"><span data-stu-id="1cda7-175">To provide custom rendering for <xref:System.Windows.Forms.ToolStrip> controls, set the `Renderer` property of a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, or <xref:System.Windows.Forms.ToolStripContentPanel> to a `ToolStripRenderer` object and handle one or more of the many drawing events provided by the `ToolStripRenderer` class.</span></span> <span data-ttu-id="1cda7-176">Como alternativa, defina um `Renderer` propriedade a uma instância de sua própria classe derivada de `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, ou <xref:System.Windows.Forms.ToolStripSystemRenderer> que implementa ou substitui específico `On` *EventName* métodos.</span><span class="sxs-lookup"><span data-stu-id="1cda7-176">Alternatively, set a `Renderer` property to an instance of your own class derived from `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, or <xref:System.Windows.Forms.ToolStripSystemRenderer> that implements or overrides specific `On`*EventName* methods.</span></span>  
  
 <span data-ttu-id="1cda7-177">Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="1cda7-177">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [<span data-ttu-id="1cda7-178">Como criar e definir um renderizador personalizado para o controle ToolStrip nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1cda7-178">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [<span data-ttu-id="1cda7-179">Como personalizar o desenho de um controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1cda7-179">How to: Custom Draw a ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a><span data-ttu-id="1cda7-180">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cda7-180">See Also</span></span>  
 [<span data-ttu-id="1cda7-181">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1cda7-181">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)