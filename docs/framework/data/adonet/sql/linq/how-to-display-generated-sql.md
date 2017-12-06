---
title: 'Como: Exibir o SQL gerado'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 523a6cbd0174da4c294e5fd2ab2d0217fc63cb5c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-display-generated-sql"></a><span data-ttu-id="7e15d-102">Como: Exibir o SQL gerado</span><span class="sxs-lookup"><span data-stu-id="7e15d-102">How to: Display Generated SQL</span></span>
<span data-ttu-id="7e15d-103">Você pode exibir o código SQL gerado para consultas e processamento de alteração usando a propriedade de <xref:System.Data.Linq.DataContext.Log%2A> .</span><span class="sxs-lookup"><span data-stu-id="7e15d-103">You can view the SQL code generated for queries and change processing by using the <xref:System.Data.Linq.DataContext.Log%2A> property.</span></span> <span data-ttu-id="7e15d-104">Essa abordagem pode ser útil para entender a funcionalidade de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e depure questões específicas.</span><span class="sxs-lookup"><span data-stu-id="7e15d-104">This approach can be useful for understanding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] functionality and for debugging specific problems.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e15d-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7e15d-105">Example</span></span>  
 <span data-ttu-id="7e15d-106">O exemplo a seguir usa a propriedade de <xref:System.Data.Linq.DataContext.Log%2A> para exibir o código SQL na janela do console antes que o código seja executado.</span><span class="sxs-lookup"><span data-stu-id="7e15d-106">The following example uses the <xref:System.Data.Linq.DataContext.Log%2A> property to display SQL code in the console window before the code is executed.</span></span>  <span data-ttu-id="7e15d-107">Você pode usar essa propriedade com consulta, inserir, atualizar, excluir e comandos.</span><span class="sxs-lookup"><span data-stu-id="7e15d-107">You can use this property with query, insert, update, and delete commands.</span></span>  
  
 <span data-ttu-id="7e15d-108">As linhas da janela do console são o que você vê quando você executa [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou código em c que segue.</span><span class="sxs-lookup"><span data-stu-id="7e15d-108">The lines from the console window are what you see when you execute the [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# code that follows.</span></span>  
  
```  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
-- @p0: Input String (Size = 6; Prec = 0; Scale = 0) [London]  
-- Context: SqlProvider(Sql2005) Model: AttributedMetaModel Build: 3.5.20810.0  
```  
  
```  
AROUT  
BSBEV  
CONSH  
EASTC  
NORTS  
SEVES  
```  
  
 [!code-csharp[DLinqDebuggingSupport#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#1)]
 [!code-vb[DLinqDebuggingSupport#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7e15d-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e15d-109">See Also</span></span>  
 [<span data-ttu-id="7e15d-110">Suporte à depuração</span><span class="sxs-lookup"><span data-stu-id="7e15d-110">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)