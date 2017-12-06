---
title: Interface IMetaDataTables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables
helpviewer_keywords: IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c89d615fbeeff4a60eb386d58c573ee7905f538d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="a20be-102">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="a20be-102">IMetaDataTables Interface</span></span>
<span data-ttu-id="a20be-103">Fornece métodos para o armazenamento e recuperação de informações de metadados nas tabelas.</span><span class="sxs-lookup"><span data-stu-id="a20be-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a20be-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a20be-104">Methods</span></span>  
  
|<span data-ttu-id="a20be-105">Método</span><span class="sxs-lookup"><span data-stu-id="a20be-105">Method</span></span>|<span data-ttu-id="a20be-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a20be-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a20be-107">Método GetBlob</span><span class="sxs-lookup"><span data-stu-id="a20be-107">GetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|<span data-ttu-id="a20be-108">Obtém um ponteiro para o objeto binário grande (BLOB) ao índice da coluna especificada.</span><span class="sxs-lookup"><span data-stu-id="a20be-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="a20be-109">Método GetBlobHeapSize</span><span class="sxs-lookup"><span data-stu-id="a20be-109">GetBlobHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="a20be-110">Obtém o tamanho, em bytes, do heap de BLOB.</span><span class="sxs-lookup"><span data-stu-id="a20be-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="a20be-111">Método GetCodedTokenInfo</span><span class="sxs-lookup"><span data-stu-id="a20be-111">GetCodedTokenInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="a20be-112">Obtém um ponteiro para uma matriz de tokens associada ao índice de linha especificado.</span><span class="sxs-lookup"><span data-stu-id="a20be-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="a20be-113">Método GetColumn</span><span class="sxs-lookup"><span data-stu-id="a20be-113">GetColumn Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|<span data-ttu-id="a20be-114">Obtém um ponteiro para os valores contidos na coluna no índice de coluna especificada na tabela do índice da tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="a20be-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="a20be-115">Método GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="a20be-115">GetColumnInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="a20be-116">Obtém dados sobre a coluna especificada na tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="a20be-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="a20be-117">Método GetGuid</span><span class="sxs-lookup"><span data-stu-id="a20be-117">GetGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|<span data-ttu-id="a20be-118">Obtém um GUID da linha no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="a20be-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="a20be-119">Método GetGuidHeapSize</span><span class="sxs-lookup"><span data-stu-id="a20be-119">GetGuidHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="a20be-120">Obtém o tamanho, em bytes, do heap GUID.</span><span class="sxs-lookup"><span data-stu-id="a20be-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="a20be-121">Método GetNextBlob</span><span class="sxs-lookup"><span data-stu-id="a20be-121">GetNextBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|<span data-ttu-id="a20be-122">Obtém o índice do próximo BLOB na tabela.</span><span class="sxs-lookup"><span data-stu-id="a20be-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="a20be-123">Método GetNextGuid</span><span class="sxs-lookup"><span data-stu-id="a20be-123">GetNextGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|<span data-ttu-id="a20be-124">Obtém o índice do próximo valor GUID na coluna da tabela atual.</span><span class="sxs-lookup"><span data-stu-id="a20be-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="a20be-125">Método GetNextString</span><span class="sxs-lookup"><span data-stu-id="a20be-125">GetNextString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|<span data-ttu-id="a20be-126">Obtém o índice da seguinte cadeia de caracteres na coluna da tabela atual.</span><span class="sxs-lookup"><span data-stu-id="a20be-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="a20be-127">Método GetNextUserString</span><span class="sxs-lookup"><span data-stu-id="a20be-127">GetNextUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="a20be-128">Obtém o índice da linha que contém a cadeia de caracteres codificada Avançar na coluna da tabela atual.</span><span class="sxs-lookup"><span data-stu-id="a20be-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="a20be-129">Método GetNumTables</span><span class="sxs-lookup"><span data-stu-id="a20be-129">GetNumTables Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|<span data-ttu-id="a20be-130">Obtém o número de tabelas no escopo atual `IMetaDataTables` instância.</span><span class="sxs-lookup"><span data-stu-id="a20be-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="a20be-131">Método GetRow</span><span class="sxs-lookup"><span data-stu-id="a20be-131">GetRow Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|<span data-ttu-id="a20be-132">Obtém a linha no índice de linha especificada na tabela do índice da tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="a20be-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="a20be-133">Método GetString</span><span class="sxs-lookup"><span data-stu-id="a20be-133">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|<span data-ttu-id="a20be-134">Obtém a cadeia de caracteres no índice especificado da coluna de tabela no escopo de referência atual.</span><span class="sxs-lookup"><span data-stu-id="a20be-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="a20be-135">Método GetStringHeapSize</span><span class="sxs-lookup"><span data-stu-id="a20be-135">GetStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="a20be-136">Obtém o tamanho, em bytes, do heap de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a20be-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="a20be-137">Método GetTableIndex</span><span class="sxs-lookup"><span data-stu-id="a20be-137">GetTableIndex Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|<span data-ttu-id="a20be-138">Obtém o índice para a tabela referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="a20be-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="a20be-139">Método GetTableInfo</span><span class="sxs-lookup"><span data-stu-id="a20be-139">GetTableInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|<span data-ttu-id="a20be-140">Obtém o nome, o tamanho de linha, o número de linhas, o número de colunas e o índice da coluna de chave da tabela do índice da tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="a20be-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="a20be-141">Método GetUserString</span><span class="sxs-lookup"><span data-stu-id="a20be-141">GetUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|<span data-ttu-id="a20be-142">Obtém a cadeia de caracteres codificada no índice especificado na coluna de cadeia de caracteres no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="a20be-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="a20be-143">Método GetUserStringHeapSize</span><span class="sxs-lookup"><span data-stu-id="a20be-143">GetUserStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="a20be-144">Obtém o tamanho, em bytes, do heap de cadeia de caracteres do usuário.</span><span class="sxs-lookup"><span data-stu-id="a20be-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a20be-145">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a20be-145">Requirements</span></span>  
 <span data-ttu-id="a20be-146">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a20be-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a20be-147">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a20be-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a20be-148">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a20be-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a20be-149">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a20be-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a20be-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a20be-150">See Also</span></span>  
 [<span data-ttu-id="a20be-151">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="a20be-151">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="a20be-152">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="a20be-152">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)