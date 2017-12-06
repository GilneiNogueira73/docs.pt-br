---
title: "Diferenças de funcionalidades em fila no Windows Vista, Windows Server 2003, e no Windows XP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 669c6be6756d79b30266c9fda0909fedc71aeae3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a><span data-ttu-id="cfcbb-102">Diferenças de funcionalidades em fila no Windows Vista, Windows Server 2003, e no Windows XP</span><span class="sxs-lookup"><span data-stu-id="cfcbb-102">Differences in Queuing Features in Windows Vista, Windows Server 2003, and Windows XP</span></span>
<span data-ttu-id="cfcbb-103">Este tópico resume as diferenças entre o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] filas de recurso entre [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cfcbb-103">This topic summarizes the differences in the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] queues feature between [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], and [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span></span>  
  
## <a name="application-specific-dead-letter-queue"></a><span data-ttu-id="cfcbb-104">Fila de mensagens mortas específicas do aplicativo</span><span class="sxs-lookup"><span data-stu-id="cfcbb-104">Application-Specific Dead-Letter Queue</span></span>  
 <span data-ttu-id="cfcbb-105">Mensagens em fila podem permanecer na fila indefinidamente se o aplicativo de recebimento não lê-los de maneira oportuna.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-105">Queued messages can remain in the queue indefinitely if the receiving application does not read them in a timely fashion.</span></span> <span data-ttu-id="cfcbb-106">Esse comportamento não é recomendado se as mensagens são sensíveis ao tempo.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-106">This behavior is not advisable if the messages are time-sensitive.</span></span> <span data-ttu-id="cfcbb-107">Mensagens de detecção de hora têm um `TimeToLive` propriedade definida na associação em fila.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-107">Time-sensitive messages have a `TimeToLive` property set in the queued binding.</span></span> <span data-ttu-id="cfcbb-108">Essa propriedade indica quanto tempo as mensagens podem ficar na fila antes de expirarem.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-108">This property indicates how long the messages can be in the queue before they expire.</span></span> <span data-ttu-id="cfcbb-109">As mensagens expiradas são enviadas para uma fila especial chamada fila de mensagens mortas.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-109">Expired messages are sent to a special queue called the dead-letter queue.</span></span> <span data-ttu-id="cfcbb-110">Uma mensagem também pode terminar em uma fila de mensagens mortas por outros motivos, como exceder uma cota de fila ou devido a uma falha de autenticação.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-110">A message can also end up in a dead-letter queue for other reasons, such as exceeding a queue quota or experiencing an authentication failure.</span></span>  
  
 <span data-ttu-id="cfcbb-111">Normalmente, uma única fila de mensagens mortas de todo o sistema existe para todos os aplicativos em fila que compartilham um Gerenciador de fila.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-111">Typically, a single system-wide dead-letter queue exists for all queued applications that share a queue manager.</span></span> <span data-ttu-id="cfcbb-112">Uma fila de mensagens mortas para cada aplicativo permite melhor isolamento entre aplicativos em fila que compartilham um Gerenciador de fila, permitindo que esses aplicativos especificar sua própria fila de mensagens mortas específicas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-112">A dead-letter queue for each application enables better isolation between queued applications that share a queue manager by allowing these applications to specify their own application-specific dead-letter queue.</span></span> <span data-ttu-id="cfcbb-113">Tem um aplicativo que compartilha uma fila de mensagens mortas com outros aplicativos procurar a fila para localizar as mensagens que se aplicam a ele.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-113">An application that shares a dead-letter queue with other applications has to browse the queue to find messages that are applicable to it.</span></span> <span data-ttu-id="cfcbb-114">Com uma fila de mensagens mortas específicas do aplicativo, o aplicativo pode ter certeza de que todas as mensagens na fila de mensagens mortas são aplicáveis a ele.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-114">With an application-specific dead-letter queue, the application can be assured that all messages in its dead-letter queue are applicable to it.</span></span>  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)]<span data-ttu-id="cfcbb-115">fornece para filas de mensagens mortas específicas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-115"> provides for application-specific dead-letter queues.</span></span> <span data-ttu-id="cfcbb-116">Filas de mensagens mortas específicas do aplicativo não estão disponíveis em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)], e os aplicativos devem usar a fila de mensagens mortas de todo o sistema.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-116">Application-specific dead-letter queues are not available in [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)], and applications must use the system-wide dead-letter queue.</span></span>  
  
## <a name="poison-message-handling"></a><span data-ttu-id="cfcbb-117">Tratamento de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="cfcbb-117">Poison-Message Handling</span></span>  
 <span data-ttu-id="cfcbb-118">Uma mensagem suspeita é uma mensagem que excedeu o número máximo de tentativas de entrega para o aplicativo receptor.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-118">A poison message is a message that has exceeded the maximum number of delivery attempts to the receiving application.</span></span> <span data-ttu-id="cfcbb-119">Essa situação pode surgir quando um aplicativo que lê uma mensagem de uma fila transacional não é possível processar a mensagem imediatamente devido a erros.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-119">This situation can arise when an application that reads a message from a transactional queue cannot process the message immediately because of errors.</span></span> <span data-ttu-id="cfcbb-120">Se o aplicativo anula a transação na qual a mensagem na fila foi recebida, ele retorna a mensagem à fila.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-120">If the application aborts the transaction in which the queued message was received, it returns the message to the queue.</span></span> <span data-ttu-id="cfcbb-121">Em seguida, o aplicativo tenta recuperar a mensagem novamente em uma nova transação.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-121">The application then tries to retrieve the message again in a new transaction.</span></span> <span data-ttu-id="cfcbb-122">Se o problema que causou o erro não for corrigido, o aplicativo receptor pode preso em um loop de recebimento e anule a mesma mensagem até que ele excede o número máximo de tentativas de entrega e resultados de uma mensagem suspeita.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-122">If the problem that causes the error is not corrected, the receiving application can get stuck in a loop receiving and aborting the same message until it exceeds the maximum number of delivery attempts, and a poison message results.</span></span>  
  
 <span data-ttu-id="cfcbb-123">As principais diferenças entre o enfileiramento de mensagens (MSMQ) em [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] que são relevantes para tratamento suspeita incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="cfcbb-123">The key differences between Message Queuing (MSMQ) on [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], and [!INCLUDE[wxp](../../../../includes/wxp-md.md)] that are relevant to poison handling include the following:</span></span>  
  
-   <span data-ttu-id="cfcbb-124">O MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] suporta subfilas, enquanto [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] não oferecem suporte a subfilas.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-124">MSMQ in [!INCLUDE[wv](../../../../includes/wv-md.md)] supports subqueues, while [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)] do not support subqueues.</span></span> <span data-ttu-id="cfcbb-125">Subfilas são usadas no tratamento de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-125">Subqueues are used in poison-message handling.</span></span> <span data-ttu-id="cfcbb-126">As filas de repetição e a fila de suspeita são as subfilas para a fila de aplicativo que é criado com base nas configurações de manipulação de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-126">The retry queues and the poison queue are subqueues to the application queue that is created based on the poison-message handling settings.</span></span> <span data-ttu-id="cfcbb-127">O `MaxRetryCycles` determina quantas Repita subfilas para criar.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-127">The `MaxRetryCycles` dictates how many retry subqueues to create.</span></span> <span data-ttu-id="cfcbb-128">Portanto, quando executado em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` são ignorados e `ReceiveErrorHandling.Move` não é permitido.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-128">Therefore, when running on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` are ignored and `ReceiveErrorHandling.Move` is not allowed.</span></span>  
  
-   <span data-ttu-id="cfcbb-129">O MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] suporta negativo confirmação, enquanto [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] não.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-129">MSMQ in [!INCLUDE[wv](../../../../includes/wv-md.md)] supports negative acknowledgment, while [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)] do not.</span></span> <span data-ttu-id="cfcbb-130">Uma confirmação negativa do Gerenciador de fila de recebimento faz com que o Gerenciador de fila de envio colocar a mensagem rejeitada na fila de mensagens mortas.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-130">A negative acknowledgment from the receiving queue manager causes the sending queue manager to place the rejected message in the dead-letter queue.</span></span> <span data-ttu-id="cfcbb-131">Como tal, `ReceiveErrorHandling.Reject` não é permitido com [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cfcbb-131">As such, `ReceiveErrorHandling.Reject` is not allowed with [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span></span>  
  
-   <span data-ttu-id="cfcbb-132">O MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] dá suporte a uma propriedade de mensagem que mantém uma contagem do número de tempos de entrega de mensagens é tentada.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-132">MSMQ in [!INCLUDE[wv](../../../../includes/wv-md.md)] supports a message property that keeps count of the number of times message delivery is attempted.</span></span> <span data-ttu-id="cfcbb-133">Essa propriedade de contagem de anulação não está disponível em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cfcbb-133">This abort count property is not available on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="cfcbb-134">mantém a contagem de anulação na memória, portanto, é possível que essa propriedade não pode conter um valor exato quando a mesma mensagem é lida por mais de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço em uma Web farm.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-134"> maintains the abort count in memory, so it is possible that this property may not contain an accurate value when the same message is read by more than one [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service in a Web farm.</span></span>  
  
## <a name="remote-transactional-read"></a><span data-ttu-id="cfcbb-135">Leitura transacional remota</span><span class="sxs-lookup"><span data-stu-id="cfcbb-135">Remote Transactional Read</span></span>  
 <span data-ttu-id="cfcbb-136">MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] dá suporte a leituras transacionais remotas.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-136">MSMQ on [!INCLUDE[wv](../../../../includes/wv-md.md)] supports remote transactional reads.</span></span> <span data-ttu-id="cfcbb-137">Isso permite que um aplicativo que está lendo de uma fila para ser hospedado em um computador diferente do computador no qual a fila está hospedada.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-137">This allows an application that is reading from a queue to be hosted on a computer that is different from the computer on which the queue is hosted.</span></span> <span data-ttu-id="cfcbb-138">Isso garante a capacidade de ter um farm de serviços de leitura de uma fila central, o que aumenta a produtividade geral do sistema.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-138">This ensures the ability to have a farm of services reading from a central queue, which increases the overall throughput of the system.</span></span> <span data-ttu-id="cfcbb-139">Ele também garante que, se ocorrer uma falha ao ler e processar a mensagem, a transação será revertida e a mensagem permanece na fila para processamento posterior.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-139">It also ensures that if a failure occurs when reading and processing the message, the transaction rolls back and the message remains in the queue for later processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfcbb-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfcbb-140">See Also</span></span>  
 [<span data-ttu-id="cfcbb-141">Usando filas de mensagens mortas para lidar com falhas de transferência de mensagem</span><span class="sxs-lookup"><span data-stu-id="cfcbb-141">Using Dead-Letter Queues to Handle Message Transfer Failures</span></span>](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 [<span data-ttu-id="cfcbb-142">Manipulação de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="cfcbb-142">Poison Message Handling</span></span>](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)