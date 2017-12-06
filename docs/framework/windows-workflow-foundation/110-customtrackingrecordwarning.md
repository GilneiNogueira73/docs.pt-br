---
title: 110 - CustomTrackingRecordWarning
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bc093de-be47-4ed0-983f-05b4246446fc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47f58312ec04231b05112a1049d15434c5eaff64
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="110---customtrackingrecordwarning"></a><span data-ttu-id="a85e4-102">110 - CustomTrackingRecordWarning</span><span class="sxs-lookup"><span data-stu-id="a85e4-102">110 - CustomTrackingRecordWarning</span></span>
## <a name="properties"></a><span data-ttu-id="a85e4-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a85e4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a85e4-104">Id</span><span class="sxs-lookup"><span data-stu-id="a85e4-104">Id</span></span>|<span data-ttu-id="a85e4-105">110</span><span class="sxs-lookup"><span data-stu-id="a85e4-105">110</span></span>|  
|<span data-ttu-id="a85e4-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="a85e4-106">Keywords</span></span>|<span data-ttu-id="a85e4-107">UserEvents, EndToEndMonitoring, solução de problemas, HealthMonitoring, WFTracking</span><span class="sxs-lookup"><span data-stu-id="a85e4-107">UserEvents, EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="a85e4-108">Nível</span><span class="sxs-lookup"><span data-stu-id="a85e4-108">Level</span></span>|<span data-ttu-id="a85e4-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="a85e4-109">Warning</span></span>|  
|<span data-ttu-id="a85e4-110">Canal</span><span class="sxs-lookup"><span data-stu-id="a85e4-110">Channel</span></span>|<span data-ttu-id="a85e4-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="a85e4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a85e4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a85e4-112">Description</span></span>  
 <span data-ttu-id="a85e4-113">Este evento é emitido pelo participante de rastreamento de ETW quando uma atividade em uma instância de fluxo de trabalho se emite CustomTrackingRecord com aviso nivelado</span><span class="sxs-lookup"><span data-stu-id="a85e4-113">This event is emitted by the ETW tracking participant when an activity within a workflow instance emits CustomTrackingRecord with level warning</span></span>  
  
## <a name="message"></a><span data-ttu-id="a85e4-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="a85e4-114">Message</span></span>  
 <span data-ttu-id="a85e4-115">TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityName=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Data=%9, Annotations=%10, ProfileName = %11</span><span class="sxs-lookup"><span data-stu-id="a85e4-115">TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityName=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Data=%9, Annotations=%10, ProfileName = %11</span></span>  
  
## <a name="details"></a><span data-ttu-id="a85e4-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a85e4-116">Details</span></span>  
  
|<span data-ttu-id="a85e4-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="a85e4-117">Data Item Name</span></span>|<span data-ttu-id="a85e4-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="a85e4-118">Data Item Type</span></span>|<span data-ttu-id="a85e4-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="a85e4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a85e4-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="a85e4-120">InstanceId</span></span>|<span data-ttu-id="a85e4-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="a85e4-121">xs:GUID</span></span>|<span data-ttu-id="a85e4-122">A identificação de instância para o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a85e4-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="a85e4-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="a85e4-123">RecordNumber</span></span>|<span data-ttu-id="a85e4-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="a85e4-124">xs:long</span></span>|<span data-ttu-id="a85e4-125">O número de sequência do registro emitido</span><span class="sxs-lookup"><span data-stu-id="a85e4-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="a85e4-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="a85e4-126">EventTime</span></span>|<span data-ttu-id="a85e4-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="a85e4-127">xs:dateTime</span></span>|<span data-ttu-id="a85e4-128">A hora UTC quando o evento foi emitido</span><span class="sxs-lookup"><span data-stu-id="a85e4-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="a85e4-129">Nome</span><span class="sxs-lookup"><span data-stu-id="a85e4-129">Name</span></span>|<span data-ttu-id="a85e4-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="a85e4-130">xs:string</span></span>|<span data-ttu-id="a85e4-131">O nome de CustomTrackingRecord</span><span class="sxs-lookup"><span data-stu-id="a85e4-131">The name of the CustomTrackingRecord</span></span>|  
|<span data-ttu-id="a85e4-132">ActivityName</span><span class="sxs-lookup"><span data-stu-id="a85e4-132">ActivityName</span></span>|<span data-ttu-id="a85e4-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="a85e4-133">xs:string</span></span>|<span data-ttu-id="a85e4-134">O nome da atividade que se emitiu o CustomTrackingRecord</span><span class="sxs-lookup"><span data-stu-id="a85e4-134">The name of the activity that emitted the CustomTrackingRecord</span></span>|  
|<span data-ttu-id="a85e4-135">ActivityId</span><span class="sxs-lookup"><span data-stu-id="a85e4-135">ActivityId</span></span>|<span data-ttu-id="a85e4-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="a85e4-136">xs:string</span></span>|<span data-ttu-id="a85e4-137">A identificação da atividade que se emitiu o CustomTrackingRecord</span><span class="sxs-lookup"><span data-stu-id="a85e4-137">The id of the activity that emitted the CustomTrackingRecord</span></span>|  
|<span data-ttu-id="a85e4-138">ActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="a85e4-138">ActivityInstanceId</span></span>|<span data-ttu-id="a85e4-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="a85e4-139">xs:string</span></span>|<span data-ttu-id="a85e4-140">A identificação de instância de atividade que se emitiu o CustomTrackingRecord</span><span class="sxs-lookup"><span data-stu-id="a85e4-140">The instance id of the activity that emitted the CustomTrackingRecord</span></span>|  
|<span data-ttu-id="a85e4-141">ActivityTypeName</span><span class="sxs-lookup"><span data-stu-id="a85e4-141">ActivityTypeName</span></span>|<span data-ttu-id="a85e4-142">xs:string</span><span class="sxs-lookup"><span data-stu-id="a85e4-142">xs:string</span></span>|<span data-ttu-id="a85e4-143">O nome da atividade que se emitiu o CustomTrackingRecord</span><span class="sxs-lookup"><span data-stu-id="a85e4-143">The name of the activity that emitted the CustomTrackingRecord</span></span>|  
|<span data-ttu-id="a85e4-144">Dados</span><span class="sxs-lookup"><span data-stu-id="a85e4-144">Data</span></span>|<span data-ttu-id="a85e4-145">xs:string</span><span class="sxs-lookup"><span data-stu-id="a85e4-145">xs:string</span></span>|<span data-ttu-id="a85e4-146">Os dados que foram rastreadas com esse evento.</span><span class="sxs-lookup"><span data-stu-id="a85e4-146">The data that was tracked with this event.</span></span>  <span data-ttu-id="a85e4-147">Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "dataName" type="System.String" > dataValue\</item > \< /itens >.</span><span class="sxs-lookup"><span data-stu-id="a85e4-147">The values are stored in an xml element in the format \<items>\< item  name = "dataName" type="System.String">dataValue\</item>\</items>.</span></span>  <span data-ttu-id="a85e4-148">Se nenhum dado foi controlado, a cadeia de caracteres contém \<itens / >.</span><span class="sxs-lookup"><span data-stu-id="a85e4-148">If no data was tracked then the string contains \<items/>.</span></span> <span data-ttu-id="a85e4-149">O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW.</span><span class="sxs-lookup"><span data-stu-id="a85e4-149">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="a85e4-150">Se o tamanho do evento excede os limites ETW, o evento é truncado descartando as anotações e substituindo o valor de dados com \<itens >...  \< /itens >.</span><span class="sxs-lookup"><span data-stu-id="a85e4-150">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the data value with \<items>...\</items>.</span></span>  <span data-ttu-id="a85e4-151">Os seguintes tipos são armazenados como seu valor como retornados por ToString(); cadeia de caracteres, char, bool, int, short, long, uint, ushort, ulong, System.Single, flutuante, double, System.Guid, System.DateTimeOffset, System.DateTime.</span><span class="sxs-lookup"><span data-stu-id="a85e4-151">The following types are stored as their value as returned by ToString(); string,char,bool,int,short,long,uint,ushort,ulong,System.Single,float,double,System.Guid,System.DateTimeOffset,System.DateTime.</span></span>  <span data-ttu-id="a85e4-152">Todos os outros tipos são serializados usando System.Runtime.Serialization.NetDataContractSerializer.</span><span class="sxs-lookup"><span data-stu-id="a85e4-152">All other types are serialized using System.Runtime.Serialization.NetDataContractSerializer.</span></span>|  
|<span data-ttu-id="a85e4-153">Anotações</span><span class="sxs-lookup"><span data-stu-id="a85e4-153">Annotations</span></span>|<span data-ttu-id="a85e4-154">xs:string</span><span class="sxs-lookup"><span data-stu-id="a85e4-154">xs:string</span></span>|<span data-ttu-id="a85e4-155">As anotações que foram adicionadas a este evento.</span><span class="sxs-lookup"><span data-stu-id="a85e4-155">The annotations that were added to this event.</span></span>  <span data-ttu-id="a85e4-156">Os valores são armazenados em um elemento xml no formato \<itens >\< nome do item = "annotationName" type="System.String" > annotationValue\</item > \< /itens >.</span><span class="sxs-lookup"><span data-stu-id="a85e4-156">The values are stored in an xml element in the format \<items>\< item  name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span>  <span data-ttu-id="a85e4-157">Se nenhuma anotação é especificada, em seguida, a cadeia de caracteres contém \<itens / >.</span><span class="sxs-lookup"><span data-stu-id="a85e4-157">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="a85e4-158">O tamanho do evento de ETW é limitado pelo tamanho do buffer de ETW ou pela carga máxima útil para um evento de ETW.</span><span class="sxs-lookup"><span data-stu-id="a85e4-158">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="a85e4-159">Se o tamanho do evento excede os limites ETW, o evento é truncado descartando as anotações e substituindo o valor anotação com \<itens >...  \< /itens >.</span><span class="sxs-lookup"><span data-stu-id="a85e4-159">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="a85e4-160">ProfileName</span><span class="sxs-lookup"><span data-stu-id="a85e4-160">ProfileName</span></span>|<span data-ttu-id="a85e4-161">xs:string</span><span class="sxs-lookup"><span data-stu-id="a85e4-161">xs:string</span></span>|<span data-ttu-id="a85e4-162">O nome ou o perfil de rastreamento que levam a este evento que está sendo emitido</span><span class="sxs-lookup"><span data-stu-id="a85e4-162">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="a85e4-163">HostReference</span><span class="sxs-lookup"><span data-stu-id="a85e4-163">HostReference</span></span>|<span data-ttu-id="a85e4-164">xs:string</span><span class="sxs-lookup"><span data-stu-id="a85e4-164">xs:string</span></span>|<span data-ttu-id="a85e4-165">Hospedados para serviços da Web, este campo identifica unicamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="a85e4-165">For web hosted services, this field uniquely identifies the service in the web hierarchy.</span></span>  <span data-ttu-id="a85e4-166">Seu formato é definido como ' caminho Virtual do aplicativo de nome de Site da Web &#124; Caminho Virtual do serviço &#124; ServiceName' exemplo: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124; CalculatorService'</span><span class="sxs-lookup"><span data-stu-id="a85e4-166">It's format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName' Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'</span></span>|  
|<span data-ttu-id="a85e4-167">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a85e4-167">AppDomain</span></span>|<span data-ttu-id="a85e4-168">xs:string</span><span class="sxs-lookup"><span data-stu-id="a85e4-168">xs:string</span></span>|<span data-ttu-id="a85e4-169">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a85e4-169">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|