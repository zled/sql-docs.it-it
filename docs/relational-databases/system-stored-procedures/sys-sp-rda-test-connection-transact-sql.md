---
title: sys.sp_rda_test_connection (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_test_connection
- sys.sp_rda_test_connection_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_test_connection stored procedure
ms.assetid: e2ba050c-d7e3-4f33-8281-c9b525b4edb4
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1c44c6c3974b10b442d4b6a5944276f7f3c3693e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33003908"
---
# <a name="syssprdatestconnection-transact-sql"></a>sys.sp_rda_test_connection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Verifica la connessione da SQL Server per il server Azure remoto e segnala i problemi che potrebbero impedire la migrazione dei dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
EXECUTE sys.sp_rda_test_connection  
   @database_name = N'db_name',   
   @server_address = N'azure_server_fully_qualified_address',  
   @azure_username = N'azure_username',   
   @azure_password = N'azure_password',  
   @credential_name = N'credential_name'  
  
```  
  
## <a name="arguments"></a>Argomenti  
 @database_name = N'*db_name*'  
 Il nome del database di SQL Server abilitata per l'estensione. Questo parametro è facoltativo.  
  
 @server_address = N'*azure_server_fully_qualified_address*'  
 L'indirizzo completo del server Azure.  
  
-   Se si fornisce un valore per **@database_name**, ma il database specificato non è abilitata per l'estensione, quindi è necessario specificare un valore per **@server_address**.  
  
-   Se si fornisce un valore per **@database_name**, il database specificato è abilitata per l'estensione, quindi non è necessario fornire un valore per **@server_address**. Se si fornisce un valore per **@server_address**, la stored procedure viene ignorato e Usa il server Azure già associate con il database abilitati per l'estensione.  
  
 @azure_username = N'*azure_username*  
 Il nome utente per il server Azure remoto.  
  
 @azure_password = N'*azure_password*'  
 La password per il server Azure remoto.  
  
 @credential_name = N'*credential_name*'  
 Invece di fornire un nome utente e una password, è possibile fornire il nome di una credenziale archiviata nel database abilitati per l'estensione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 In caso di **successo**, sp_rda_test_connection restituisce l'errore 14855 (STRETCH_MAJOR, STRETCH_CONNECTION_TEST_PROC_SUCCEEDED) con livello di gravità EX_INFO e codice restituito esito positivo.  
  
 In caso di **errore**, sp_rda_test_connection restituisce l'errore 14856 (STRETCH_MAJOR, STRETCH_CONNECTION_TEST_PROC_FAILED) con livello di gravità EX_USER e codice di errore restituito.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|link_state|int|Uno dei valori seguenti, che corrispondono ai valori per **link_state_desc**.<br /><br /> -   0<br />-   1<br />-   2<br />-   3<br />-   4|  
|link_state_desc|varchar (32)|Uno dei valori seguenti, che corrisponde al precedente valori per **link_state**.<br /><br /> -INTEGRO<br />     Il tra SQL Server e di Azure remoto server è integro.<br />-ERROR_AZURE_FIREWALL<br />     Il firewall di Azure impedisce il collegamento tra SQL Server e il server Azure remoto.<br />-ERROR_NO_CONNECTION<br />     SQL Server non è possibile stabilire una connessione al server Azure remoto.<br />-ERROR_AUTH_FAILURE<br />     Errore di autenticazione impedisce il collegamento tra SQL Server e il server Azure remoto.<br />-ERRORE<br />     Un errore che non è un problema di autenticazione, un problema di connettività o un problema di firewall impedisce il collegamento tra SQL Server e il server Azure remoto.|  
|error_number|int|Il numero dell'errore. Se non si verificano errori, questo campo è NULL.|  
|error_message|nvarchar(1024)|Messaggio di errore. Se non si verificano errori, questo campo è NULL.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede autorizzazioni db_owner.  
  
## <a name="examples"></a>Esempi  
  
### <a name="check-the-connection-from-sql-server-to-the-remote-azure-server"></a>Verificare la connessione da SQL Server e il server Azure remoto  
  
```sql  
EXECUTE sys.sp_rda_test_connection @database_name = N'<Stretch-enabled database>'  
GO  
  
```  
  
 I risultati mostrano che SQL Server non è possibile connettersi al server Azure remoto.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|2|ERROR_NO_CONNECTION|*\<numero di errore relativi alla connessione >*|*\<messaggio di errore relativi alla connessione >*|  
  
### <a name="check-the-azure-firewall"></a>Controllare il firewall di Azure  
  
```sql  
USE <Stretch-enabled database>  
GO  
EXECUTE sys.sp_rda_test_connection  
GO  
  
```  
  
 I risultati mostrano che il firewall di Azure impedisce il collegamento tra SQL Server e il server Azure remoto.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|1|ERROR_AZURE_FIREWALL|*\<numero di errore correlato al firewall >*|*\<messaggio di errore correlato al firewall >*|  
  
### <a name="check-authentication-credentials"></a>Verificare le credenziali di autenticazione.  
  
```sql  
USE <Stretch-enabled database>  
GO  
EXECUTE sys.sp_rda_test_connection  
GO  
  
```  
  
 I risultati mostrano un errore di autenticazione che impedisce il collegamento tra SQL Server e il server Azure remoto.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|3|ERROR_AUTH_FAILURE|*\<numero di errore relativi all'autenticazione >*|*\<messaggio di errore relativi all'autenticazione >*|  
  
### <a name="check-the-status-of-the-remote-azure-server"></a>Controllare lo stato del server Azure remoto  
  
```sql  
USE <SQL Server database>  
GO  
EXECUTE sys.sp_rda_test_connection   
    @server_address = N'<server name>.database.windows.net',   
    @azure_username = N'<user name>',   
    @azure_password = N'<password>'  
GO  
  
```  
  
 I risultati mostrano che la connessione sia integro e che è possibile abilitare estensione Database per il database specificato.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|0|HEALTHY|NULL|NULL|  
  
  
