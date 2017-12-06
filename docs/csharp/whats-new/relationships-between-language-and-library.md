---
title: "A relação entre os recursos de linguagem e tipos de biblioteca | Microsoft Docs"
description: "Recursos de linguagem geralmente dependem de tipos de biblioteca para implementação. Entenda a relação."
keywords: "Design de linguagem c#, biblioteca padrão"
author: billwagner
ms.author: wiwagn
ms.date: 07/20/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 93fd26a72743fcf45df3904cb8d0c787d8a228a8
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2017
---
# <a name="relationships-between-language-features-and-library-types"></a><span data-ttu-id="2ec69-105">Relações entre os recursos de linguagem e tipos de biblioteca</span><span class="sxs-lookup"><span data-stu-id="2ec69-105">Relationships between language features and library types</span></span>

<span data-ttu-id="2ec69-106">A definição de linguagem c# requer uma biblioteca padrão para determinados tipos e membros determinados acessíveis desses tipos.</span><span class="sxs-lookup"><span data-stu-id="2ec69-106">The C# language definition requires a standard library to have certain types and certain accessible members on those types.</span></span> <span data-ttu-id="2ec69-107">O compilador gera o código que usa esses tipos necessários e os membros de muitos recursos de idioma diferente.</span><span class="sxs-lookup"><span data-stu-id="2ec69-107">The compiler generates code that uses these required types and members for many different language features.</span></span> <span data-ttu-id="2ec69-108">Quando necessário, há pacotes do NuGet que contêm os tipos necessários para as versões mais recentes do idioma ao escrever código para ambientes em que esses tipos ou membros não foram implantados ainda.</span><span class="sxs-lookup"><span data-stu-id="2ec69-108">When necessary, there are NuGet packages that contain types needed for newer versions of the language when writing code for environments where those types or members have not been deployed yet.</span></span>

<span data-ttu-id="2ec69-109">Essa dependência na funcionalidade de biblioteca padrão foi parte da linguagem c# desde sua primeira versão.</span><span class="sxs-lookup"><span data-stu-id="2ec69-109">This dependency on standard library functionality has been part of the C# language since its first version.</span></span> <span data-ttu-id="2ec69-110">Nessa versão, os exemplos incluídos:</span><span class="sxs-lookup"><span data-stu-id="2ec69-110">In that version, examples included:</span></span>

* <span data-ttu-id="2ec69-111"><xref:System.Exception>-usado para todas as exceções geradas pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="2ec69-111"><xref:System.Exception> - used for all compiler generated exceptions.</span></span>
* <span data-ttu-id="2ec69-112"><xref:System.String>-C# `string` tipo é um sinônimo para <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="2ec69-112"><xref:System.String> - the C# `string` type is a synonym for <xref:System.String>.</span></span>
* <span data-ttu-id="2ec69-113"><xref:System.Int32>-sinônimo de `int`.</span><span class="sxs-lookup"><span data-stu-id="2ec69-113"><xref:System.Int32> - synonym of `int`.</span></span>

<span data-ttu-id="2ec69-114">A primeira versão foi simple: o compilador e a biblioteca padrão fornecidos juntos e não havia somente uma versão de cada.</span><span class="sxs-lookup"><span data-stu-id="2ec69-114">That first version was simple: the compiler and the standard library shipped together, and there was only one version of each.</span></span>

<span data-ttu-id="2ec69-115">As versões subsequentes do c# ocasionalmente adicionou novos tipos ou membros para as dependências.</span><span class="sxs-lookup"><span data-stu-id="2ec69-115">Subsequent versions of C# have occasionally added new types or members to the dependencies.</span></span> <span data-ttu-id="2ec69-116">Os exemplos incluem: <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> e <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2ec69-116">Examples include: <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> and <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>.</span></span> <span data-ttu-id="2ec69-117">C# 7.0 continua isso adicionando uma dependência no <xref:System.ValueTuple> para implementar o [tuplas](../tuples.md) recurso de idioma.</span><span class="sxs-lookup"><span data-stu-id="2ec69-117">C# 7.0 continues this by adding a dependency on <xref:System.ValueTuple> to implement the [tuples](../tuples.md) language feature.</span></span>

<span data-ttu-id="2ec69-118">A equipe de design de linguagem funciona para minimizar a área de superfície dos tipos e membros necessários em uma biblioteca padrão compatível.</span><span class="sxs-lookup"><span data-stu-id="2ec69-118">The language design team works to minimize the surface area of the types and members required in a compliant standard library.</span></span> <span data-ttu-id="2ec69-119">Essa meta é equilibrada em relação a um design limpo onde novos recursos de biblioteca são incorporados diretamente para o idioma.</span><span class="sxs-lookup"><span data-stu-id="2ec69-119">That goal is balanced against a clean design where new library features are incorporated seamlessly into the language.</span></span> <span data-ttu-id="2ec69-120">Haverá novos recursos em versões futuras do c# que exigem novos tipos e membros em uma biblioteca padrão.</span><span class="sxs-lookup"><span data-stu-id="2ec69-120">There will be new features in future versions of C# that require new types and members in a standard library.</span></span> <span data-ttu-id="2ec69-121">É importante entender como gerenciar essas dependências em seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="2ec69-121">It's important to understand how to manage those dependencies in your work.</span></span>

## <a name="managing-your-dependencies"></a><span data-ttu-id="2ec69-122">Gerenciando suas dependências</span><span class="sxs-lookup"><span data-stu-id="2ec69-122">Managing your dependencies</span></span>

<span data-ttu-id="2ec69-123">Ferramentas do compilador c# agora são desacopladas o ciclo de versão das bibliotecas do .NET em plataformas com suporte.</span><span class="sxs-lookup"><span data-stu-id="2ec69-123">C# compiler tools are now decoupled from the release cycle of the .NET libraries on supported platforms.</span></span> <span data-ttu-id="2ec69-124">Na verdade, bibliotecas .NET diferentes têm ciclos de lançamento diferentes: o .NET Framework no Windows é relesed como uma atualização do Windows, .NET Core é fornecido em uma agenda separada e as versões do Xamarin do envio de atualizações de biblioteca com as ferramentas Xamarin para cada plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="2ec69-124">In fact, different .NET libraries have different release cycles: the .NET Framework on Windows is relesed as a Windows Update, .NET Core ships on a separate schedule, and the Xamarin versions of library updates ship with the Xamarin tools for each target platform.</span></span>

<span data-ttu-id="2ec69-125">A maior parte do tempo, você não perceberá essas alterações.</span><span class="sxs-lookup"><span data-stu-id="2ec69-125">The majority of time, you won't notice these changes.</span></span> <span data-ttu-id="2ec69-126">No entanto, quando você estiver trabalhando com uma versão mais recente do idioma que requer recursos não ainda nas bibliotecas do .NET nessa plataforma, você será referenciar os pacotes do NuGet para fornecer esses novos tipos.</span><span class="sxs-lookup"><span data-stu-id="2ec69-126">However, when you are working with a newer version of the language that requires features not yet in the .NET libraries on that platform, you'll reference the NuGet packages to provide those new types.</span></span>
<span data-ttu-id="2ec69-127">Como as plataformas de seu aplicativo suporta é atualizadas com as novas instalações do framework, você pode remover a referência extra.</span><span class="sxs-lookup"><span data-stu-id="2ec69-127">As the platforms your app supports are updated with new framework installations, you can remove the extra reference.</span></span>

<span data-ttu-id="2ec69-128">Essa separação significa que você pode usar os novos recursos de linguagem até mesmo quando você direcionar máquinas que podem não ter o framework correspondente.</span><span class="sxs-lookup"><span data-stu-id="2ec69-128">This separation means you can use new language features even when you are targeting machines that may not have the corresponding framework.</span></span>