---
title: Atividades de fluxo de controle em WF
ms.date: 03/30/2017
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
ms.openlocfilehash: bcbb12210af2d0172977dca6f81355031baa043a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512993"
---
# <a name="control-flow-activities-in-wf"></a>Atividades de fluxo de controle em WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] fornece várias atividades para o fluxo de controle de execução dentro de um fluxo de trabalho. Algumas dessas atividades (como `Switch` e `If`) implementar estruturas semelhantes aos ambientes, como o Visual c#, enquanto outros de programação de controle de fluxo (como `Pick`) novas estruturas de programação de modelo.  
  
 Observe que quando atividades como `Parallel` e atividades filhos de cronograma de atividades de `ParallelForEach` várias para a execução simultaneamente, somente um único segmento é usado para um fluxo de trabalho. Cada atividade filho dessas atividades executa seqüencialmente e as atividades sucessivas não executam até atividades anteriores completa ou vão ociosa. Como resultado, essas atividades são mais úteis para aplicativos que potencialmente em vários bloquear atividades deve executar em uma forma intercalada. Se nenhuma das atividades filhos dessas atividades vão ociosa, uma atividade de `Parallel` apenas executa como uma atividade de `Sequence` , e uma atividade de `ParallelForEach` apenas executa como uma atividade de `ForEach` . Se, no entanto, as atividades assíncronos (como atividades que derivam de <xref:System.Activities.AsyncCodeActivity>) ou as atividades de mensagem são usadas, o controle irá passar a ramificação seguir quando as espera por filhos de atividade para que a mensagem a ser recebidos ou seu trabalho assíncrono está concluído.  
  
## <a name="flow-control-activities"></a>Atividades de controle de fluxo  
  
|Atividade|Descrição|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.DoWhile>|Executa as atividades contidas uma vez e continua a fazer isso quando a condição é `true`.|  
|<xref:System.Activities.Statements.ForEach%601>|Executa uma declaração inserido em ordem para cada elemento em uma coleção. <xref:System.Activities.Statements.ForEach%601> é semelhante a palavra-chave `foreach`, mas é implementado como uma atividade em vez de uma declaração de idioma.|  
|<xref:System.Activities.Statements.If>|Executes continha atividades se uma condição é `true`, e pode executar as atividades contidas na propriedade de <xref:System.Activities.Statements.If.Else%2A> se a condição for `false`.|  
|<xref:System.Activities.Statements.Parallel>|Executes continha atividades paralelamente.|  
|<xref:System.Activities.Statements.ParallelForEach%601>|Executa uma declaração inserido paralelamente para cada elemento em uma coleção.|  
|<xref:System.Activities.Statements.Pick>|Fornece etapas de eventos com base modelagem de fluxo de controle.|  
|<xref:System.Activities.Statements.PickBranch>|Representa um caminho potencial de execução em uma atividade de <xref:System.Activities.Statements.Pick> .|  
|<xref:System.Activities.Statements.Sequence>|Executes continha atividades em ordem.|  
|<xref:System.Activities.Statements.Switch%601>|Seleciona uma opção de um número de atividades para executar, com base no valor de uma expressão fornecida.|  
|<xref:System.Activities.Statements.While>|Executes continha atividades enquanto uma condição for `true`.|
