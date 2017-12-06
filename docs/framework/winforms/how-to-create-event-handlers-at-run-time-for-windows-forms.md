---
title: "Como criar manipuladores de eventos em tempo de execução para formulários do Windows Forms"
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
- Windows Forms, event handling
- event handlers [Windows Forms], creating
- run time [Windows Forms], creating event handlers at
- examples [Windows Forms], event handling
- Button control [Windows Forms], event handlers
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 53664bcf8c776338399297687a16ec430bca128b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="8e55c-102">Como criar manipuladores de eventos em tempo de execução para formulários do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8e55c-102">How to: Create Event Handlers at Run Time for Windows Forms</span></span>
<span data-ttu-id="8e55c-103">Além de criar eventos usando o Designer de Formulários do Windows, também é possível criar um manipulador de eventos no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8e55c-103">In addition to creating events using the Windows Forms Designer, you can also create an event handler at run time.</span></span> <span data-ttu-id="8e55c-104">Essa ação permite que você conecte manipuladores de eventos com base em condições no código no tempo de execução em vez de conectá-los quando o programa inicia.</span><span class="sxs-lookup"><span data-stu-id="8e55c-104">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>  
  
### <a name="to-create-an-event-handler-at-run-time"></a><span data-ttu-id="8e55c-105">Para criar um manipulador de eventos no tempo de execução</span><span class="sxs-lookup"><span data-stu-id="8e55c-105">To create an event handler at run time</span></span>  
  
1.  <span data-ttu-id="8e55c-106">Abra o formulário no Editor de códigos ao qual deseja adicionar um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="8e55c-106">Open the form in the Code Editor that you want to add an event handler to.</span></span>  
  
2.  <span data-ttu-id="8e55c-107">Adicione um método ao seu formulário com a assinatura do método para o evento que deseja manipular.</span><span class="sxs-lookup"><span data-stu-id="8e55c-107">Add a method to your form with the method signature for the event that you want to handle.</span></span>  
  
     <span data-ttu-id="8e55c-108">Por exemplo, se você estivesse tratando o <xref:System.Windows.Forms.Control.Click> eventos de um <xref:System.Windows.Forms.Button> controle, você deve criar um método como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8e55c-108">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)  
       ' Add event handler code here.  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
    // Add event handler code here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          // Add event handler code here.  
       }  
    ```  
  
3.  <span data-ttu-id="8e55c-109">Adicione código ao manipulador de eventos conforme apropriado para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8e55c-109">Add code to the event handler as appropriate to your application.</span></span>  
  
4.  <span data-ttu-id="8e55c-110">Determine para qual formulário ou controle deseja criar um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="8e55c-110">Determine which form or control you want to create an event handler for.</span></span>  
  
5.  <span data-ttu-id="8e55c-111">Em um método na classe do formulário, adicione o código que especifica o manipulador de eventos para manipular o evento.</span><span class="sxs-lookup"><span data-stu-id="8e55c-111">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="8e55c-112">Por exemplo, o código a seguir especifica o manipulador de eventos `button1_Click` identificadores de <xref:System.Windows.Forms.Control.Click> eventos de um <xref:System.Windows.Forms.Button> controle:</span><span class="sxs-lookup"><span data-stu-id="8e55c-112">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="8e55c-113">O <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> método demonstrado no código do Visual Basic acima estabelece um manipulador de eventos de clique do botão.</span><span class="sxs-lookup"><span data-stu-id="8e55c-113">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e55c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e55c-114">See Also</span></span>  
 [<span data-ttu-id="8e55c-115">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8e55c-115">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="8e55c-116">Visão geral de manipuladores de eventos</span><span class="sxs-lookup"><span data-stu-id="8e55c-116">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 [<span data-ttu-id="8e55c-117">Solucionando problemas de manipuladores de eventos herdados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e55c-117">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)