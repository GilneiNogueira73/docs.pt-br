---
title: "Como: definir relações de entidades (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60c2fc812bc00fcbc27335cf3b9539aacb32c91c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a><span data-ttu-id="9eed6-102">Como: definir relações de entidades (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="9eed6-102">How to: Define Entity Relationships (WCF Data Services)</span></span>
<span data-ttu-id="9eed6-103">Quando você adiciona uma nova entidade no [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], todas as relações entre as entidades relacionadas e nova entidade não são definidas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9eed6-103">When you add a new entity in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], any relationships between the new entity and related entities are not automatically defined.</span></span> <span data-ttu-id="9eed6-104">Você pode criar e alterar relações entre instâncias de entidade e que a biblioteca cliente refletir essas alterações no serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="9eed6-104">You can create and change relationships between entity instances and have the client library reflect those changes in the data service.</span></span> <span data-ttu-id="9eed6-105">Para obter mais informações, consulte [atualizar o serviço de dados](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="9eed6-105">For more information, see [Updating the Data Service](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="9eed6-106">O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9eed6-106">The example in this topic uses the Northwind sample data service and autogenerated client data service classes.</span></span> <span data-ttu-id="9eed6-107">Esse serviço e as classes de dados do cliente são criadas quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="9eed6-107">This service and the client data classes are created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eed6-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9eed6-108">Example</span></span>  
 <span data-ttu-id="9eed6-109">O exemplo a seguir cria uma nova instância de objeto e, em seguida, chama o <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> método sobre o <xref:System.Data.Services.Client.DataServiceContext> para criar o item de contexto junto com o link para o pedido relacionado.</span><span class="sxs-lookup"><span data-stu-id="9eed6-109">The following example creates a new object instance and then calls the <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> method on the <xref:System.Data.Services.Client.DataServiceContext> to create the item in the context along with the link to the related order.</span></span> <span data-ttu-id="9eed6-110">Uma mensagem HTTP POST é enviada para os dados de serviço quando o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método é chamado.</span><span class="sxs-lookup"><span data-stu-id="9eed6-110">An HTTP POST message is sent to the data service when the <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> method is called.</span></span>  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a><span data-ttu-id="9eed6-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9eed6-111">Example</span></span>  
 <span data-ttu-id="9eed6-112">O exemplo a seguir mostra como usar o <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> método para adicionar um `Order_Details` objeto para um relacionado `Orders` objeto com uma referência a um determinado `Products` objeto.</span><span class="sxs-lookup"><span data-stu-id="9eed6-112">The following example shows how to use the <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> method to add an `Order_Details` object to a related `Orders` object with a reference to a specific `Products` object.</span></span> <span data-ttu-id="9eed6-113">O <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> e <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> métodos definem as relações.</span><span class="sxs-lookup"><span data-stu-id="9eed6-113">The <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> and <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> methods define the relationships.</span></span> <span data-ttu-id="9eed6-114">Neste exemplo, as propriedades de navegação no `Order_Details` objeto são definidos explicitamente.</span><span class="sxs-lookup"><span data-stu-id="9eed6-114">In this example, the navigation properties on the `Order_Details` object are also explicitly set.</span></span>  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a><span data-ttu-id="9eed6-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9eed6-115">See Also</span></span>  
 <span data-ttu-id="9eed6-116">[WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="9eed6-116">[WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)</span></span>  
 [<span data-ttu-id="9eed6-117">Como: adicionar, modificar e excluir entidades</span><span class="sxs-lookup"><span data-stu-id="9eed6-117">How to: Add, Modify, and Delete Entities</span></span>](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md)