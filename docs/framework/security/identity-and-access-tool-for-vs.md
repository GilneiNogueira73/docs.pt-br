---
title: Ferramenta de Identidade e Acesso para o Visual Studio 2012
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
caps.latest.revision: 3
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a009f37e1f16646df10e693a10827990b073c65c
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a><span data-ttu-id="bc93a-102">Ferramenta de Identidade e Acesso para o Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="bc93a-102">Identity and Access Tool for Visual Studio 2012</span></span>
<span data-ttu-id="bc93a-103">Este tópico descreve a nova Ferramenta de Identidade e Acesso para o Visual Studio 11.</span><span class="sxs-lookup"><span data-stu-id="bc93a-103">This topic describes the new Identity and Access Tool for Visual Studio 11.</span></span> <span data-ttu-id="bc93a-104">Você pode baixar essa ferramenta da seguinte URL: [http://go.microsoft.com/fwlink/?LinkID=245849](http://go.microsoft.com/fwlink/?LinkID=245849) ou diretamente do Visual Studio 11 pesquisando por “identidade” diretamente no Gerenciador de Extensões.</span><span class="sxs-lookup"><span data-stu-id="bc93a-104">You can download this tool from the following URL: [http://go.microsoft.com/fwlink/?LinkID=245849](http://go.microsoft.com/fwlink/?LinkID=245849) or directly from within Visual Studio 11 by searching for "identity" directly in the Extensions Manager.</span></span>  
  
 <span data-ttu-id="bc93a-105">A Ferramenta de Identidade e Acesso para o Visual Studio 11 fornece uma experiência de tempo de desenvolvimento drasticamente simplificada com os seguintes destaques:</span><span class="sxs-lookup"><span data-stu-id="bc93a-105">The Identity and Access Tool for Visual Studio 11 delivers a dramatically simplified development-time experience with the following highlights:</span></span>  
  
-   <span data-ttu-id="bc93a-106">Usando a nova ferramenta, você pode desenvolver usando tipos de projeto de aplicativos Web e o IIS Express como alvo.</span><span class="sxs-lookup"><span data-stu-id="bc93a-106">Using the new tool, you can develop using web applications project types and target IIS express.</span></span>  
  
-   <span data-ttu-id="bc93a-107">Diferente da autenticação somente de proteção ampla, com a nova ferramenta, você pode especificar sua página de descoberta do realm/controlador inicial local (ou qualquer outro ponto de extremidade que trata a experiência de autenticação em seu aplicativo) e o WIF configurará todas as solicitações não autenticadas para irem para lá, em vez de redirecioná-las ao STS.</span><span class="sxs-lookup"><span data-stu-id="bc93a-107">Unlike with the blanket protection-only authentication, with the new tool, you can specify your local home realm discovery page/controller (or any other endpoint handling the authentication experience within your application) and WIF will configure all unauthenticated requests to go there, instead of redirecting them to the STS.</span></span>  
  
-   <span data-ttu-id="bc93a-108">A ferramenta inclui um STS (Serviço de Token de Segurança) de teste que é executado no computador local quando você inicia uma sessão de depuração.</span><span class="sxs-lookup"><span data-stu-id="bc93a-108">The tool includes a test Security Token Service (STS) which runs on your local machine when you launch a debug session.</span></span> <span data-ttu-id="bc93a-109">Consequentemente, você não precisa criar projetos STS personalizados e ajustá-los para obter as declarações necessárias para testar seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="bc93a-109">Therefore, you no longer need to create custom STS projects and tweak them in order to get the claims you need to test your applications.</span></span> <span data-ttu-id="bc93a-110">Os tipos e os valores das declarações são completamente personalizáveis.</span><span class="sxs-lookup"><span data-stu-id="bc93a-110">The claim types and values are fully customizable.</span></span>  
  
-   <span data-ttu-id="bc93a-111">Você pode modificar as configurações comuns diretamente na interface de usuário da ferramenta, sem precisar editar o web.config.</span><span class="sxs-lookup"><span data-stu-id="bc93a-111">You can modify common settings directly via the tool’s UI, without the need to edit web.config.</span></span>  
  
-   <span data-ttu-id="bc93a-112">Você pode estabelecer federação com o Serviços de Federação do Active Directory (AD FS) 2.0 (ou outros provedores de WS-Federation) em uma única tela.</span><span class="sxs-lookup"><span data-stu-id="bc93a-112">You can establish federation with Active Directory Federation Services (AD FS) 2.0 (or other WS-Federation providers) in a single screen.</span></span>  
  
-   <span data-ttu-id="bc93a-113">A ferramenta usa os recursos do Serviço de Controle de Acesso (ACS) do Microsoft Azure com uma lista simples de caixas de seleção para todos os provedores de identidade que você quer usar: Facebook, Google, Live ID, Yahoo!, qualquer provedor do OpenID e qualquer provedor de WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="bc93a-113">The tool leverages Windows Azure Access Control Service (ACS) capabilities with a simple list of checkboxes for all the identity providers that you want to use: Facebook, Google, Live ID, Yahoo!, any OpenID provider, and any WS-Federation provider.</span></span> <span data-ttu-id="bc93a-114">Selecione seus provedores de identidade, clique em OK e pressione F5. Seu aplicativo e o ACS serão configurados automaticamente e seu aplicativo de teste será baseado no ACS.</span><span class="sxs-lookup"><span data-stu-id="bc93a-114">Select your identity providers, click OK, then F5, and both your application and ACS will be automatically configured and your test application will be ACS-aware.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc93a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc93a-115">See Also</span></span>  
 [<span data-ttu-id="bc93a-116">Recursos do WIF</span><span class="sxs-lookup"><span data-stu-id="bc93a-116">WIF Features</span></span>](../../../docs/framework/security/wif-features.md)
