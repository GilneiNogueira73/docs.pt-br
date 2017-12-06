---
title: Interface ISymUnmanagedWriter4
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f7ab7f06ba280675ca8349500e766364d30f9349
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="a4eca-102">Interface ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="a4eca-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="a4eca-103">Interface ISymUnmanagedWriter4.</span><span class="sxs-lookup"><span data-stu-id="a4eca-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4eca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4eca-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="a4eca-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a4eca-105">Methods</span></span>  
 <span data-ttu-id="a4eca-106">Essa interface contém os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="a4eca-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="a4eca-107">Método</span><span class="sxs-lookup"><span data-stu-id="a4eca-107">Method</span></span>|<span data-ttu-id="a4eca-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4eca-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a4eca-109">Método GetDebugInfoWithPadding</span><span class="sxs-lookup"><span data-stu-id="a4eca-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="a4eca-110">Funciona da mesma forma [método GetDebugInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) exceto que a cadeia de caracteres de caminho é preenchida com zeros após o caractere null de terminação para tornar os dados de cadeia de caracteres de tamanho fixo de `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="a4eca-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="a4eca-111">O preenchimento é fornecido apenas se o comprimento da cadeia de caracteres de caminho em si é menor que `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="a4eca-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="a4eca-112">Isso torna mais fácil escrever ferramentas que arquivos de diferença PE.</span><span class="sxs-lookup"><span data-stu-id="a4eca-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a4eca-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a4eca-113">Requirements</span></span>  
 <span data-ttu-id="a4eca-114">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a4eca-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4eca-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4eca-115">See Also</span></span>  
 [<span data-ttu-id="a4eca-116">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="a4eca-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="a4eca-117">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="a4eca-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)