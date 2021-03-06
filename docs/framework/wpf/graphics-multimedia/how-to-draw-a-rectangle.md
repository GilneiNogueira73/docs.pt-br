---
title: Como desenhar um retângulo
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 5f65bd11976817fe3f4d3e5d016f820a249769c3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506148"
---
# <a name="how-to-draw-a-rectangle"></a>Como desenhar um retângulo
Este exemplo mostra como desenhar um retângulo usando o <xref:System.Windows.Shapes.Rectangle> elemento.  
  
 Para desenhar um retângulo, crie uma <xref:System.Windows.Shapes.Rectangle> elemento e especifique seus <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A>. Para pintar o interior de um retângulo, defina seu <xref:System.Windows.Shapes.Shape.Fill%2A>. Para fornecer uma estrutura de tópicos de retângulo, use seus <xref:System.Windows.Shapes.Shape.Stroke%2A> e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propriedades.  
  
 Para dar o retângulo de cantos arredondados, especifique o valor opcional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> e <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> propriedades. O <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> e <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> propriedades definidas os raios do eixo x e y da elipse que é usada para arredondar os cantos do retângulo.  
  
 No exemplo a seguir, dois <xref:System.Windows.Shapes.Rectangle> elementos são desenhados em um <xref:System.Windows.Controls.Canvas>. O primeiro retângulo tem um <xref:System.Windows.Media.Brushes.Blue%2A> interiores. O segundo retângulo tem um <xref:System.Windows.Media.Brushes.Blue%2A> interiores, uma <xref:System.Windows.Media.Brushes.Black%2A> contorno e cantos arredondados.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 Embora este exemplo usa uma <xref:System.Windows.Controls.Canvas> para conter os retângulos, você pode usar elementos de retângulo (e todos os outros elementos de forma) com qualquer <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> que dá suporte a conteúdo não textual. Na verdade, retângulos são particularmente úteis para fornecer tela de fundo para partes do <xref:System.Windows.Controls.Grid> painéis. Para ver um exemplo, consulte a [Visão geral da tabela](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Shapes.Rectangle>  
 [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037)  
 [Visão geral de formas e desenho básico no WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Visão geral da tabela](../../../../docs/framework/wpf/advanced/table-overview.md)
