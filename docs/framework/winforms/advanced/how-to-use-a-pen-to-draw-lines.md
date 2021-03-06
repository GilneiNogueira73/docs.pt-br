---
title: Como usar uma caneta para desenhar linhas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: 6a728bcaf9946b2b92ce0ee97599f4c4fd0fea69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522978"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a>Como usar uma caneta para desenhar linhas
Para desenhar linhas, é necessário um <xref:System.Drawing.Graphics> objeto e um <xref:System.Drawing.Pen> objeto. O <xref:System.Drawing.Graphics> objeto fornece o <xref:System.Drawing.Graphics.DrawLine%2A> método e o <xref:System.Drawing.Pen> objeto armazena recursos da linha, como cor e largura.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desenha uma linha de (10, 20) para (300, 100). A primeira instrução usa o <xref:System.Drawing.Pen.%23ctor%2A> construtor de classe para criar uma caneta preta. Um argumento passado para o <xref:System.Drawing.Pen.%23ctor%2A> construtor é um <xref:System.Drawing.Color> objeto criado com o <xref:System.Drawing.Color.FromArgb%2A> método. Os valores usados para criar o <xref:System.Drawing.Color> objeto — (255, 0, 0, 0) — correspondem aos componentes alfa, vermelhos, verdes e azuis da cor. Esses valores definem uma caneta preta opaca.  
  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Pen>  
 [Usando uma caneta para desenhar linhas e formas](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Canetas, Linhas e Retângulos no GDI+](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
