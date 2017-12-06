---
title: Rastreamento personalizada
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71a27ffb1c18f0f5ae6f30cac432d5ffd8712b74
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-tracking"></a><span data-ttu-id="4e44c-102">Rastreamento personalizada</span><span class="sxs-lookup"><span data-stu-id="4e44c-102">Custom Tracking</span></span>
<span data-ttu-id="4e44c-103">Este exemplo demonstra como criar um participante personalizado de rastreamento e gravar o conteúdo dos dados de acompanhamento no console.</span><span class="sxs-lookup"><span data-stu-id="4e44c-103">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="4e44c-104">Além disso, o exemplo demonstra como emitir os objetos de <xref:System.Activities.Tracking.CustomTrackingRecord> preenchido com dados definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="4e44c-104">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="4e44c-105">O participante controlando console- base filtra os objetos de <xref:System.Activities.Tracking.TrackingRecord> emissores pelo fluxo de trabalho usando um objeto de perfil de rastreamento criado em código.</span><span class="sxs-lookup"><span data-stu-id="4e44c-105">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="4e44c-106">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="4e44c-106">Sample Details</span></span>  
 [!INCLUDE[wf](../../../../includes/wf-md.md)]<span data-ttu-id="4e44c-107"> fornece uma infraestrutura de rastreamento para a execução de mesmo nível de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4e44c-107"> provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="4e44c-108">O tempo de execução de rastreamento implementa uma instância de fluxo de trabalho para emitir os eventos relacionados ao ciclo de vida de fluxo de trabalho, os eventos de atividades de fluxo de trabalho e eventos personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="4e44c-108">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="4e44c-109">A tabela a seguir detalha os componentes principais de infraestrutura de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="4e44c-109">The following table details the primary components of the tracking infrastructure.</span></span>  
  
|<span data-ttu-id="4e44c-110">Componente</span><span class="sxs-lookup"><span data-stu-id="4e44c-110">Component</span></span>|<span data-ttu-id="4e44c-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="4e44c-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4e44c-112">Tempo de execução de rastreamento</span><span class="sxs-lookup"><span data-stu-id="4e44c-112">Tracking runtime</span></span>|<span data-ttu-id="4e44c-113">Fornece a infraestrutura para emitir registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="4e44c-113">Provides the infrastructure to emit tracking records.</span></span>|  
|<span data-ttu-id="4e44c-114">Participantes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="4e44c-114">Tracking participants</span></span>|<span data-ttu-id="4e44c-115">Consome os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="4e44c-115">Consumes the tracking records.</span></span> <span data-ttu-id="4e44c-116">vem de[!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] com um participante de rastreamento que grava registros de rastreamento como o rastreamento de evento para eventos do Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="4e44c-116">[!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|  
|<span data-ttu-id="4e44c-117">Controlando o perfil</span><span class="sxs-lookup"><span data-stu-id="4e44c-117">Tracking profile</span></span>|<span data-ttu-id="4e44c-118">Um mecanismo de filtragem que permite que um participante de rastreamento assine para um subconjunto de registros de rastreamento emissores de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4e44c-118">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|  
  
 <span data-ttu-id="4e44c-119">A tabela a seguir detalha os registros de rastreamento que o tempo de execução de fluxo de trabalho se emite.</span><span class="sxs-lookup"><span data-stu-id="4e44c-119">The following table details the tracking records that the workflow runtime emits.</span></span>  
  
|<span data-ttu-id="4e44c-120">Registro de Rastreamento</span><span class="sxs-lookup"><span data-stu-id="4e44c-120">Tracking Record</span></span>|<span data-ttu-id="4e44c-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="4e44c-121">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="4e44c-122">Registros de rastreamento de instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4e44c-122">Workflow instance tracking records.</span></span>|<span data-ttu-id="4e44c-123">Descreve o ciclo de vida de instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4e44c-123">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="4e44c-124">Por exemplo, um registro de instância é emitida quando o fluxo de trabalho inicia ou termina.</span><span class="sxs-lookup"><span data-stu-id="4e44c-124">For example, an instance record is emitted when the workflow starts or completes.</span></span>|  
|<span data-ttu-id="4e44c-125">Estado da atividade que acompanha registros.</span><span class="sxs-lookup"><span data-stu-id="4e44c-125">Activity state Tracking Records.</span></span>|<span data-ttu-id="4e44c-126">Detalha a execução da atividade.</span><span class="sxs-lookup"><span data-stu-id="4e44c-126">Details activity execution.</span></span> <span data-ttu-id="4e44c-127">Esses registros indicam o estado de uma atividade de fluxo de trabalho como quando uma atividade é agendada ou quando a atividade completa ou quando uma falha é lançada.</span><span class="sxs-lookup"><span data-stu-id="4e44c-127">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|  
|<span data-ttu-id="4e44c-128">Registro de ressunção do indexador.</span><span class="sxs-lookup"><span data-stu-id="4e44c-128">Bookmark resumption record.</span></span>|<span data-ttu-id="4e44c-129">Emitido sempre que um marcador em uma instância de fluxo de trabalho que é.</span><span class="sxs-lookup"><span data-stu-id="4e44c-129">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|  
|<span data-ttu-id="4e44c-130">Registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="4e44c-130">Custom Tracking Records.</span></span>|<span data-ttu-id="4e44c-131">Um autor de fluxo de trabalho pode criar registros personalizados de rastreamento e emitir os dentro da atividade personalizado.</span><span class="sxs-lookup"><span data-stu-id="4e44c-131">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|  
  
 <span data-ttu-id="4e44c-132">O participante de rastreamento assinatura para um subconjunto dos objetos emissores de <xref:System.Activities.Tracking.TrackingRecord> usando perfis de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="4e44c-132">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="4e44c-133">Um perfil de rastreamento contém consultas de rastreamento que permitem assinar para um tipo de registro específico de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="4e44c-133">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="4e44c-134">Controlar perfis pode ser especificado no código ou na configuração.</span><span class="sxs-lookup"><span data-stu-id="4e44c-134">Tracking profiles can be specified in code or in configuration.</span></span>  
  
### <a name="custom-tracking-participant"></a><span data-ttu-id="4e44c-135">Participante de rastreamento personalizada</span><span class="sxs-lookup"><span data-stu-id="4e44c-135">Custom Tracking Participant</span></span>  
 <span data-ttu-id="4e44c-136">O participante API de rastreamento permite a extensão de rastreamento com um usuário fornecido pelo participante que pode incluir a lógica personalizada para manipular os objetos de <xref:System.Activities.Tracking.TrackingRecord> emissores em tempo de execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4e44c-136">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="4e44c-137">Para gravar um participante de rastreamento o usuário deve implementar <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="4e44c-137">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="4e44c-138">Especificamente, o método de <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> precisa ser implementado por participante personalizado.</span><span class="sxs-lookup"><span data-stu-id="4e44c-138">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="4e44c-139">Este método é chamado quando <xref:System.Activities.Tracking.TrackingRecord> é emitida em tempo de execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4e44c-139">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>  
  
```csharp  
public abstract class TrackingParticipant  
{  
    protected TrackingParticipant();  
  
    public virtual TrackingProfile TrackingProfile { get; set; }  
    public abstract void Track(TrackingRecord record, TimeSpan timeout);  
}  
```  
  
 <span data-ttu-id="4e44c-140">O participante completo de rastreamento é implementado no arquivo de ConsoleTrackingParticipant.cs. O exemplo de código é o método de <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> para o participante personalizado de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="4e44c-140">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>  
  
```csharp  
protected override void Track(TrackingRecord record, TimeSpan timeout)  
{  
    ...             
    WorkflowInstanceRecord workflowInstanceRecord = record as WorkflowInstanceRecord;  
    if (workflowInstanceRecord != null)  
    {  
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,  
            " Workflow InstanceID: {0} Workflow instance state: {1}",  
            record.InstanceId, workflowInstanceRecord.State));  
    }  
  
    ActivityStateRecord activityStateRecord = record as ActivityStateRecord;  
    if (activityStateRecord != null)  
    {  
        IDictionary<String, object> variables = activityStateRecord.Variables;  
        StringBuilder vars = new StringBuilder();  
  
        if (variables.Count > 0)  
        {  
            vars.AppendLine("\n\tVariables:");  
            foreach (KeyValuePair<string, object> variable in variables)  
            {     
                vars.AppendLine(String.Format(  
                    "\t\tName: {0} Value: {1}", variable.Key, variable.Value));  
            }  
        }  
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,  
            " :Activity DisplayName: {0} :ActivityInstanceState: {1} {2}",  
                activityStateRecord.Activity.Name, activityStateRecord.State,  
            ((variables.Count > 0) ? vars.ToString() : String.Empty)));  
    }  
  
    CustomTrackingRecord customTrackingRecord = record as CustomTrackingRecord;  
  
    if ((customTrackingRecord != null) && (customTrackingRecord.Data.Count > 0))  
    {  
        ...  
    }  
    Console.WriteLine();  
  
}  
```  
  
 <span data-ttu-id="4e44c-141">O exemplo de código a seguir adiciona o participante de console para o solicitante de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4e44c-141">The following code example adds the console participant to the workflow invoker.</span></span>  
  
```csharp  
ConsoleTrackingParticipant customTrackingParticipant = new ConsoleTrackingParticipant()  
{  
    ...  
    // The tracking profile is set here, refer to Program.CS  
...  
}  
  
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());  
invoker.Extensions.Add(customTrackingParticipant);  
```  
  
### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="4e44c-142">Emitindo registros de rastreamento personalizadas</span><span class="sxs-lookup"><span data-stu-id="4e44c-142">Emitting Custom Tracking Records</span></span>  
 <span data-ttu-id="4e44c-143">Este exemplo também demonstra a capacidade de emitir objetos de <xref:System.Activities.Tracking.CustomTrackingRecord> de uma atividade personalizado de fluxo de trabalho:</span><span class="sxs-lookup"><span data-stu-id="4e44c-143">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>  
  
-   <span data-ttu-id="4e44c-144">Os objetos de <xref:System.Activities.Tracking.CustomTrackingRecord> são criados e preenchido com dados definidos pelo usuário que são desejados ser emitidos com o registro.</span><span class="sxs-lookup"><span data-stu-id="4e44c-144">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>  
  
-   <span data-ttu-id="4e44c-145">O <xref:System.Activities.Tracking.CustomTrackingRecord> é emitido, chamando o método de controle do <xref:System.Activities.ActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="4e44c-145">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>  
  
 <span data-ttu-id="4e44c-146">O exemplo a seguir demonstra como emitir objetos de <xref:System.Activities.Tracking.CustomTrackingRecord> dentro de uma atividade personalizado.</span><span class="sxs-lookup"><span data-stu-id="4e44c-146">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>  
  
```csharp  
// Create the Custom Tracking Record  
CustomTrackingRecord customRecord = new CustomTrackingRecord("OrderIn")  
{  
    Data =   
    {  
        {"OrderId", 200},  
        {"OrderDate", "20 Aug 2001"}  
    }  
};  
  
// Emit custom tracking record  
context.Track(customRecord);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="4e44c-147">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="4e44c-147">To use this sample</span></span>  
  
1.  <span data-ttu-id="4e44c-148">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de CustomTrackingSample.sln.</span><span class="sxs-lookup"><span data-stu-id="4e44c-148">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CustomTrackingSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="4e44c-149">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="4e44c-149">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="4e44c-150">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="4e44c-150">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4e44c-151">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4e44c-151">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4e44c-152">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4e44c-152">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4e44c-153">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="4e44c-153">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4e44c-154">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4e44c-154">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="4e44c-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e44c-155">See Also</span></span>  
 [<span data-ttu-id="4e44c-156">Exemplos de monitoramento do AppFabric</span><span class="sxs-lookup"><span data-stu-id="4e44c-156">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)