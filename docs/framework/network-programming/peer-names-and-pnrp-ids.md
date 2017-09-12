---
title: Nomes de par e IDs de PNRP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
caps.latest.revision: 5
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 11d20e346bba9ae6300f88c5d5bf48f99ec27904
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="peer-names-and-pnrp-ids"></a><span data-ttu-id="57d86-102">Nomes de par e IDs de PNRP</span><span class="sxs-lookup"><span data-stu-id="57d86-102">Peer Names and PNRP IDs</span></span>
<span data-ttu-id="57d86-103">Um nome de par representa um ponto de extremidade para comunicação, que pode ser um computador, um usuário, um grupo, um serviço ou qualquer elemento associado a um par que pode ser resolvido para um endereço IPv6.</span><span class="sxs-lookup"><span data-stu-id="57d86-103">A Peer Name represents an endpoint for communication, which can be a computer, a user, a group, a service, or anything associated with a Peer that can be resolved to an IPv6 address.</span></span> <span data-ttu-id="57d86-104">O protocolo PNRP usa o nome do par estatisticamente exclusivo para a criação de uma ID de PNRP, que é usado para identificar membros de nuvem.</span><span class="sxs-lookup"><span data-stu-id="57d86-104">The Peer Name Resolution Protocol (PNRP) takes the statistically unique Peer Name for the creation of a PNRP ID, which is used to identify cloud members.</span></span>  
  
## <a name="peer-names"></a><span data-ttu-id="57d86-105">Nomes de par</span><span class="sxs-lookup"><span data-stu-id="57d86-105">Peer Names</span></span>  
 <span data-ttu-id="57d86-106">Nomes de par podem ser registrados como seguros ou não seguros.</span><span class="sxs-lookup"><span data-stu-id="57d86-106">Peer names can be registered as unsecured or secured.</span></span> <span data-ttu-id="57d86-107">Nomes não seguros são apenas cadeias de caracteres de texto que estão sujeitas a falsificação, já que qualquer pessoa pode registrar um nome duplicado não seguro.</span><span class="sxs-lookup"><span data-stu-id="57d86-107">Unsecured names are just text strings that are subject to spoofing, as anyone can register a duplicate unsecured name.</span></span> <span data-ttu-id="57d86-108">Nomes não seguros encontram sua melhor aplicação em redes privadas ou protegidas.</span><span class="sxs-lookup"><span data-stu-id="57d86-108">Unsecured names are best used in private or otherwise protected networks.</span></span> <span data-ttu-id="57d86-109">Nomes seguros são protegidos com um certificado e uma assinatura digital.</span><span class="sxs-lookup"><span data-stu-id="57d86-109">Secured names are protected with a certificate and a digital signature.</span></span> <span data-ttu-id="57d86-110">Somente o editor original poderá comprovar a propriedade de um nome seguro.</span><span class="sxs-lookup"><span data-stu-id="57d86-110">Only the original publisher will be able to prove ownership of a secured name.</span></span>  
  
 <span data-ttu-id="57d86-111">A combinação de nuvem e o escopo fornece um ambiente razoavelmente seguro para pares que participam da atividade PNRP.</span><span class="sxs-lookup"><span data-stu-id="57d86-111">The combination of cloud and scope provides a reasonably secure environment for peers that participate in PNRP activity.</span></span> <span data-ttu-id="57d86-112">No entanto, usar um nome de par seguro não garante a segurança geral do aplicativo de rede.</span><span class="sxs-lookup"><span data-stu-id="57d86-112">However, using a secured peer name does not ensure the overall security of the networking application.</span></span> <span data-ttu-id="57d86-113">A segurança do aplicativo depende de implementação.</span><span class="sxs-lookup"><span data-stu-id="57d86-113">Security of the application is implementation-dependent.</span></span>  
  
 <span data-ttu-id="57d86-114">Nomes de par seguros só são registrados pelo seu proprietário e são protegidos com criptografia de chave pública.</span><span class="sxs-lookup"><span data-stu-id="57d86-114">Secured peer names are only registered by their owner and are protected with public key cryptography.</span></span> <span data-ttu-id="57d86-115">Um nome de par seguro é considerado pertencente à entidade de par com a chave privada correspondente.</span><span class="sxs-lookup"><span data-stu-id="57d86-115">A secured peer name is considered owned by the peer entity having the corresponding private key.</span></span> <span data-ttu-id="57d86-116">A propriedade pode ser comprovada através do endereço de par certificado (CPA), que é assinado usando a chave privada.</span><span class="sxs-lookup"><span data-stu-id="57d86-116">Ownership can be proved via the certified peer address (CPA), which is signed using the private key.</span></span> <span data-ttu-id="57d86-117">Um usuário mal-intencionado não pode forjar uma propriedade de um nome de par sem a chave privada correspondente.</span><span class="sxs-lookup"><span data-stu-id="57d86-117">A malicious user cannot forge ownership of a peer name without the corresponding private key.</span></span>  
  
## <a name="pnrp-ids"></a><span data-ttu-id="57d86-118">IDs de PNRP</span><span class="sxs-lookup"><span data-stu-id="57d86-118">PNRP IDs</span></span>  
 <span data-ttu-id="57d86-119">![ID de PNRP](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")</span><span class="sxs-lookup"><span data-stu-id="57d86-119">![PNRP ID](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")</span></span>  
  
 <span data-ttu-id="57d86-120">IDs de PNRP são compostas do seguinte:</span><span class="sxs-lookup"><span data-stu-id="57d86-120">PNRP IDs are composed of the following:</span></span>  
  
-   <span data-ttu-id="57d86-121">Os 128 bits superiores, conhecidos como a ID P2P (ponto a ponto), são um hash de um nome de par atribuído ao ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="57d86-121">The high-order 128 bits, known as the peer-to-peer (P2P) ID, are a hash of a peer name assigned to the endpoint.</span></span> <span data-ttu-id="57d86-122">O nome de par tem o seguinte formato: *Autoridade.Classificador*.</span><span class="sxs-lookup"><span data-stu-id="57d86-122">The peer name has the following format: *Authority.Classifier*.</span></span> <span data-ttu-id="57d86-123">Para nomes seguros, *Autoridade* é o hash SHA1 (Secure Hash Algorithm 1) da chave pública do nome de par em caracteres hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="57d86-123">For secured names, *Authority* is the Secure Hash Algorithm 1 (SHA1) hash of the public key of the peer name in hexadecimal characters.</span></span> <span data-ttu-id="57d86-124">Para nomes não seguros, a *Autoridade* é o caractere único "0".</span><span class="sxs-lookup"><span data-stu-id="57d86-124">For unsecured names, the *Authority* is the single character "0".</span></span> <span data-ttu-id="57d86-125">*Classificador* é uma cadeia de caracteres que identifica o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="57d86-125">*Classifier* is a string that identifies the application.</span></span> <span data-ttu-id="57d86-126">Nenhuma classificação de nome de par pode ser maior que 149 caracteres, incluindo o terminador `null`.</span><span class="sxs-lookup"><span data-stu-id="57d86-126">No peer name classifier can be greater than 149 characters long, including the `null` terminator.</span></span>  
  
-   <span data-ttu-id="57d86-127">Os 128 bits inferiores são usados para o Local do Serviço, que é um número gerado que identifica diferentes instâncias da mesma ID P2P na mesma nuvem.</span><span class="sxs-lookup"><span data-stu-id="57d86-127">The low-order 128 bits are used for the Service Location, which is a generated number that identifies different instances of the same P2P ID in the same cloud.</span></span>  
  
 <span data-ttu-id="57d86-128">Essa combinação de ID P2P e Local de Serviço permite que várias IDs de PNRP sejam registradas em um único computador.</span><span class="sxs-lookup"><span data-stu-id="57d86-128">This combination of P2P ID and Service Location allows multiple PNRP IDs to be registered from a single computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57d86-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57d86-129">See Also</span></span>  
 <xref:System.Net.PeerToPeer.PeerName>   
 <xref:System.Net.PeerToPeer>
