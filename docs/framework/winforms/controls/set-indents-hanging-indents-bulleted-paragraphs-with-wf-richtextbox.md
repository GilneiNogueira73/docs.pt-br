---
title: "Como definir recuos definidos, recuos deslocados e parágrafos com marcadores com o controle RichTextBox dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9b1398c0438f9ebe528e9394014f5f6529ea8f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="2b7d8-102">Como definir recuos definidos, recuos deslocados e parágrafos com marcadores com o controle RichTextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2b7d8-102">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="2b7d8-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> controle tem várias opções para formatar o texto é exibido.</span><span class="sxs-lookup"><span data-stu-id="2b7d8-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="2b7d8-104">Você pode formatar parágrafos selecionados como listas de marcadores, definindo o <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="2b7d8-104">You can format selected paragraphs as bulleted lists by setting the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="2b7d8-105">Você também pode usar o <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, e <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> propriedades para definir o recuo de parágrafos em relação à esquerda e direita bordas do controle e a borda esquerda de outras linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="2b7d8-105">You can also use the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, and <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> properties to set the indentation of paragraphs relative to the left and right edges of the control, and the left edge of other lines of text.</span></span>  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a><span data-ttu-id="2b7d8-106">Formatar um parágrafo como uma lista com marcadores</span><span class="sxs-lookup"><span data-stu-id="2b7d8-106">To format a paragraph as a bulleted list</span></span>  
  
1.  <span data-ttu-id="2b7d8-107">Defina a propriedade <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="2b7d8-107">Set the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property to `true`.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a><span data-ttu-id="2b7d8-108">Para recuar um parágrafo</span><span class="sxs-lookup"><span data-stu-id="2b7d8-108">To indent a paragraph</span></span>  
  
1.  <span data-ttu-id="2b7d8-109">Definir o <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> propriedade como um inteiro que representa a distância em pixels entre a borda esquerda do controle e a borda esquerda do texto.</span><span class="sxs-lookup"><span data-stu-id="2b7d8-109">Set the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> property to an integer representing the distance in pixels between the left edge of the control and the left edge of the text.</span></span>  
  
2.  <span data-ttu-id="2b7d8-110">Definir o <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> propriedade como um inteiro que representa a distância em pixels entre a borda esquerda da primeira linha do texto no parágrafo e a borda esquerda das linhas subsequentes no mesmo paragraph.</span><span class="sxs-lookup"><span data-stu-id="2b7d8-110">Set the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property to an integer representing the distance in pixels between the left edge of the first line of text in the paragraph and the left edge of subsequent lines in the same paragraph.</span></span> <span data-ttu-id="2b7d8-111">O valor de <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> propriedade só se aplica a linhas em um parágrafo que encapsulados abaixo da primeira linha.</span><span class="sxs-lookup"><span data-stu-id="2b7d8-111">The value of the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property only applies to lines in a paragraph that have wrapped below the first line.</span></span>  
  
3.  <span data-ttu-id="2b7d8-112">Definir o <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> propriedade como um inteiro que representa a distância em pixels entre a borda direita do controle e a borda direita do texto.</span><span class="sxs-lookup"><span data-stu-id="2b7d8-112">Set the <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> property to an integer representing the distance in pixels between the right edge of the control and the right edge of the text.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="2b7d8-113">Todas essas propriedades afetam todos os parágrafos que contêm o texto selecionado, bem como o texto digitado após o ponto de inserção atual.</span><span class="sxs-lookup"><span data-stu-id="2b7d8-113">All these properties affect any paragraphs that contain selected text, and also the text that is typed after the current insertion point.</span></span> <span data-ttu-id="2b7d8-114">Por exemplo, quando um usuário seleciona uma palavra em um parágrafo e ajusta o recuo, as novas configurações serão aplicadas a todo o parágrafo que contém a palavra, bem como aos parágrafos subsequentemente inseridos depois do parágrafo selecionado.</span><span class="sxs-lookup"><span data-stu-id="2b7d8-114">For example, when a user selects a word within a paragraph and then adjusts the indentation, the new settings will apply to the entire paragraph that contains that word, and also to any paragraphs subsequently entered after the selected paragraph.</span></span> <span data-ttu-id="2b7d8-115">Para obter informações sobre como selecionar texto programaticamente, consulte <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="2b7d8-115">For information about selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b7d8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b7d8-116">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="2b7d8-117">Controle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="2b7d8-117">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="2b7d8-118">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2b7d8-118">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)