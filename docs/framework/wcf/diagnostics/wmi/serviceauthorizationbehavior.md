---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: c916d0820a1eae333384deab7b0619abfbdc8167
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374294"
---
# <a name="serviceauthorizationbehavior"></a>ServiceAuthorizationBehavior
ServiceAuthorizationBehavior  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ServiceAuthorizationBehavior não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe ServiceAuthorizationBehavior tem as seguintes propriedades:  
  
### <a name="impersonatecallerforalloperations"></a>ImpersonateCallerForAllOperations  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor que controla se o serviço tentará representar usando as credenciais fornecidas pela mensagem de entrada.  
  
### <a name="principalpermissionmode"></a>PrincipalPermissionMode  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 A entidade de segurança usada para executar operações no servidor.  
  
### <a name="roleprovider"></a>RoleProvider  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O nome do provedor de função ASP.NET.  
  
### <a name="serviceauthorizationmanager"></a>ServiceAuthorizationManager  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O Gerenciador de autorização usado para autorização personalizada.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
