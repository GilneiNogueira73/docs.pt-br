---
title: Método ICorDebugProcess::WriteMemory
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6da4c282c7f969a406a657d1e30dd6120a32b4e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420902"
---
# <a name="icordebugprocesswritememory-method"></a>Método ICorDebugProcess::WriteMemory
Grava dados em uma área da memória do processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `address`  
 [in] Um `CORDB_ADDRESS` valor que é o endereço base da área de memória no qual os dados é gravado. Antes que ocorra a transferência de dados, o sistema verifica se a área da memória do tamanho especificado, começando no endereço base, está acessível para gravação. Se não estiver acessível, o método falhará.  
  
 `size`  
 [in] O número de bytes a serem gravados para a área de memória.  
  
 `buffer`  
 [in] Um buffer que contém os dados a serem gravados.  
  
 `written`  
 [out] Um ponteiro para uma variável que recebe o número de bytes gravados para a área de memória nesse processo. Se `written` for NULL, esse parâmetro é ignorado.  
  
## <a name="remarks"></a>Comentários  
 Automaticamente, os dados são gravados por trás de qualquer ponto de interrupção. O .NET Framework versão 2.0, depuradores nativo não devem usar esse método para inserir pontos de interrupção no fluxo de instrução. Use [Icordebugprocess2](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) em vez disso.  
  
 O `WriteMemory` método deve ser usado somente fora do código gerenciado. Esse método pode corromper o tempo de execução se usada incorretamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
