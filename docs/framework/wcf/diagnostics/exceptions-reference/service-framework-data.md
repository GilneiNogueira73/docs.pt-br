---
title: Dados de estrutura de serviço
ms.date: 03/30/2017
ms.assetid: 2a2c8ddc-4e82-4e7f-a79f-97085c469517
ms.openlocfilehash: 5c65e9d473b5fe3f2b1c29824dcc1151abb0c3f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474010"
---
# <a name="service-framework-data"></a>Dados de estrutura de serviço
Este tópico lista todas as exceções geradas pelo serviço de estrutura de dados.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|AddressingExtensionInBadNS|O elemento especificado no namespace especificado não é válido. Isso significa que o elemento especificado é um elemento duplicado ou que não é uma extensão legal porque os elementos de extensão não podem estar em namespaces de endereçamento.|  
|BinaryEncoderSessionInvalid|A sessão de codificador binário não é válida porque houve um erro ao decodificar uma mensagem anterior.|  
|CannotDetectAddressingVersion|Não é possível detectar a versão do WS-Addressing. EndpointAddress não começar com um elemento.|  
|CouldNotFindNamespaceForPrefix|O prefixo especificado não tem nenhuma associação de namespace no escopo.|  
|EncoderBadContentType|Não é possível processar contentType.|  
|EncoderEnvelopeVersionMismatch|A versão de envelope da mensagem de entrada especificada não coincide com o codificador especificado. Verifique se que a associação está configurada com a mesma versão das mensagens esperadas.|  
|EncoderMessageVersionMismatch|A versão de mensagem da mensagem de saída especificada não coincide com o codificador especificado. Verifique se que a associação está configurada com a mesma versão da mensagem.|  
|ExtraContentIsPresentInFaultDetail|Conteúdo XML adicional está presente no elemento de detalhes da falha. É permitido somente um elemento.|  
|FilterBadTableType|A interface IMessageFilterTable criada para um filtro não pode ser MessageFilterTable ou derivado de MessageFilterTable.|  
|FilterTableInvalidForLookup|O estado de MessageFilterTable está corrompido. A pesquisa solicitada não pode ser executada.|  
|MandatoryHeaderNotUnderstood|Um ou mais necessários não foram entendidos blocos de cabeçalho de protocolo de acesso de objeto simples.|  
|MessageBodyIsStream|O corpo da mensagem é um fluxo.|  
|MessageBodyIsUnknown|O formato do corpo da mensagem é desconhecido.|  
|MessageBodyReaderInvalidReadState|O ReadState especificado do leitor de corpo de mensagem não pode ser consumido.|  
|MessageTextEncodingNotSupported|Não há suporte para a codificação do texto especificado que é usado no formato de mensagem de texto.|  
|MissingMessageID|Solicitação de que mensagem está faltando um cabeçalho MessageID. Um cabeçalho MessageID é necessário para correlacionar uma resposta.|  
|MultipleMessageHeaders|Mais de um cabeçalho com o nome especificado e o namespace foi encontrado.|  
|MultipleMessageHeadersWithActor|Foi encontrado mais de um cabeçalho com o nome especificado, o namespace e a função.|  
|MultipleRelatesToHeaders|Foi encontrado mais de um cabeçalho RelatesTo com a relação especificada. Somente um é permitido para cada relação.|  
|QueryFunctionTypeNotSupported|Não há suporte para o IXsltContextFunction tipo de retorno especificado.|  
|QueryIteratorOutOfScope|XPathNodeIterator foi invalidado. XPathNodeIterators transmitidos como argumentos a IXsltContextFunctions apenas são válidos na função. Não pode ser armazenado em cache para uso posterior ou retornados pela função.|  
|QueryVariableNull|Métodos de IXsltContextVariable não podem retornar nulos.|  
|QueryVariableTypeNotSupported|O IXsltContextVariable especificado, não há suporte para tipo derivado.|  
|ReceiveShutdownReturnedMessage|O canal recebeu uma mensagem de entrada inesperada com ação especificada durante o fechamento. Feche o canal quando não estiver esperando mais mensagens de entrada.|  
|XmlBufferInInvalidState|Ocorreu um erro interno. A operação não pode ser executada devido ao estado do buffer de XML.|  
|XmlBufferQuotaExceeded|O tamanho necessário para armazenar em buffer o conteúdo XML ultrapassou a cota de buffer.|
