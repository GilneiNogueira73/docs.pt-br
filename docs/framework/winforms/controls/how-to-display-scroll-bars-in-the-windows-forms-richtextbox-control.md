---
title: Como exibir barras de rolagem no controle RichTextBox dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3b20c526b27eb185bf79eaf0ace47e5a9fded42a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a><span data-ttu-id="fddc8-102">Como exibir barras de rolagem no controle RichTextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fddc8-102">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="fddc8-103">Por padrão, o Windows Forms <xref:System.Windows.Forms.RichTextBox> controle exibe barras de rolagem horizontal e vertical conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="fddc8-103">By default, the Windows Forms <xref:System.Windows.Forms.RichTextBox> control displays horizontal and vertical scroll bars as necessary.</span></span> <span data-ttu-id="fddc8-104">Há sete valores possíveis para a <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> propriedade o <xref:System.Windows.Forms.RichTextBox> controle, que são descritas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="fddc8-104">There are seven possible values for the <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> property of the <xref:System.Windows.Forms.RichTextBox> control, which are described in the table below.</span></span>  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a><span data-ttu-id="fddc8-105">Exibir barras de rolagem em um controle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="fddc8-105">To display scroll bars in a RichTextBox control</span></span>  
  
1.  <span data-ttu-id="fddc8-106">Defina a propriedade <xref:System.Windows.Forms.RichTextBox.Multiline%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="fddc8-106">Set the <xref:System.Windows.Forms.RichTextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="fddc8-107">Nenhum tipo de barra, inclusive de rolagem horizontal, será exibida se o <xref:System.Windows.Forms.RichTextBox.Multiline%2A> está definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="fddc8-107">No type of scroll bar, including horizontal, will display if the <xref:System.Windows.Forms.RichTextBox.Multiline%2A> property is set to `false`.</span></span>  
  
2.  <span data-ttu-id="fddc8-108">Definir o <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> propriedade para um valor apropriado igual a <xref:System.Windows.Forms.RichTextBoxScrollBars> enumeração.</span><span class="sxs-lookup"><span data-stu-id="fddc8-108">Set the <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> property to an appropriate value of the <xref:System.Windows.Forms.RichTextBoxScrollBars> enumeration.</span></span>  
  
    |<span data-ttu-id="fddc8-109">Valor</span><span class="sxs-lookup"><span data-stu-id="fddc8-109">Value</span></span>|<span data-ttu-id="fddc8-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="fddc8-110">Description</span></span>|  
    |-----------|-----------------|  
    |<span data-ttu-id="fddc8-111"><xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (padrão)</span><span class="sxs-lookup"><span data-stu-id="fddc8-111"><xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (default)</span></span>|<span data-ttu-id="fddc8-112">Exibe barras de rolagem horizontal, vertical ou ambas, mas apenas quando o texto excede a largura ou o comprimento do controle.</span><span class="sxs-lookup"><span data-stu-id="fddc8-112">Displays horizontal or vertical scroll bars, or both, only when text exceeds the width or length of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|<span data-ttu-id="fddc8-113">Nunca exibe nenhum tipo de barra de rolagem.</span><span class="sxs-lookup"><span data-stu-id="fddc8-113">Never displays any type of scroll bar.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|<span data-ttu-id="fddc8-114">Exibe uma barra de rolagem horizontal somente quando o texto excede a largura do controle.</span><span class="sxs-lookup"><span data-stu-id="fddc8-114">Displays a horizontal scroll bar only when the text exceeds the width of the control.</span></span> <span data-ttu-id="fddc8-115">(Para que isso ocorra, o <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> propriedade deve ser definida como `false`.)</span><span class="sxs-lookup"><span data-stu-id="fddc8-115">(For this to occur, the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property must be set to `false`.)</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|<span data-ttu-id="fddc8-116">Exibe uma barra de rolagem vertical somente quando o texto excede a altura do controle.</span><span class="sxs-lookup"><span data-stu-id="fddc8-116">Displays a vertical scroll bar only when the text exceeds the height of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|<span data-ttu-id="fddc8-117">Exibe quando da barra de rolagem de uma horizontal de <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> está definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="fddc8-117">Displays a horizontal scroll bar when the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property is set to `false`.</span></span> <span data-ttu-id="fddc8-118">A barra de rolagem aparece esmaecida quando o texto não excede a largura do controle.</span><span class="sxs-lookup"><span data-stu-id="fddc8-118">The scroll bar appears dimmed when text does not exceed the width of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|<span data-ttu-id="fddc8-119">Sempre exibe uma barra de rolagem vertical.</span><span class="sxs-lookup"><span data-stu-id="fddc8-119">Always displays a vertical scroll bar.</span></span> <span data-ttu-id="fddc8-120">A barra de rolagem aparece esmaecida quando o texto não excede o tamanho do controle.</span><span class="sxs-lookup"><span data-stu-id="fddc8-120">The scroll bar appears dimmed when text does not exceed the length of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|<span data-ttu-id="fddc8-121">Sempre exibe uma barra de rolagem vertical.</span><span class="sxs-lookup"><span data-stu-id="fddc8-121">Always displays a vertical scrollbar.</span></span> <span data-ttu-id="fddc8-122">Exibe quando da barra de rolagem de uma horizontal de <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> está definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="fddc8-122">Displays a horizontal scroll bar when the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property is set to `false`.</span></span> <span data-ttu-id="fddc8-123">A barra de rolagem aparece esmaecida quando o texto não excede a largura ou altura do controle.</span><span class="sxs-lookup"><span data-stu-id="fddc8-123">The scroll bars appear grayed when text does not exceed the width or length of the control.</span></span>|  
  
3.  <span data-ttu-id="fddc8-124">Definir o <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> propriedade para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="fddc8-124">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="fddc8-125">Valor</span><span class="sxs-lookup"><span data-stu-id="fddc8-125">Value</span></span>|<span data-ttu-id="fddc8-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="fddc8-126">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="fddc8-127">O texto do controle não é ajustado automaticamente para caber na largura do controle, por isso rolará para a direita até atingir uma quebra de linha.</span><span class="sxs-lookup"><span data-stu-id="fddc8-127">Text in the control is not automatically adjusted to fit the width of the control, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="fddc8-128">Use esse valor se você escolher barras de rolagem horizontal ou ambas acima.</span><span class="sxs-lookup"><span data-stu-id="fddc8-128">Use this value if you chose horizontal scroll bars or both, above.</span></span>|  
    |<span data-ttu-id="fddc8-129">`true` (padrão)</span><span class="sxs-lookup"><span data-stu-id="fddc8-129">`true` (default)</span></span>|<span data-ttu-id="fddc8-130">O texto do controle é ajustado automaticamente para caber na largura do controle.</span><span class="sxs-lookup"><span data-stu-id="fddc8-130">Text in the control is automatically adjusted to fit the width of the control.</span></span> <span data-ttu-id="fddc8-131">A barra de rolagem horizontal não será exibida.</span><span class="sxs-lookup"><span data-stu-id="fddc8-131">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="fddc8-132">Use esse valor se você escolher as barras de rolagem vertical ou nenhuma acima para exibir um ou mais parágrafos acima.</span><span class="sxs-lookup"><span data-stu-id="fddc8-132">Use this value if you chose vertical scroll bars or none, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fddc8-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fddc8-133">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="fddc8-134">Controle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="fddc8-134">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="fddc8-135">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fddc8-135">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)