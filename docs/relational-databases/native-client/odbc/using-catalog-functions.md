---
title: Utilizzo di funzioni di catalogo | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|ODBC
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC, functions
- SQLLinkedCatalogs function
- SQL Server Native Client ODBC driver, catalog functions
- SQLLinkedServers function
- catalog functions [ODBC]
- functions [ODBC]
ms.assetid: 7773fb2e-06b5-4c4b-88e9-0ad9132ad273
caps.latest.revision: "36"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ec3ca1363dd571b04b67b987725ad6fa280dd3bd
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="using-catalog-functions"></a>Utilizzo delle funzioni di catalogo
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Tutti i database presentano una struttura che contiene i dati archiviati nel database. Una definizione di tale struttura, insieme ad altre informazioni quali le autorizzazioni, è archiviata in un catalogo (implementato come un set di tabelle di sistema), noto anche come dizionario dei dati.  
  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client consente a un'applicazione determinare la struttura del database tramite chiamate alle funzioni di catalogo ODBC. Le funzioni di catalogo restituiscono informazioni nei set di risultati e vengono implementate utilizzando stored procedure di catalogo per eseguire query sulle tabelle di sistema nel catalogo. Un'applicazione potrebbe ad esempio richiedere un set di risultati contenente informazioni su tutte le tabelle del sistema o tutte le colonne di una particolare tabella. Le funzioni di catalogo ODBC standard vengono utilizzate per ottenere informazioni di catalogo dal computer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] al quale è connessa l'applicazione.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporta query distribuite grazie alle quali è possibile accedere con un'unica query ai dati provenienti da più origini dati OLE DB eterogenee. Uno dei metodi di accesso a un'origine dati OLE DB remota consiste nel definire l'origine dati come server collegato. Questa operazione può essere eseguita tramite [sp_addlinkedserver](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md). Dopo che è stato definito il server collegato, è possibile fare riferimento agli a oggetti del server nelle istruzioni Transact-SQL utilizzando un nome costituito da quattro parti:  
  
 *linked_server_name*.  
  
 Il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supporta due funzioni specifiche del driver per il recupero delle informazioni di catalogo dai server collegati:  
  
-   **SQLLinkedServers**  
  
     Restituisce un elenco dei server collegati definiti nel server locale.  
  
-   **SQLLinkedCatalogs**  
  
     Restituisce un elenco dei cataloghi presenti in un server collegato.  
  
 Dopo aver creato un server collegato e un nome di catalogo, il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta il recupero di informazioni dal catalogo utilizzando un nome in due parti di *linked_server_name***.** *catalogo* per *CatalogName* in ODBC seguenti funzioni di catalogo:  
  
-   **SQLColumnPrivileges**  
  
-   **SQLColumns**  
  
-   **SQLPrimaryKeys**  
  
-   **SQLStatistics**  
  
-   **SQLTablePrivileges**  
  
-   **SQLTables**  
  
 Le due parti *linked_server_name***.** *catalogo* è supportata anche per *FKCatalogName* e *PKCatalogName* su [SQLForeignKeys](../../../relational-databases/native-client-odbc-api/sqlforeignkeys.md).  
  
 L'utilizzo di SQLLinkedServers e SQLLinkedCatalogs richiede i file seguenti:  
  
-   sqlncli.h  
  
     Include prototipi della funzione e definizioni costanti per le funzioni del catalogo del server collegato. sqlncli.h deve essere incluso nell'applicazione ODBC e deve trovarsi nel percorso di inclusione al momento della compilazione dell'applicazione.  
  
-   sqlncli11.lib  
  
     Deve trovarsi nel percorso della libreria del linker e deve essere specificato come un file da collegare. sqlncli11.lib è distribuito con il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
-   sqlncli11.dll  
  
     Deve essere presente in fase di esecuzione. sqlncli11.dll è distribuito con il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40; ODBC &#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLColumnPrivileges](../../../relational-databases/native-client-odbc-api/sqlcolumnprivileges.md)   
 [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)   
 [SQLPrimaryKeys](../../../relational-databases/native-client-odbc-api/sqlprimarykeys.md)   
 [SQLTablePrivileges](../../../relational-databases/native-client-odbc-api/sqltableprivileges.md)   
 [SQLTables](../../../relational-databases/native-client-odbc-api/sqltables.md)   
 [SQLStatistics](../../../relational-databases/native-client-odbc-api/sqlstatistics.md)  
  
  
