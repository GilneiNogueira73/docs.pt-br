---
title: Decodificador de mensagens
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b0147049a988a8fa2d0721da39f1d9c37278803
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="message-encoding"></a><span data-ttu-id="10661-102">Decodificador de mensagens</span><span class="sxs-lookup"><span data-stu-id="10661-102">Message Encoding</span></span>
<span data-ttu-id="10661-103">Codificação é o processo de transformar um conjunto de caracteres Unicode em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="10661-103">Encoding is the process of transforming a set of Unicode characters into a sequence of bytes.</span></span> <span data-ttu-id="10661-104">Decodificação de é o processo inverso.</span><span class="sxs-lookup"><span data-stu-id="10661-104">Decoding is the reverse process.</span></span> <span data-ttu-id="10661-105">Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: texto, binária e mecanismo de otimização de transmissão mensagem (MTOM).</span><span class="sxs-lookup"><span data-stu-id="10661-105">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="10661-106">O `binaryMessageEncoding` seção de configuração especifica o caractere de codificação e a mensagem de controle de versão usado para mensagens XML baseadas em binário.</span><span class="sxs-lookup"><span data-stu-id="10661-106">The `binaryMessageEncoding` configuration section specifies the character encoding and message versioning used for binary-based XML messages.</span></span> <span data-ttu-id="10661-107">O codificador de mensagem binária codifica mensagens do Windows Communication Foundation (WCF) em binário no fio.</span><span class="sxs-lookup"><span data-stu-id="10661-107">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="10661-108">Embora essa codificação resulta em muito rápido transmissão de mensagens, interoperabilidade com base em WS-* padrões serão perdidos.</span><span class="sxs-lookup"><span data-stu-id="10661-108">While this encoding results in very fast transmission of messages, interoperability based on the WS-* standards is lost.</span></span>  
  
 <span data-ttu-id="10661-109">O `mtomMessageEncoding` seção de configuração especifica o caractere de codificação e a mensagem de controle de versão usada para uma mensagem usando uma codificação de mecanismo de otimização de transmissão da mensagem (MTOM).</span><span class="sxs-lookup"><span data-stu-id="10661-109">The `mtomMessageEncoding` configuration section specifies the character encoding and message versioning used for a message using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="10661-110">(MTOM) é uma tecnologia eficiente para transmitir dados binários em mensagens do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="10661-110">(MTOM) is an efficient technology for transmitting binary data in Windows Communication Foundation (WCF) messages.</span></span> <span data-ttu-id="10661-111">O codificador MTOM tenta obter um equilíbrio entre eficiência e interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="10661-111">The MTOM encoder attempts to strike a balance between efficiency and interoperability.</span></span> <span data-ttu-id="10661-112">A codificação de MTOM transmite a maioria dos XML no formato textual, mas otimiza o transmiti-los como blocos grandes de dados binários-é, sem conversão de texto.</span><span class="sxs-lookup"><span data-stu-id="10661-112">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to text.</span></span>  
  
 <span data-ttu-id="10661-113">O `textMessageEncoding` seção de configuração especifica um codificador de texto usado para criar mensagens de baseado em texto na conexão.</span><span class="sxs-lookup"><span data-stu-id="10661-113">The `textMessageEncoding` configuration section specifies a text encoder used to create text-based messages on the wire.</span></span> <span data-ttu-id="10661-114">Produzido por esse codificador de mensagens são adequadas para WS-* com base em interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="10661-114">Messages produced by this encoder are suitable for WS-* based interop.</span></span> <span data-ttu-id="10661-115">Serviço Web ou cliente de serviço Web geralmente pode entender XML textual.</span><span class="sxs-lookup"><span data-stu-id="10661-115">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="10661-116">No entanto, a transmissão de grandes blocos de dados binários como texto é o método menos eficiente para codificação de mensagens XML</span><span class="sxs-lookup"><span data-stu-id="10661-116">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10661-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10661-117">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <span data-ttu-id="10661-118">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="10661-118">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="10661-119">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="10661-119">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="10661-120">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="10661-120">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="10661-121">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="10661-121">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="10661-122">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="10661-122">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)