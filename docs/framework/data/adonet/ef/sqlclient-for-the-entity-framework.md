---
title: SqlClient para Entity Framework
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: 430e0e143519f97802c8cef4eee658b482a81880
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252584"
---
# <a name="sqlclient-for-the-entity-framework"></a>SqlClient para Entity Framework
Esta seção descreve o provedor de dados. NET Framework para SQL Server (SqlClient), que permite Entity Framework para trabalhar sobre o Microsoft SQL Server.  
  
## <a name="provider-schema-attribute"></a>Atributo do provedor  
 `Provider` é um atributo do elemento de `Schema` na linguagem de definição de esquema de armazenamento (SSDL).  
  
 Para usar SqlClient, atribua a cadeia de caracteres “System.Data.SqlClient” ao atributo de `Provider` do elemento de `Schema` .  
  
## <a name="providermanifesttoken-schema-attribute"></a>Atributo do esquema de ProviderManifestToken  
 `ProviderManifestToken` é necessário um atributo do elemento de `Schema` em SSDL. Este token é usado para carregar o manifesto do provedor para cenários off-line. Para obter mais informações sobre `ProviderManifestToken` atributo, consulte [elemento de esquema (SSDL)](https://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222).  
  
 SqlClient pode ser usado como um provedor de dados para diferentes versões do SQL Server. Essas versões têm recursos diferentes. Por exemplo, [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] não oferece suporte `varchar(max)` e os tipos de `nvarchar(max)` que foram introduzidos com [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].  
  
 SqlClient gerencia e aceita os seguintes tokens de manifesto de provedor para versões diferentes do SQL Server.  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|-|-|-|  
|2000|2005|2008|  
  
> [!NOTE]
>  Começando com o Visual Studio 2010, o [ferramentas de modelo de dados de entidade ADO.NET](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) não dão suporte a SQL Server 2000.  
  
## <a name="provider-namespace-name"></a>Nome do namespace do provedor  
 Todos os provedores devem especificar um namespace. Essa propriedade informa a Entity Framework que prefixo é usado pelo provedor para compilações específicas, como tipos e funções. O namespace para manifestos de provedor SqlClient é `SqlServer`. Para obter mais informações sobre namespaces, consulte [Namespaces](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).  
  
## <a name="types"></a>Tipos  
 O provedor SqlClient para Entity Framework fornece informações de mapeamento entre tipos de modelo conceitual e tipos SQL Server. Para obter mais informações, consulte [SqlClient para Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
## <a name="functions"></a>Funções  
 O provedor SqlClient para Entity Framework define a lista de funções suportadas pelo provedor. Para obter uma lista das funções com suporte, consulte [SqlClient para funções de Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [SqlClient para funções de Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [SqlClient para Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [Problemas conhecidos em SqlClient para Entity Framework](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Consulte também  
 [Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) (Linguagem SQL de entidade)  
 [Referência de Linguagem](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)  
 [Problemas conhecidos no provedor do SqlClient para Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
