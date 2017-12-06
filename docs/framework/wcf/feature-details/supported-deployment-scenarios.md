---
title: "Cenários de desempenho com suporte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5886b327f1ea6d2866b9fc76bb29031ee870934e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="supported-deployment-scenarios"></a><span data-ttu-id="81098-102">Cenários de desempenho com suporte</span><span class="sxs-lookup"><span data-stu-id="81098-102">Supported Deployment Scenarios</span></span>
<span data-ttu-id="81098-103">O subconjunto de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] recursos com suporte para uso em aplicativos parcialmente confiáveis é projetado para atender aos requisitos de algumas, mas nem todos os cenários de uso [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81098-103">The subset of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] features supported for use in partially trusted applications is designed to meet the requirements of some, but not all, scenarios for using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="81098-104">No servidor, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] atende os requisitos de escala da Internet compartilhada provedores de hospedagem que executam aplicativos de terceiros no [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] conjunto por motivos de segurança de permissões de confiança média.</span><span class="sxs-lookup"><span data-stu-id="81098-104">On the server, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] meets the requirements of Internet-scale shared hosting providers who run third-party applications in the [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] Medium Trust permission set for security reasons.</span></span> <span data-ttu-id="81098-105">No cliente, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] suporte de confiança parcial é projetado para atender aos requisitos de tecnologias de implantação, como [implantação de ClickOnce](http://go.microsoft.com/fwlink/?LinkId=83712) ou [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]da tecnologia de aplicativo de navegador XAML, que permitem contínua e implantação segura de aplicativos de área de trabalho de sites não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="81098-105">On the client, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] partial trust support is designed to meet the requirements of deployment technologies such as [ClickOnce Deployment](http://go.microsoft.com/fwlink/?LinkId=83712) or [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]'s XAML Browser Application technology, which allow seamless and secure deployment of desktop applications from untrusted sites.</span></span>  
  
## <a name="minimum-permission-requirements"></a><span data-ttu-id="81098-106">Requisitos de permissão mínima</span><span class="sxs-lookup"><span data-stu-id="81098-106">Minimum Permission Requirements</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="81098-107">dá suporte a um subconjunto de recursos em aplicativos em execução em qualquer um dos seguintes conjuntos de permissões nomeadas padrão:</span><span class="sxs-lookup"><span data-stu-id="81098-107"> supports a subset of features in applications running under either of the following standard named permission sets:</span></span>  
  
-   <span data-ttu-id="81098-108">Permissões de confiança médio</span><span class="sxs-lookup"><span data-stu-id="81098-108">Medium Trust permissions</span></span>  
  
-   <span data-ttu-id="81098-109">Permissões de zona da Internet</span><span class="sxs-lookup"><span data-stu-id="81098-109">Internet Zone permissions</span></span>  
  
 <span data-ttu-id="81098-110">Tentativa de usar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em aplicativos parcialmente confiáveis com permissões mais restritivas pode resultar em exceções de segurança em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="81098-110">Attempting to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in partially trusted applications with more restrictive permissions may result in security exceptions at runtime.</span></span>  
  
 <span data-ttu-id="81098-111">Para obter mais informações sobre os recursos com suporte nesses conjuntos de permissão, consulte [compatibilidade de recurso de relação de confiança parcial](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).</span><span class="sxs-lookup"><span data-stu-id="81098-111">For more information about the features supported in these permission sets, see [Partial Trust Feature Compatibility](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).</span></span>  
  
## <a name="partial-trust-on-the-server"></a><span data-ttu-id="81098-112">Confiança parcial no servidor</span><span class="sxs-lookup"><span data-stu-id="81098-112">Partial Trust on the Server</span></span>  
 <span data-ttu-id="81098-113">Muitos provedores comerciais de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] autorizar que executam aplicativos em execução em seus servidores em de serviços de hospedagem de aplicativos Web a [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] conjunto de permissões de confiança média.</span><span class="sxs-lookup"><span data-stu-id="81098-113">Many commercial providers of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application hosting services mandate that applications running on their servers run in the [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] Medium Trust permission set.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="81098-114">os serviços podem ser executados nesses ambientes desde que eles usam o <xref:System.ServiceModel.BasicHttpBinding>, o <xref:System.ServiceModel.WebHttpBinding>, ou <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> com segurança em nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="81098-114"> services can run in these environments provided they use the <xref:System.ServiceModel.BasicHttpBinding>, the <xref:System.ServiceModel.WebHttpBinding>, or the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with transport-level security.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="81098-115">serviços em execução em ambientes de hospedagem de confiança média também podem agir como serviços de camada intermediária, enviando mensagens para outros servidores em resposta a solicitações de cliente.</span><span class="sxs-lookup"><span data-stu-id="81098-115"> services running in Medium Trust hosting environments can also act as middle-tier services by sending messages to other servers in response to client requests.</span></span> <span data-ttu-id="81098-116">Cenários de camada intermediária do servidor têm suporte se o ambiente de hospedagem concedido o aplicativo apropriado <xref:System.Net.WebPermission> para fazer solicitações de saída para o servidor desejado.</span><span class="sxs-lookup"><span data-stu-id="81098-116">Middle-tier scenarios on the server are supported if the hosting environment has granted the application the appropriate <xref:System.Net.WebPermission> to make outbound requests to the desired server.</span></span>  
  
 <span data-ttu-id="81098-117">Além de usar uma das associações SOAP com suporte, as mensagens de SOAP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece suporte a <xref:System.ServiceModel.WebHttpBinding> para criar serviços de estilo da Web em aplicativos parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="81098-117">In addition to SOAP messaging using one of the supported SOAP bindings, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports the <xref:System.ServiceModel.WebHttpBinding> for building Web-style services in partially trusted applications.</span></span> <span data-ttu-id="81098-118">O [modelo de programação do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md), [Sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md), e [integração de AJAX e suporte a JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md) recursos de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] são todos com suporte em confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="81098-118">The [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md), [WCF Syndication](../../../../docs/framework/wcf/feature-details/wcf-syndication.md), and [AJAX Integration and JSON Support](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md) features of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are all supported in partial trust.</span></span>  
  
 <span data-ttu-id="81098-119">Serviços de fluxo de trabalho exigem permissões de confiança total e não podem ser usados em aplicativos parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="81098-119">Workflow Services require Full Trust permissions and cannot be used in partially trusted applications.</span></span>  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="81098-120">[Como: usar confiança média no ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=84603).</span><span class="sxs-lookup"><span data-stu-id="81098-120"> [How to: Use Medium Trust in ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=84603).</span></span>  
  
## <a name="partial-trust-on-the-client"></a><span data-ttu-id="81098-121">Confiança parcial no cliente</span><span class="sxs-lookup"><span data-stu-id="81098-121">Partial Trust on the Client</span></span>  
 <span data-ttu-id="81098-122">Certas precauções de segurança devem ter cuidadas ao baixar e executar código não confiáveis de sites da Internet.</span><span class="sxs-lookup"><span data-stu-id="81098-122">Certain security precautions must be taken when downloading and running code from untrusted Internet sites.</span></span> <span data-ttu-id="81098-123">Ambos [implantação de ClickOnce](http://go.microsoft.com/fwlink/?LinkId=83712) e [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]XAML navegador XBAP (aplicativos) tecnologia fazer uso de confiança parcial para conceder permissões limitadas (zona da Internet) para código não confiável.</span><span class="sxs-lookup"><span data-stu-id="81098-123">Both [ClickOnce Deployment](http://go.microsoft.com/fwlink/?LinkId=83712) and [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]'s XAML Browser Application (XBAP) technology make use of partial trust to grant limited permissions (Internet Zone) to untrusted code.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="81098-124">pode ser usado para se comunicar com servidores remotos a partir parcialmente confiáveis aplicativos implantados pelo [implantação de ClickOnce](http://go.microsoft.com/fwlink/?LinkId=83712) ou XBAP.</span><span class="sxs-lookup"><span data-stu-id="81098-124"> can be used to communicate with remote servers from within partially trusted applications deployed by either [ClickOnce Deployment](http://go.microsoft.com/fwlink/?LinkId=83712) or XBAP.</span></span> <span data-ttu-id="81098-125">Inclui o conjunto de permissões da zona da Internet <xref:System.Net.WebPermission> para o host de origem, que permite que esses aplicativos para se comunicar com o servidor de origem usando qualquer um com suporte [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vinculações descritos em [recurso de relação de confiança parcial Compatibilidade](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).</span><span class="sxs-lookup"><span data-stu-id="81098-125">The Internet Zone permission set includes <xref:System.Net.WebPermission> for the originating host, which allows these applications to communicate with their origin server using any of the supported [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bindings described in [Partial Trust Feature Compatibility](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81098-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81098-126">See Also</span></span>  
 [<span data-ttu-id="81098-127">Segurança de acesso do código</span><span class="sxs-lookup"><span data-stu-id="81098-127">Code Access Security</span></span>](http://go.microsoft.com/fwlink/?LinkId=83717)  
 [<span data-ttu-id="81098-128">Visão geral de aplicativos hospedados em navegador do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="81098-128">Windows Presentation Foundation Browser-Hosted Applications Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=98397)  
 [<span data-ttu-id="81098-129">Confiança parcial</span><span class="sxs-lookup"><span data-stu-id="81098-129">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 [<span data-ttu-id="81098-130">Confiança média do ASP.Net</span><span class="sxs-lookup"><span data-stu-id="81098-130">ASP.Net Medium Trust</span></span>](http://go.microsoft.com/fwlink/?LinkId=69328)