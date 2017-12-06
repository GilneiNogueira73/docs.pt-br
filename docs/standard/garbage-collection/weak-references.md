---
title: "Referências fracas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 906c23caa7065486bb094ad2475ed9e7e24b3d9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="weak-references"></a><span data-ttu-id="b59bb-102">Referências fracas</span><span class="sxs-lookup"><span data-stu-id="b59bb-102">Weak References</span></span>
<span data-ttu-id="b59bb-103">O coletor de lixo não pode coletar um objeto em uso por um aplicativo enquanto o código do aplicativo pode acessar esse objeto.</span><span class="sxs-lookup"><span data-stu-id="b59bb-103">The garbage collector cannot collect an object in use by an application while the application's code can reach that object.</span></span> <span data-ttu-id="b59bb-104">O aplicativo tem uma referência forte para o objeto.</span><span class="sxs-lookup"><span data-stu-id="b59bb-104">The application is said to have a strong reference to the object.</span></span>  
  
 <span data-ttu-id="b59bb-105">Uma referência fraca permite que o coletor de lixo colete o objeto enquanto ainda permite que o aplicativo o acesse.</span><span class="sxs-lookup"><span data-stu-id="b59bb-105">A weak reference permits the garbage collector to collect the object while still allowing the application to access the object.</span></span> <span data-ttu-id="b59bb-106">Uma referência fraca é válida somente durante o período indeterminado até que o objeto seja coletado quando não há nenhuma referência forte.</span><span class="sxs-lookup"><span data-stu-id="b59bb-106">A weak reference is valid only during the indeterminate amount of time until the object is collected when no strong references exist.</span></span> <span data-ttu-id="b59bb-107">Quando você usa uma referência fraca, o aplicativo ainda pode obter uma referência forte para o objeto, o que impede que ele seja coletado.</span><span class="sxs-lookup"><span data-stu-id="b59bb-107">When you use a weak reference, the application can still obtain a strong reference to the object, which prevents it from being collected.</span></span> <span data-ttu-id="b59bb-108">No entanto, sempre há o risco de o coletor de lixo obter o objeto primeiro antes de uma referência forte ser restabelecida.</span><span class="sxs-lookup"><span data-stu-id="b59bb-108">However, there is always the risk that the garbage collector will get to the object first before a strong reference is reestablished.</span></span>  
  
 <span data-ttu-id="b59bb-109">As referências fracas são úteis para objetos que usam muita memória, mas podem ser facilmente recriados se forem recuperados pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b59bb-109">Weak references are useful for objects that use a lot of memory, but can be recreated easily if they are reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="b59bb-110">Suponha que uma exibição de árvore em um aplicativo Windows Forms exibe uma opção complexa hierárquica das opções para o usuário.</span><span class="sxs-lookup"><span data-stu-id="b59bb-110">Suppose a tree view in a Windows Forms application displays a complex hierarchical choice of options to the user.</span></span> <span data-ttu-id="b59bb-111">Se os dados subjacentes forem grandes, manter a árvore na memória é ineficiente quando o usuário está envolvido com outra coisa no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b59bb-111">If the underlying data is large, keeping the tree in memory is inefficient when the user is involved with something else in the application.</span></span>  
  
 <span data-ttu-id="b59bb-112">Quando o usuário alterna imediatamente para outra parte do aplicativo, você pode usar o <xref:System.WeakReference> classe para criar uma referência fraca a árvore e destruir todas as referências de alta seguras.</span><span class="sxs-lookup"><span data-stu-id="b59bb-112">When the user switches away to another part of the application, you can use the <xref:System.WeakReference> class to create a weak reference to the tree and destroy all strong references.</span></span> <span data-ttu-id="b59bb-113">Quando o usuário alterna de volta para a árvore, o aplicativo tenta obter uma referência forte para a árvore e, se tiver êxito, evita a reconstrução da árvore.</span><span class="sxs-lookup"><span data-stu-id="b59bb-113">When the user switches back to the tree, the application attempts to obtain a strong reference to the tree and, if successful, avoids reconstructing the tree.</span></span>  
  
 <span data-ttu-id="b59bb-114">Para estabelecer uma referência fraca com um objeto, você cria um <xref:System.WeakReference> usando a instância do objeto a ser rastreada.</span><span class="sxs-lookup"><span data-stu-id="b59bb-114">To establish a weak reference with an object, you create a <xref:System.WeakReference> using the instance of the object to be tracked.</span></span> <span data-ttu-id="b59bb-115">Você definir o <xref:System.WeakReference.Target%2A> propriedade para esse objeto e o conjunto original de referência para o objeto a ser `null`.</span><span class="sxs-lookup"><span data-stu-id="b59bb-115">You then set the <xref:System.WeakReference.Target%2A> property to that object and set the original reference to the object to `null`.</span></span> <span data-ttu-id="b59bb-116">Para obter um exemplo de código, consulte <xref:System.WeakReference> na biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="b59bb-116">For a code example, see <xref:System.WeakReference> in the class library.</span></span>  
  
## <a name="short-and-long-weak-references"></a><span data-ttu-id="b59bb-117">Referências fracas curtas e longas</span><span class="sxs-lookup"><span data-stu-id="b59bb-117">Short and Long Weak References</span></span>  
 <span data-ttu-id="b59bb-118">Você pode criar uma referência fraca curta ou uma referência fraca longa:</span><span class="sxs-lookup"><span data-stu-id="b59bb-118">You can create a short weak reference or a long weak reference:</span></span>  
  
-   <span data-ttu-id="b59bb-119">Abreviado</span><span class="sxs-lookup"><span data-stu-id="b59bb-119">Short</span></span>  
  
     <span data-ttu-id="b59bb-120">O destino de uma referência fraca curta se torna `null` quando o objeto é recuperado pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b59bb-120">The target of a short weak reference becomes `null` when the object is reclaimed by garbage collection.</span></span> <span data-ttu-id="b59bb-121">A referência fraca é um objeto gerenciado e está sujeita à coleta de lixo assim como qualquer outro objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b59bb-121">The weak reference is itself a managed object, and is subject to garbage collection just like any other managed object.</span></span>  <span data-ttu-id="b59bb-122">Uma referência fraca curta é o construtor padrão para <xref:System.WeakReference>.</span><span class="sxs-lookup"><span data-stu-id="b59bb-122">A short weak reference is the default constructor for <xref:System.WeakReference>.</span></span>  
  
-   <span data-ttu-id="b59bb-123">Long</span><span class="sxs-lookup"><span data-stu-id="b59bb-123">Long</span></span>  
  
     <span data-ttu-id="b59bb-124">Uma referência fraca longa é mantida após o objeto <xref:System.Object.Finalize%2A> método foi chamado.</span><span class="sxs-lookup"><span data-stu-id="b59bb-124">A long weak reference is retained after the object's <xref:System.Object.Finalize%2A> method has been called.</span></span> <span data-ttu-id="b59bb-125">Isso permite que o objeto seja recriado, mas o estado do objeto permanece imprevisível.</span><span class="sxs-lookup"><span data-stu-id="b59bb-125">This allows the object to be recreated, but the state of the object remains unpredictable.</span></span> <span data-ttu-id="b59bb-126">Para usar uma referência de tempo, especifique `true` no <xref:System.WeakReference> construtor.</span><span class="sxs-lookup"><span data-stu-id="b59bb-126">To use a long reference, specify `true` in the <xref:System.WeakReference> constructor.</span></span>  
  
     <span data-ttu-id="b59bb-127">Se o tipo de objeto não tem um <xref:System.Object.Finalize%2A> aplica-se do método, a funcionalidade de referência fraca curto e a referência fraca é válida somente até que o destino é coletado, que podem ocorrer a qualquer momento após o finalizador é executado.</span><span class="sxs-lookup"><span data-stu-id="b59bb-127">If the object's type does not have a <xref:System.Object.Finalize%2A> method, the short weak reference functionality applies and the weak reference is valid only until the target is collected, which can occur anytime after the finalizer is run.</span></span>  
  
 <span data-ttu-id="b59bb-128">Para estabelecer uma referência forte e usar o objeto novamente, converter o <xref:System.WeakReference.Target%2A> propriedade de um <xref:System.WeakReference> para o tipo do objeto.</span><span class="sxs-lookup"><span data-stu-id="b59bb-128">To establish a strong reference and use the object again, cast the <xref:System.WeakReference.Target%2A> property of a <xref:System.WeakReference> to the type of the object.</span></span> <span data-ttu-id="b59bb-129">Se o <xref:System.WeakReference.Target%2A> propriedade retorna `null`, o objeto foi coletado; caso contrário, você pode continuar a usar o objeto porque o aplicativo foi recuperado uma referência forte para ele.</span><span class="sxs-lookup"><span data-stu-id="b59bb-129">If the <xref:System.WeakReference.Target%2A> property returns `null`, the object was collected; otherwise, you can continue to use the object because the application has regained a strong reference to it.</span></span>  
  
## <a name="guidelines-for-using-weak-references"></a><span data-ttu-id="b59bb-130">Diretrizes para usar referências fracas</span><span class="sxs-lookup"><span data-stu-id="b59bb-130">Guidelines for Using Weak References</span></span>  
 <span data-ttu-id="b59bb-131">Use referências fracas longas somente quando necessário, uma vez que o estado do objeto é imprevisível após a finalização.</span><span class="sxs-lookup"><span data-stu-id="b59bb-131">Use long weak references only when necessary as the state of the object is unpredictable after finalization.</span></span>  
  
 <span data-ttu-id="b59bb-132">Evite usar referências fracas para objetos pequenos, pois o ponteiro em si pode ser tão grande quanto ou maior.</span><span class="sxs-lookup"><span data-stu-id="b59bb-132">Avoid using weak references to small objects because the pointer itself may be as large or larger.</span></span>  
  
 <span data-ttu-id="b59bb-133">Evite usar referências fracas como uma solução automática para problemas de gerenciamento de memória.</span><span class="sxs-lookup"><span data-stu-id="b59bb-133">Avoid using weak references as an automatic solution to memory management problems.</span></span> <span data-ttu-id="b59bb-134">Em vez disso, desenvolva uma política de cache efetiva para lidar com os objetos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b59bb-134">Instead, develop an effective caching policy for handling your application's objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b59bb-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b59bb-135">See Also</span></span>  
 [<span data-ttu-id="b59bb-136">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="b59bb-136">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)