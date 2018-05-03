---
title: Tramite il Driver OLE DB per SQL Server intestazione e i file di libreria | Documenti Microsoft
description: Usa il Driver OLE DB per i file di intestazione e di libreria di SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- header files [OLE DB Driver for SQL Server]
- MSOLEDBSQL, header files
- OLE DB, header files
- library files [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, header files
- data access [OLE DB Driver for SQL Server], header files
- data access [OLE DB Driver for SQL Server], library files
- OLE DB Driver for SQL Server, library files
- MSOLEDBSQL, library files
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 8ed2d5385806ee439cc67111c83cc08ea786e160
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-the-ole-db-driver-for-sql-server-header-and-library-files"></a>Tramite il Driver OLE DB per SQL Server intestazione e i file di libreria
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il Driver OLE DB per SQL Server intestazione e i file di libreria vengono installati quando il Driver OLE DB per l'opzione di SQL Server SDK viene selezionato durante il processo di installazione. Quando si sviluppa un'applicazione, è importante copiare e installare nell'ambiente di sviluppo tutti i file necessari per lo sviluppo. Per ulteriori informazioni sull'installazione e la ridistribuzione del Driver OLE DB per SQL Server, vedere [installazione di Driver OLE DB per SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md).  
  
 Il Driver OLE DB per SQL Server intestazione e i file di libreria vengono installati nel percorso seguente:  
  
 *% PROGRAMMI %* \Microsoft SQL Server\Client SDK\OLEDB\180\SDK  
  
 Il Driver OLE DB per il file di intestazione di SQL Server (msoledbsql.h) utilizzabile per aggiungere Driver OLE DB per la funzionalità di accesso ai dati di SQL Server alle applicazioni personalizzate. Il Driver OLE DB per il file di intestazione di SQL Server contiene tutte le definizioni, attributi, proprietà e le interfacce necessarie per sfruttare i vantaggi delle nuove funzionalità introdotte in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Oltre al Driver OLE DB per il file di intestazione di SQL Server, è inoltre disponibile un file di libreria msoledbsql.lib che rappresenta la libreria di esportazione per [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) funzionalità.  
  
 Il Driver OLE DB per il file di intestazione di SQL Server è compatibile con il file di intestazione SQLOLEDB. h utilizzato con Microsoft Data Access Components (MDAC), ma non contiene i CLSID per SQLOLEDB (il provider OLE DB per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] incluso con MDAC) o simboli per Funzionalità XML (che non è supportata dal Driver OLE DB per SQL Server).    
  
 Le applicazioni OLE DB che utilizzano il Driver OLE DB per SQL Server è necessario solo fare riferimento a msoledbsql.h. Se un'applicazione utilizza sia MDAC (SQLOLEDB) e il Driver OLE DB per SQL Server, è possibile fare riferimento a SQLOLEDB. h sia msoledbsql.h, ma deve precedere il riferimento a SQLOLEDB. h.  
  
## <a name="using-the-ole-db-driver-for-sql-server-header-file"></a>Tramite il Driver OLE DB per il File di intestazione SQL Server  
 Per utilizzare il Driver OLE DB per il file di intestazione di SQL Server, è necessario utilizzare un **includono** istruzione all'interno del codice di programmazione C/C++. Le sezioni seguenti descrivono come eseguire questa applicazione OLE DB.  
  
> [!NOTE]  
>  Il Driver OLE DB per i file di intestazione e di libreria di SQL Server può solo essere compilata usando Visual Studio C++ 2012 o versione successiva.  
  
### <a name="ole-db"></a>OLE DB  
 Per utilizzare il Driver OLE DB per file di intestazione di SQL Server in un'applicazione OLE DB, utilizzando le righe di codice di programmazione seguenti:  
  
```    
include "msoledbsql.h";  
```  
  
> [!NOTE]  
>  Se l'applicazione ha un **includono** istruzione per SQLOLEDB. h, il **includono** informativa per msoledbsql.h deve provenire dopo di esso.  
  
 Quando si crea una connessione a un'origine dati tramite il Driver OLE DB per SQL Server, utilizzare "MSOLEDBSQL" come stringa del nome del provider.  

  
## <a name="component-names-and-properties-by-version"></a>Proprietà e nomi dei componenti per versione  

|Proprietà|Driver OLE DB per SQL Server|MDAC|  
|--------|----------------------------|----|   
|OLE DB PROGID|MSOLEDBSQL|SQLOLEDB|  
|Nome file di intestazione OLE DB|msoledbsql.h|Sqloledb.h|  
|DLL del provider OLE DB|msoledbsql.dll|Sqloledb.dll| 
  
  
## <a name="static-linking-and-bcp-functions"></a>Collegamento statico e funzioni BCP  
 Quando in un'applicazione vengono utilizzate funzioni BCP, è importante specificare nella stringa di connessione il driver della stessa versione fornita con il file di intestazione e la libreria utilizzati per compilare l'applicazione.  
  
 Per ulteriori informazioni, vedere esecuzione [eseguendo le operazioni di copia Bulk](../../oledb/features/performing-bulk-copy-operations.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con il driver OLE DB per SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
