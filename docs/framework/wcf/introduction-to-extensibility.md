---
title: "Introdução à extensibilidade"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 852d689ff3159818fb25ecfd9b6e5df6df84470c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="introduction-to-extensibility"></a><span data-ttu-id="8438c-102">Introdução à extensibilidade</span><span class="sxs-lookup"><span data-stu-id="8438c-102">Introduction to Extensibility</span></span>
<span data-ttu-id="8438c-103">O [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] modelo de aplicativo é projetado para resolver a maior parte dos requisitos de comunicação de qualquer aplicativo distribuído.</span><span class="sxs-lookup"><span data-stu-id="8438c-103">The [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application model is designed to solve the greater part of the communication requirements of any distributed application.</span></span> <span data-ttu-id="8438c-104">Mas sempre há cenários em que o modelo de aplicativo padrão e implementações de fornecido pelo sistema não têm suporte.</span><span class="sxs-lookup"><span data-stu-id="8438c-104">But there are always scenarios that the default application model and system-provided implementations do not support.</span></span> <span data-ttu-id="8438c-105">O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modelo de extensibilidade destina-se para dar suporte a cenários personalizados, permitindo que você modificar o comportamento do sistema em cada nível, até mesmo para o ponto de substituir o modelo de aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="8438c-105">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] extensibility model is intended to support custom scenarios by enabling you to modify system behavior at every level, even to the point of replacing the entire application model.</span></span> <span data-ttu-id="8438c-106">Este tópico descreve as várias áreas de extensão e aponta para obter mais informações sobre cada um.</span><span class="sxs-lookup"><span data-stu-id="8438c-106">This topic outlines the various areas of extension and points to more information about each.</span></span>  
  
## <a name="areas-to-extend"></a><span data-ttu-id="8438c-107">Áreas para estender</span><span class="sxs-lookup"><span data-stu-id="8438c-107">Areas to Extend</span></span>  
 <span data-ttu-id="8438c-108">Você pode estender:</span><span class="sxs-lookup"><span data-stu-id="8438c-108">You can extend:</span></span>  
  
-   <span data-ttu-id="8438c-109">O tempo de execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8438c-109">The application runtime.</span></span> <span data-ttu-id="8438c-110">Isso estende a distribuição e o processamento de mensagens para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8438c-110">This extends the dispatching and the processing of messages for the application.</span></span> <span data-ttu-id="8438c-111">Essa área também inclui estender o sistema de segurança, o sistema de metadados, o sistema de serialização e as associações e elementos que se conectam o aplicativos com o sistema de canais subjacente de associação.</span><span class="sxs-lookup"><span data-stu-id="8438c-111">This area also includes extending the security system, the metadata system, the serialization system, and the bindings and binding elements that connect the application with the underlying channel system.</span></span>  
  
-   <span data-ttu-id="8438c-112">O canal e o tempo de execução do canal.</span><span class="sxs-lookup"><span data-stu-id="8438c-112">The channel and channel runtime.</span></span> <span data-ttu-id="8438c-113">Isso estende o sistema que funciona no nível da mensagem, fornecendo o protocolo de transporte e suporte a codificação.</span><span class="sxs-lookup"><span data-stu-id="8438c-113">This extends the system that functions at the message level, providing protocol, transport, and encoding support.</span></span>  
  
-   <span data-ttu-id="8438c-114">O tempo de execução do host.</span><span class="sxs-lookup"><span data-stu-id="8438c-114">The host runtime.</span></span> <span data-ttu-id="8438c-115">Isso estende a relação entre o domínio de aplicativo de hospedagem para o tempo de execução do aplicativo e de canal.</span><span class="sxs-lookup"><span data-stu-id="8438c-115">This extends the relationship of the hosting application domain to the channel and application runtime.</span></span>  
  
### <a name="extending-the-application-runtime"></a><span data-ttu-id="8438c-116">Estendendo o tempo de execução do aplicativo</span><span class="sxs-lookup"><span data-stu-id="8438c-116">Extending the Application Runtime</span></span>  
 <span data-ttu-id="8438c-117">Em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos, há uma distinção entre as mensagens destinadas a um canal correspondente e que são destinados para o aplicativo em si.</span><span class="sxs-lookup"><span data-stu-id="8438c-117">In [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications, there is a distinction between messages that are destined for a corresponding channel and messages that are destined for the application itself.</span></span> <span data-ttu-id="8438c-118">Mensagens do canal de suportam a algumas funcionalidades relacionadas de canal, como estabelecer uma conversa segura ou estabelecer uma sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="8438c-118">Channel messages support some channel-related functionality, such as establishing a secure conversation or establishing a reliable session.</span></span> <span data-ttu-id="8438c-119">Essas mensagens não estão disponíveis para o tempo de execução do aplicativo; eles são processados antes que a camada de aplicativo está envolvida.</span><span class="sxs-lookup"><span data-stu-id="8438c-119">These messages are not available to the application runtime; they are processed before the application layer is involved.</span></span>  
  
 <span data-ttu-id="8438c-120">As mensagens de aplicativo contém dados que são destinados a um cliente ou operação de serviço que você ou seu cliente tiver sido criado.</span><span class="sxs-lookup"><span data-stu-id="8438c-120">Application messages contain data that is destined for a client or service operation that you or your customer has created.</span></span> <span data-ttu-id="8438c-121">Essas mensagens estão disponíveis para o sistema de extensão do nível do aplicativo no formato de mensagem ou de objeto, dependendo das suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="8438c-121">These messages are available to the application-level extension system in message or object form, depending upon your needs.</span></span>  
  
 <span data-ttu-id="8438c-122">Todas as mensagens passam por meio do sistema de canal. somente as mensagens de aplicativo são passadas do sistema de canal para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8438c-122">All messages pass through the channel system; only application messages are passed from the channel system into the application.</span></span> <span data-ttu-id="8438c-123">Para criar a nova funcionalidade no nível do canal, você deve estender o sistema de canal.</span><span class="sxs-lookup"><span data-stu-id="8438c-123">To create new channel-level functionality, you must extend the channel system.</span></span> <span data-ttu-id="8438c-124">Para criar a nova funcionalidade no nível do aplicativo, você deve estender o tempo de execução do serviço ou cliente (distribuidores e fábricas de canais, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="8438c-124">To create new application-level functionality, you must extend the service or client runtime (dispatchers and channel factories, respectively).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="8438c-125">Estendendo o tempo de execução do aplicativo, consulte [estendendo ServiceHost e a camada de modelo de serviço](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).</span><span class="sxs-lookup"><span data-stu-id="8438c-125"> extending the application runtime, see [Extending ServiceHost and the Service Model Layer](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).</span></span>  
  
#### <a name="extending-security"></a><span data-ttu-id="8438c-126">Segurança estendida</span><span class="sxs-lookup"><span data-stu-id="8438c-126">Extending Security</span></span>  
 <span data-ttu-id="8438c-127">Para criar os mecanismos de segurança personalizada, como tokens e credenciais, você deve estender o sistema de segurança.</span><span class="sxs-lookup"><span data-stu-id="8438c-127">To build custom security mechanisms such as tokens and credentials, you must extend the security system.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="8438c-128">[Estendendo a segurança](../../../docs/framework/wcf/extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="8438c-128"> [Extending Security](../../../docs/framework/wcf/extending/extending-security.md).</span></span>  
  
#### <a name="extending-metadata"></a><span data-ttu-id="8438c-129">Estendendo metadados</span><span class="sxs-lookup"><span data-stu-id="8438c-129">Extending Metadata</span></span>  
 <span data-ttu-id="8438c-130">Para expor seus metadados em diferente do padrão, você deve estender o sistema de metadados.</span><span class="sxs-lookup"><span data-stu-id="8438c-130">To expose your metadata in differently than the default, you must extend the metadata system.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="8438c-131">[Estendendo o sistema de metadados](../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span><span class="sxs-lookup"><span data-stu-id="8438c-131"> [Extending the Metadata System](../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span></span>  
  
#### <a name="extending-serialization"></a><span data-ttu-id="8438c-132">Estendendo a serialização</span><span class="sxs-lookup"><span data-stu-id="8438c-132">Extending Serialization</span></span>  
 <span data-ttu-id="8438c-133">Para construir decodificadores personalizados, fornecer substitutos de dados ou outras tarefas que envolvem a personalização de dados transferidos, você deve estender o sistema de serialização.</span><span class="sxs-lookup"><span data-stu-id="8438c-133">To build custom encoders, provide data surrogates, or other work involving the customization of transferred data, you must extend the serialization system.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="8438c-134">[Estendendo codificadores e serializadores](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md).</span><span class="sxs-lookup"><span data-stu-id="8438c-134"> [Extending Encoders and Serializers](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md).</span></span>  
  
#### <a name="extending-bindings"></a><span data-ttu-id="8438c-135">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="8438c-135">Extending Bindings</span></span>  
 <span data-ttu-id="8438c-136">Para associar os canais de transporte ou protocolo da camada de aplicativo, você deve estender o sistema de associação.</span><span class="sxs-lookup"><span data-stu-id="8438c-136">To associate transport or protocol channels with the application layer, you must extend the binding system.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="8438c-137">[Estendendo associações](../../../docs/framework/wcf/extending/extending-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="8438c-137"> [Extending Bindings](../../../docs/framework/wcf/extending/extending-bindings.md).</span></span>  
  
### <a name="extending-the-channel-system"></a><span data-ttu-id="8438c-138">Estendendo o sistema de canal</span><span class="sxs-lookup"><span data-stu-id="8438c-138">Extending the Channel System</span></span>  
 <span data-ttu-id="8438c-139">Para criar canais que oferecem suporte a transportes personalizados ou funcionalidade de protocolo, consulte [estendendo a camada do canal](../../../docs/framework/wcf/extending/extending-the-channel-layer.md).</span><span class="sxs-lookup"><span data-stu-id="8438c-139">To create channels that support custom transports or protocol functionality, see [Extending the Channel Layer](../../../docs/framework/wcf/extending/extending-the-channel-layer.md).</span></span>  
  
### <a name="extending-the-service-hosting-system"></a><span data-ttu-id="8438c-140">Estendendo o serviço de sistema de hospedagem</span><span class="sxs-lookup"><span data-stu-id="8438c-140">Extending the Service Hosting System</span></span>  
 <span data-ttu-id="8438c-141">Para modificar o modelo de aplicativo de todo o serviço, você deve estender <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="8438c-141">To modify the service-wide application model, you must extend <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> class.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="8438c-142">[Estendendo ServiceHost e a camada de modelo de serviço](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).</span><span class="sxs-lookup"><span data-stu-id="8438c-142"> [Extending ServiceHost and the Service Model Layer](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).</span></span>  
  
 <span data-ttu-id="8438c-143">Para modificar a relação entre o domínio de aplicativo de hospedagem e o host de serviço, você deve estender o <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="8438c-143">To modify the relationship between the hosting application domain and the service host, you must extend the <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> class.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="8438c-144">[Estendendo a hospedagem com ServiceHostFactory](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md).</span><span class="sxs-lookup"><span data-stu-id="8438c-144"> [Extending Hosting Using ServiceHostFactory](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8438c-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8438c-145">See Also</span></span>  
 <span data-ttu-id="8438c-146">[Extending WCF](../../../docs/framework/wcf/extending/extending-wcf.md) (Estendendo o WCF)</span><span class="sxs-lookup"><span data-stu-id="8438c-146">[Extending WCF](../../../docs/framework/wcf/extending/extending-wcf.md)</span></span>