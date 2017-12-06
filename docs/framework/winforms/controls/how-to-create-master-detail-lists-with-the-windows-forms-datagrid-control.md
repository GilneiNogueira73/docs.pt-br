---
title: 'Como: criar listas mestre / detalhes com o controle DataGrid dos Windows Forms'
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
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63cb647e2ed6dcbc97fab15db3166b55c52f635a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="e1a57-102">Como criar listas mestre/detalhes com o controle DataGrid dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1a57-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="e1a57-103">O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="e1a57-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="e1a57-104">Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e1a57-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="e1a57-105">Se seu <xref:System.Data.DataSet> contém uma série de tabelas relacionadas, você pode usar dois <xref:System.Windows.Forms.DataGrid> controles para exibir os dados em um formato de detalhes/mestre.</span><span class="sxs-lookup"><span data-stu-id="e1a57-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="e1a57-106">Um <xref:System.Windows.Forms.DataGrid> é designado como a grade principal, e o segundo é designado como a grade de detalhes.</span><span class="sxs-lookup"><span data-stu-id="e1a57-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="e1a57-107">Quando você seleciona uma entrada na lista mestra, todas as entradas filho relacionados são mostradas na lista de detalhes.</span><span class="sxs-lookup"><span data-stu-id="e1a57-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="e1a57-108">Por exemplo, se seu <xref:System.Data.DataSet> contém uma tabela clientes e uma tabela relacionada Orders, você deve especificar a tabela de clientes para a grade principal e a tabela de pedidos para a grade de detalhes.</span><span class="sxs-lookup"><span data-stu-id="e1a57-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="e1a57-109">Quando um cliente é selecionado na grade principal, todos os pedidos associados a ele na tabela Pedidos serão exibidos na grade de detalhes.</span><span class="sxs-lookup"><span data-stu-id="e1a57-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="e1a57-110">Definir uma relação mestre/detalhes com programação</span><span class="sxs-lookup"><span data-stu-id="e1a57-110">To set a master/detail relationship programmatically</span></span>  
  
1.  <span data-ttu-id="e1a57-111">Crie dois novos <xref:System.Windows.Forms.DataGrid> controla e definir suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="e1a57-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2.  <span data-ttu-id="e1a57-112">Adicione tabelas ao conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="e1a57-112">Add tables to the dataset.</span></span>  
  
3.  <span data-ttu-id="e1a57-113">Declare uma variável do tipo <xref:System.Data.DataRelation> representar a relação que você deseja criar.</span><span class="sxs-lookup"><span data-stu-id="e1a57-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4.  <span data-ttu-id="e1a57-114">Instancie o relacionamento especificando um nome para o relacionamento e especificando a tabela, coluna e item que associará as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="e1a57-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5.  <span data-ttu-id="e1a57-115">Adicionar a relação com o <xref:System.Data.DataSet> do objeto <xref:System.Data.DataSet.Relations%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="e1a57-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6.  <span data-ttu-id="e1a57-116">Use o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método o <xref:System.Windows.Forms.DataGrid> para associar cada uma das grades para o <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e1a57-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="e1a57-117">O exemplo a seguir mostra como definir uma relação mestre/detalhes entre as tabelas Customers e Orders no gerado anteriormente <xref:System.Data.DataSet> (`ds`).</span><span class="sxs-lookup"><span data-stu-id="e1a57-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e1a57-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1a57-118">See Also</span></span>  
 [<span data-ttu-id="e1a57-119">Controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="e1a57-119">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="e1a57-120">Visão geral do controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="e1a57-120">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [<span data-ttu-id="e1a57-121">Como associar o controle DataGrid dos Windows Forms a uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="e1a57-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)