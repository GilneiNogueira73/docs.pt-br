---
title: "Como dar suporte à interoperabilidade COM exibindo um formulário do Windows Forms com o método ShowDialog"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop [Windows Forms], calling methods
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: 87aac8ad-3c04-43b3-9b0c-d0b00df9ee74
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f01fc82be38f7c5acb02c28960785e97a782909
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a><span data-ttu-id="4a5a5-102">Como dar suporte à interoperabilidade COM exibindo um formulário do Windows Forms com o método ShowDialog</span><span class="sxs-lookup"><span data-stu-id="4a5a5-102">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>
<span data-ttu-id="4a5a5-103">Você pode resolver problemas de interoperabilidade do modelo de objeto de componente (COM) exibindo o formulário do Windows em um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] loop de mensagem, que é criado usando o <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="4a5a5-103">You can resolve Component Object Model (COM) interoperability problems by displaying your Windows Form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which is created by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="4a5a5-104">Para fazer um formulário funcionar corretamente em um aplicativo cliente COM, você deve executá-lo em um loop de mensagem do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4a5a5-104">To make a form work correctly from a COM client application, you must run it on a Windows Forms message loop.</span></span> <span data-ttu-id="4a5a5-105">Para fazer isso, use uma das abordagens a seguir:</span><span class="sxs-lookup"><span data-stu-id="4a5a5-105">To do this, use one of the following approaches:</span></span>  
  
-   <span data-ttu-id="4a5a5-106">Use o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método para exibir o formulário do Windows;</span><span class="sxs-lookup"><span data-stu-id="4a5a5-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form;</span></span>  
  
-   <span data-ttu-id="4a5a5-107">Exiba cada Windows Form em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="4a5a5-107">Display each Windows Form on a separate thread.</span></span> <span data-ttu-id="4a5a5-108">Para obter mais informações, consulte [Como dar suporte à interoperabilidade COM exibindo cada formulário do Windows Forms em um thread separado](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).</span><span class="sxs-lookup"><span data-stu-id="4a5a5-108">For more information, see [How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="4a5a5-109">Procedimento</span><span class="sxs-lookup"><span data-stu-id="4a5a5-109">Procedure</span></span>  
 <span data-ttu-id="4a5a5-110">Usando o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método pode ser a maneira mais fácil de exibir um formulário em um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] loop de mensagem porque, de todas as abordagens, ele requer o mínimo de código para implementar.</span><span class="sxs-lookup"><span data-stu-id="4a5a5-110">Using the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method can be the easiest way to display a form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop because, of all the approaches, it requires the least code to implement.</span></span>  
  
 <span data-ttu-id="4a5a5-111">O <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método suspende o loop de mensagem do aplicativo não gerenciado e exibe o formulário como uma caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="4a5a5-111">The <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method suspends the unmanaged application's message loop and displays the form as a dialog box.</span></span> <span data-ttu-id="4a5a5-112">Como loop de mensagem o aplicativo host do foi suspenso, o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método cria um novo [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] loop de mensagem para processar mensagens do formulário.</span><span class="sxs-lookup"><span data-stu-id="4a5a5-112">Because the host application's message loop has been suspended, the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method creates a new [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop to process the form's messages.</span></span>  
  
 <span data-ttu-id="4a5a5-113">A desvantagem de usar o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método é que o formulário será aberto como uma caixa de diálogo modal.</span><span class="sxs-lookup"><span data-stu-id="4a5a5-113">The disadvantage of using the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method is that the form will be opened as a modal dialog box.</span></span> <span data-ttu-id="4a5a5-114">Esse comportamento bloqueia qualquer interface do usuário (IU) do aplicativo de chamada enquanto o Windows Form está aberto.</span><span class="sxs-lookup"><span data-stu-id="4a5a5-114">This behavior blocks any user interface (UI) in the calling application while the Windows Form is open.</span></span> <span data-ttu-id="4a5a5-115">Quando o usuário sai do formulário, o loop de mensagem [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fecha e o loop de mensagem do aplicativo anterior começa a ser executado novamente.</span><span class="sxs-lookup"><span data-stu-id="4a5a5-115">When the user exits the form, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop closes and the earlier application's message loop starts running again.</span></span>  
  
 <span data-ttu-id="4a5a5-116">Você pode criar uma biblioteca de classes do Windows Forms que tem um método para mostrar o formulário e, em seguida, compilar a biblioteca de classes para interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="4a5a5-116">You can create a class library in Windows Forms which has a method to show the form, and then build the class library for COM interop.</span></span> <span data-ttu-id="4a5a5-117">Você pode usar o arquivo DLL do Visual Basic 6.0 ou Microsoft Foundation Classes (MFC) e de qualquer um desses ambientes você pode chamar o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método para exibir o formulário.</span><span class="sxs-lookup"><span data-stu-id="4a5a5-117">You can use this DLL file from Visual Basic 6.0 or Microsoft Foundation Classes (MFC), and from either of these environments you can call the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the form.</span></span>  
  
#### <a name="to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a><span data-ttu-id="4a5a5-118">Dar suporte à interoperabilidade COM exibindo um formulário do Windows com o método ShowDialog</span><span class="sxs-lookup"><span data-stu-id="4a5a5-118">To support COM interop by displaying a windows form with the ShowDialog method</span></span>  
  
-   <span data-ttu-id="4a5a5-119">Substitua todas as chamadas para o <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> método com chamadas para o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método no seu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] componente.</span><span class="sxs-lookup"><span data-stu-id="4a5a5-119">Replace all calls to the <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> method with calls to the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method in your [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a5a5-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a5a5-120">See Also</span></span>  
 [<span data-ttu-id="4a5a5-121">Expondo componentes do .NET Framework ao COM</span><span class="sxs-lookup"><span data-stu-id="4a5a5-121">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="4a5a5-122">Como dar suporte à interoperabilidade COM exibindo cada formulário do Windows Forms em um thread separado</span><span class="sxs-lookup"><span data-stu-id="4a5a5-122">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 [<span data-ttu-id="4a5a5-123">Windows Forms e Aplicativos Não Gerenciados</span><span class="sxs-lookup"><span data-stu-id="4a5a5-123">Windows Forms and Unmanaged Applications</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)