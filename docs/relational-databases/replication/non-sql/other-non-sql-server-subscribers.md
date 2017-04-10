---
title: "Altri Sottoscrittori non SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sottoscrittori non SQL Server, altri tipi"
ms.assetid: 96b8beb9-38e8-4ce4-97ca-c0f8656b73b4
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# Altri Sottoscrittori non SQL Server
  Per un elenco di non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sottoscrittori supportati da [!INCLUDE[msCoName](../../../includes/msconame-md.md)], vedere [sottoscrittori Non SQL Server](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md). In questo argomento vengono fornite informazioni sui requisiti per i driver ODBC e i provider OLE DB.  
  
## Requisiti per i driver ODBC  
 Il driver ODBC deve soddisfare i requisiti seguenti:  
  
-   Deve essere conforme a ODBC di livello 1.  
  
-   Deve essere un ambiente di distribuzione thread-safe.  
  
-   Deve essere in grado di eseguire transazioni.  
  
-   Deve supportare il linguaggio DDL (Data Definition Language).  
  
-   Non può essere di sola lettura.  
  
-   Deve supportare nomi di tabella lunghi, ad esempio **MSreplication_subscriptions**.  
  
## Esecuzione della replica tramite interfacce OLE DB  
 Per la replica transazionale i provider OLE DB devono supportare gli oggetti seguenti:  
  
-   **Origine dati** oggetto  
  
-   **Sessione** oggetto  
  
-   **Comando** oggetto  
  
-   **Set di righe** oggetto  
  
-   **Errore** oggetto  
  
### Interfacce per oggetti DataSource  
 Per la connessione a un'origine dei dati sono necessarie le interfacce seguenti:  
  
-   **IDBInitialize**  
  
-   **IDBCreateSession**  
  
-   **IDBProperties**  
  
 Se il provider supporta il **IDBInfo** interfaccia [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizza l'interfaccia per recuperare informazioni quali l'identificatore tra virgolette, lunghezza massima delle istruzioni SQL e il numero massimo di caratteri nei nomi di tabella e colonna.  
  
### Interfacce per oggetti Session  
 Sono necessarie le interfacce seguenti:  
  
-   **IDBCreateCommand**  
  
-   **ITransaction**  
  
-   **ITransactionLocal**  
  
-   **IDBSchemaRowset**  
  
### Interfacce per oggetti Command  
 Sono necessarie le interfacce seguenti:  
  
-   **ICommand**  
  
-   **ICommandProperties**  
  
-   **ICommandText**  
  
-   **ICommandPrepare**  
  
-   **IColumnsInfo**  
  
-   **IAccessor**  
  
-   **ICommandWithParameters**  
  
 **IAccessor** è necessario creare le funzioni di accesso di parametro. Se il provider supporta **IColumnRowset**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tale interfaccia viene utilizzata per determinare se una colonna è una colonna identity.  
  
### Interfacce per oggetti Rowset  
 Sono necessarie le interfacce seguenti:  
  
-   **IRowset**  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
 In un'applicazione può essere necessario aprire un set di righe di una tabella replicata creata nel database di sottoscrizione. **IColumnsInfo** e **IAccessor** sono necessarie per accedere ai dati nel set di righe.  
  
### Interfacce per oggetti Error  
 Per la gestione degli errori, utilizzare le interfacce seguenti:  
  
-   **IErrorRecords**  
  
-   **IErrorInfo**  
  
 Utilizzare **ISQLErrorInfo** se è supportato dal provider OLE DB.  
  
 Per ulteriori informazioni sul provider OLE DB, vedere la relativa documentazione.  
  
## Vedere anche  
 [Sottoscrittori non SQL Server](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)  
  
  