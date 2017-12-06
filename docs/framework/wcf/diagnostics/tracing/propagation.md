---
title: "Propagação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a993ec836417906229e47b7f415f4aee8b1a9eb1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="propagation"></a><span data-ttu-id="55f74-102">Propagação</span><span class="sxs-lookup"><span data-stu-id="55f74-102">Propagation</span></span>
<span data-ttu-id="55f74-103">Este tópico descreve a propagação de atividade no [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] modelo de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="55f74-103">This topic describes activity propagation in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model.</span></span>  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a><span data-ttu-id="55f74-104">Usando a propagação para correlacionar atividades entre pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="55f74-104">Using Propagation to Correlate Activities Across Endpoints</span></span>  
 <span data-ttu-id="55f74-105">Propagação fornece que ao usuário uma correlação direta de erro rastreamentos para a mesma unidade de processamento entre pontos de extremidade do aplicativo, por exemplo, uma solicitação.</span><span class="sxs-lookup"><span data-stu-id="55f74-105">Propagation provides the user with direct correlation of error traces for the same unit of processing across application endpoints, for example, a request.</span></span> <span data-ttu-id="55f74-106">Emitido em diferentes pontos de extremidade para a mesma unidade de processamento de erros são agrupados na mesma atividade, mesmo em domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="55f74-106">Errors emitted at different endpoints for the same unit of processing are grouped in the same activity, even across application domains.</span></span> <span data-ttu-id="55f74-107">Isso é feito por meio de propagação de ID de atividade nos cabeçalhos da mensagem.</span><span class="sxs-lookup"><span data-stu-id="55f74-107">This is done through propagation of the activity ID in the message headers.</span></span> <span data-ttu-id="55f74-108">Portanto, se um cliente de tempo limite devido a um erro interno no servidor, ambos os erros aparecem na mesma atividade de correlação direta.</span><span class="sxs-lookup"><span data-stu-id="55f74-108">Therefore, if a client times out because of an internal error in the server, both errors appear in the same activity for direct correlation.</span></span>  
  
 <span data-ttu-id="55f74-109">Para fazer isso, use o `ActivityTracing` configuração como demonstrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="55f74-109">To do this, use the `ActivityTracing` setting as demonstrated in the previous example.</span></span> <span data-ttu-id="55f74-110">Além disso, defina o `propagateActivity` de atributo para o `System.ServiceModel` em todos os pontos de extremidade de origem do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="55f74-110">In addition, set the `propagateActivity` attribute for the `System.ServiceModel` trace source at all endpoints.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 <span data-ttu-id="55f74-111">Propagação de atividade é uma funcionalidade configurável que faz com que [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] para adicionar um cabeçalho para as mensagens de saída, que inclui a ID de atividade no TLS.</span><span class="sxs-lookup"><span data-stu-id="55f74-111">Activity propagation is a configurable capability that causes [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] to add a header to outbound messages, which includes the activity ID on the TLS.</span></span> <span data-ttu-id="55f74-112">Incluindo isso em rastreamentos subsequentes no lado do servidor, podemos pode correlacionar atividades do cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="55f74-112">By including this on subsequent traces on the server side, we can correlate client and server activities.</span></span>  
  
## <a name="propagation-definition"></a><span data-ttu-id="55f74-113">Definição de propagação</span><span class="sxs-lookup"><span data-stu-id="55f74-113">Propagation Definition</span></span>  
 <span data-ttu-id="55f74-114">GAId da atividade M é propagada para a atividade N se todas as seguintes condições se aplicarem.</span><span class="sxs-lookup"><span data-stu-id="55f74-114">Activity M’s gAId is propagated to activity N if all of the following conditions apply.</span></span>  
  
-   <span data-ttu-id="55f74-115">N é criado devido a M</span><span class="sxs-lookup"><span data-stu-id="55f74-115">N is created because of M</span></span>  
  
-   <span data-ttu-id="55f74-116">GAId do M é conhecido por N</span><span class="sxs-lookup"><span data-stu-id="55f74-116">M’s gAId is known to N</span></span>  
  
-   <span data-ttu-id="55f74-117">GAId do N é igual ao gAId do M.</span><span class="sxs-lookup"><span data-stu-id="55f74-117">N's gAId is equal to M’s gAId.</span></span>  
  
 <span data-ttu-id="55f74-118">O gAId é propagada por meio do cabeçalho da mensagem ActivityId, conforme ilustrado no seguinte esquema XML.</span><span class="sxs-lookup"><span data-stu-id="55f74-118">The gAId is propagated through the ActivityId message header, as illustrated in the following XML schema.</span></span>  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 <span data-ttu-id="55f74-119">Este é um exemplo do cabeçalho da mensagem.</span><span class="sxs-lookup"><span data-stu-id="55f74-119">The following is an example of the message header.</span></span>  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"     
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"   
  
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous  
          </a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a><span data-ttu-id="55f74-120">Propagação e limites de atividade</span><span class="sxs-lookup"><span data-stu-id="55f74-120">Propagation and Activity Boundaries</span></span>  
 <span data-ttu-id="55f74-121">Quando a ID da atividade é propagada por pontos de extremidade, o receptor da mensagem emite um início e parada rastreamentos com essa ID de atividade (propagadas).</span><span class="sxs-lookup"><span data-stu-id="55f74-121">When the activity ID is propagated across endpoints, the message receiver emits a Start and Stop traces with that (propagated) activity ID.</span></span> <span data-ttu-id="55f74-122">Portanto, há um rastreamento de início e parada com que gAId em cada origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="55f74-122">Therefore, there is a Start and Stop trace with that gAId from each trace source.</span></span> <span data-ttu-id="55f74-123">Se os pontos de extremidade estão no mesmo processo e usam o mesmo nome de origem de rastreamento, são criados vários iniciar e parar com o mesmo layout (gAId mesmo, mesma origem de rastreamento, mesmo processo).</span><span class="sxs-lookup"><span data-stu-id="55f74-123">If the endpoints are in the same process and use the same trace source name, multiple Start and Stop with the same lAId (same gAId, same trace source, same process) are created.</span></span>  
  
## <a name="synchronization"></a><span data-ttu-id="55f74-124">Sincronização</span><span class="sxs-lookup"><span data-stu-id="55f74-124">Synchronization</span></span>  
 <span data-ttu-id="55f74-125">Para sincronizar os eventos em pontos de extremidade que são executados em computadores diferentes, um CorrelationId é adicionado ao cabeçalho da ActivityId é propagado de mensagens.</span><span class="sxs-lookup"><span data-stu-id="55f74-125">To synchronize events across endpoints that run on different machines, a CorrelationId is added to the ActivityId header that is propagated in messages.</span></span> <span data-ttu-id="55f74-126">Ferramentas podem usá-la para sincronizar os eventos em máquinas com discrepância de relógio.</span><span class="sxs-lookup"><span data-stu-id="55f74-126">Tools can use this ID to synchronize events across machines with clock discrepancy.</span></span> <span data-ttu-id="55f74-127">Especificamente, a ferramenta do Visualizador de rastreamento de serviço usa essa ID para mostrar os fluxos de mensagens entre pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="55f74-127">Specifically, the Service Trace Viewer tool uses this ID for showing message flows between endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f74-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55f74-128">See Also</span></span>  
 [<span data-ttu-id="55f74-129">Configurando o rastreamento</span><span class="sxs-lookup"><span data-stu-id="55f74-129">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="55f74-130">Usando o Visualizador de Rastreamento de Serviço para exibir rastreamentos correlacionados e solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="55f74-130">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="55f74-131">Cenários de rastreamento ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="55f74-131">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 <span data-ttu-id="55f74-132">[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) (Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe))</span><span class="sxs-lookup"><span data-stu-id="55f74-132">[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)</span></span>