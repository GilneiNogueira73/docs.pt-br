---
title: Habilitando o acesso entre bancos de dados no SQL Server
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 720c4c8eecc20b971eb9ecf1abb85da1e72e3c54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="enabling-cross-database-access-in-sql-server"></a><span data-ttu-id="283e2-102">Habilitando o acesso entre bancos de dados no SQL Server</span><span class="sxs-lookup"><span data-stu-id="283e2-102">Enabling Cross-Database Access in SQL Server</span></span>
<span data-ttu-id="283e2-103">O encadeamento de propriedade entre bancos de dados ocorre quando um procedimento em um banco de dados depende dos objetos em outro banco de dados.</span><span class="sxs-lookup"><span data-stu-id="283e2-103">Cross-database ownership chaining occurs when a procedure in one database depends on objects in another database.</span></span> <span data-ttu-id="283e2-104">Uma cadeia de propriedade entre bancos de dados funciona como a cadeia de propriedade dentro de um único banco de dados, exceto que uma cadeia de propriedade exige que todos os proprietários de objetos sejam mapeados para a mesma conta de logon.</span><span class="sxs-lookup"><span data-stu-id="283e2-104">A cross-database ownership chain works in the same way as ownership chaining within a single database, except that an unbroken ownership chain requires that all the object owners are mapped to the same login account.</span></span> <span data-ttu-id="283e2-105">Se o objeto de origem no banco de dados de origem e os objetos de destino nos bancos de dados de destino forem de propriedade da mesma conta de logon, o SQL Server não verificará permissões nos objetos de destino.</span><span class="sxs-lookup"><span data-stu-id="283e2-105">If the source object in the source database and the target objects in the target databases are owned by the same login account, SQL Server does not check permissions on the target objects.</span></span>  
  
## <a name="off-by-default"></a><span data-ttu-id="283e2-106">Desativado por padrão</span><span class="sxs-lookup"><span data-stu-id="283e2-106">Off By Default</span></span>  
 <span data-ttu-id="283e2-107">A cadeia de propriedade nos bancos de dados é desativada por padrão.</span><span class="sxs-lookup"><span data-stu-id="283e2-107">Ownership chaining across databases is turned off by default.</span></span> <span data-ttu-id="283e2-108">A Microsoft recomenda que você desabilite a propriedade do banco de dados porque o encadeamento expõe você aos seguintes riscos de segurança:</span><span class="sxs-lookup"><span data-stu-id="283e2-108">Microsoft recommends that you disable cross-database ownership chaining because it exposes you to the following security risks:</span></span>  
  
-   <span data-ttu-id="283e2-109">Os proprietários de banco de dados e os membros de `db_ddladmin` ou das funções de banco de dados de `db_owners` podem criar os objetos pertencentes a outros usuários.</span><span class="sxs-lookup"><span data-stu-id="283e2-109">Database owners and members of the `db_ddladmin` or the `db_owners` database roles can create objects that are owned by other users.</span></span> <span data-ttu-id="283e2-110">Esses objetos podem potencialmente ser destinados a objetos em outros bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="283e2-110">These objects can potentially target objects in other databases.</span></span> <span data-ttu-id="283e2-111">Isso significa que, se você habilitar o encadeamento de propriedades entre banco de dados, deverá confiar completamente nesses usuários com dados em todos os bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="283e2-111">This means that if you enable cross-database ownership chaining, you must fully trust these users with data in all databases.</span></span>  
  
-   <span data-ttu-id="283e2-112">Os usuários com a permissão CREATE DATABASE podem criar novos bancos de dados e anexar bancos de dados existentes.</span><span class="sxs-lookup"><span data-stu-id="283e2-112">Users with CREATE DATABASE permission can create new databases and attach existing databases.</span></span> <span data-ttu-id="283e2-113">Se o encadeamento de propriedades entre banco de dados estiver habilitado, esses usuários poderão acessar objetos em outros bancos de dados que possam não ter privilégios nos bancos de dados recém-criados ou anexados.</span><span class="sxs-lookup"><span data-stu-id="283e2-113">If cross-database ownership chaining is enabled, these users can access objects in other databases that they might not have privileges in from the newly created or attached databases that they create.</span></span>  
  
## <a name="enabling-cross-database-ownership-chaining"></a><span data-ttu-id="283e2-114">Habilitando o encadeamento de propriedades entre banco de dados</span><span class="sxs-lookup"><span data-stu-id="283e2-114">Enabling Cross-database Ownership Chaining</span></span>  
 <span data-ttu-id="283e2-115">O encadeamento de propriedades entre banco de dados deve ser habilitado apenas em ambientes onde você possa confiar completamente em usuários altamente privilegiados.</span><span class="sxs-lookup"><span data-stu-id="283e2-115">Cross-database ownership chaining should only be enabled in environments where you can fully trust highly-privileged users.</span></span> <span data-ttu-id="283e2-116">Pode ser configurado durante a instalação para todos os bancos de dados, ou seletivamente para os bancos de dados específicos usando comandos [!INCLUDE[tsql](../../../../../includes/tsql-md.md)]`sp_configure` e `ALTER DATABASE`.</span><span class="sxs-lookup"><span data-stu-id="283e2-116">It can be configured during setup for all databases, or selectively for specific databases using the [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] commands `sp_configure` and `ALTER DATABASE`.</span></span>  
  
 <span data-ttu-id="283e2-117">Para configurar seletivamente o encadeamento de propriedades entre banco de dados, use `sp_configure` para desativá-lo para o servidor.</span><span class="sxs-lookup"><span data-stu-id="283e2-117">To selectively configure cross-database ownership chaining, use `sp_configure` to turn it off for the server.</span></span> <span data-ttu-id="283e2-118">Use o comando ALTER DATABASE com SET DB_CHAINING ON para configurar o encadeamento de propriedades entre banco de dados para somente os bancos de dados que exigirem isso.</span><span class="sxs-lookup"><span data-stu-id="283e2-118">Then use the ALTER DATABASE command with SET DB_CHAINING ON to configure cross-database ownership chaining for only the databases that require it.</span></span>  
  
 <span data-ttu-id="283e2-119">O exemplo a seguir ativa o encadeamento de propriedades entre banco de dados para todos os bancos de dados:</span><span class="sxs-lookup"><span data-stu-id="283e2-119">The following sample turns on cross-database ownership chaining for all databases:</span></span>  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 <span data-ttu-id="283e2-120">O exemplo a seguir ativa o encadeamento de propriedades entre banco de dados para bancos de dados específicos:</span><span class="sxs-lookup"><span data-stu-id="283e2-120">The following sample turns on cross-database ownership chaining for specific databases:</span></span>  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a><span data-ttu-id="283e2-121">SQL dinâmico</span><span class="sxs-lookup"><span data-stu-id="283e2-121">Dynamic SQL</span></span>  
 <span data-ttu-id="283e2-122">O encadeamento de propriedades entre bancos de dados não funciona nos casos em que as instruções SQL criadas dinamicamente são executadas a menos que o mesmo usuário exista em ambos os bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="283e2-122">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed unless the same user exists in both databases.</span></span> <span data-ttu-id="283e2-123">Você pode solucionar isso no [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] criando um procedimento armazenado que acessa dados em outro banco de dados e assinando o procedimento armazenado com um certificado existente em ambos os bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="283e2-123">You can work around this in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="283e2-124">Isso concede acesso de usuários aos recursos de banco de dados usados pelo procedimento sem conceder-lhes o acesso ao banco de dados ou permissões.</span><span class="sxs-lookup"><span data-stu-id="283e2-124">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="283e2-125">Recursos externos</span><span class="sxs-lookup"><span data-stu-id="283e2-125">External Resources</span></span>  
 <span data-ttu-id="283e2-126">Para obter mais informações, consulte os seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="283e2-126">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="283e2-127">Recurso</span><span class="sxs-lookup"><span data-stu-id="283e2-127">Resource</span></span>|<span data-ttu-id="283e2-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="283e2-128">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="283e2-129">[Estendendo a representação de banco de dados usando EXECUTE AS](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) e [opção Cross DB Ownership Chaining](http://msdn.microsoft.com/library/ms188694.aspx) [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Manuais Online.</span><span class="sxs-lookup"><span data-stu-id="283e2-129">[Extending Database Impersonation by Using EXECUTE AS](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) and [Cross DB Ownership Chaining Option](http://msdn.microsoft.com/library/ms188694.aspx)[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>|<span data-ttu-id="283e2-130">Os tópicos a seguir descrevem como configurar o encadeamento de propriedade entre banco de dados para uma instância do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="283e2-130">Topics describe how to configure cross-database ownership chaining for an instance of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="283e2-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="283e2-131">See Also</span></span>  
 <span data-ttu-id="283e2-132">[Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="283e2-132">[Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)</span></span>  
 [<span data-ttu-id="283e2-133">Visão geral de segurança do SQL Server</span><span class="sxs-lookup"><span data-stu-id="283e2-133">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="283e2-134">Gerenciando permissões com procedimentos armazenados no SQL Server</span><span class="sxs-lookup"><span data-stu-id="283e2-134">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="283e2-135">Gravando SQL dinâmico seguro no SQL Server</span><span class="sxs-lookup"><span data-stu-id="283e2-135">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="283e2-136">Assinando procedimentos armazenados no SQL Server</span><span class="sxs-lookup"><span data-stu-id="283e2-136">Signing Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 <span data-ttu-id="283e2-137">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="283e2-137">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>