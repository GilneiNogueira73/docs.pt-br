---
title: Método ICLRStrongName::StrongNameGetPublicKey
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c8d97653a195ec0fc287455079f37b311c3d42e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508778"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>Método ICLRStrongName::StrongNameGetPublicKey
Obtém a chave pública de um par de chaves pública/privada. O par de chaves pode ser fornecido como um nome de contêiner de chave dentro de um provedor de serviços de criptografia (CSP) ou como uma coleção bruta de bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szKeyContainer`  
 [in] O nome do contêiner de chave que contém o par de chaves pública/privada. Se `pbKeyBlob` for nulo, `szKeyContainer` deve especificar um contêiner válido dentro do CSP. Nesse caso, o [iclrstrongname:: Strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) método extrai a chave pública do par de chaves armazenado no contêiner.  
  
 Se `pbKeyBlob` não for nulo, presume-se o par de chaves para caber no objeto binário grande (BLOB) chave.  
  
 As chaves devem ser Rivest-Shamir-Adleman (RSA de 1024 bits) chaves de assinatura. Não há outros tipos de chaves têm suporte no momento.  
  
 `pbKeyBlob`  
 [in] Um ponteiro para o par de chaves pública/privada. Esse par está no formato criado pelo Win32 `CryptExportKey` função. Se `pbKeyBlob` for nula, o contêiner de chave especificado por `szKeyContainer` deve para conter o par de chaves.  
  
 `cbKeyBlob`  
 [in] O tamanho, em bytes, do `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 [out] A chave pública retornada BLOB. O `ppbPublicKeyBlob` parâmetro é alocado pelo common language runtime e retornado ao chamador. O chamador deve liberar a memória usando o [iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método.  
  
 `pcbPublicKeyBlob`  
 [out] O tamanho da chave pública retornado BLOB.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).  
  
## <a name="remarks"></a>Comentários  
 A chave pública está contida em uma [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) estrutura.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [Estrutura PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
