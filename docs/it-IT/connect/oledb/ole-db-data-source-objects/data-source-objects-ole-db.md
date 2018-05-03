---
title: Oggetti (OLE DB) dell'origine dati | Documenti Microsoft
description: Oggetti origine dati (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], data source objects
- OLE DB Driver for SQL Server, data source objects
- MSOLEDBSQL, data source objects
- OLE DB Driver for SQL Server, data source objects
- OLE DB data source objects [OLE DB Driver for SQL Server]
- data source objects [OLE DB]
- CLSID
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 05e9653ad107d31042ff75416e85754129709fff
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="data-source-objects-ole-db"></a>Oggetti origine dati (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il Driver OLE DB per SQL Server utilizza il termine origine dati per il set di interfacce di OLE DB utilizzato per stabilire un collegamento a un archivio dati, ad esempio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Creazione di un'istanza dell'oggetto origine dati del provider è la prima attività di un Driver OLE DB per il consumer di SQL Server.  
  
 Ogni provider OLE DB dichiara un identificatore di classe (CLSID) per se stesso. Il CLSID per il Driver OLE DB per SQL Server è CLSID_MSOLEDBSQL il GUID C/C++ (il simbolo MSOLEDBSQL_CLSID verrà risolta in corrette progid nel file msoledbsql.h cui si fa riferimento). Con il CLSID, il consumer utilizza OLE **CoCreateInstance** funzione per produrre un'istanza dell'oggetto di origine dati.  
  
 Il Driver OLE DB per SQL Server è un server in-process. Le istanze di Driver OLE DB per gli oggetti di SQL Server vengono create utilizzando la macro CLSCTX_INPROC_SERVER per indicare il contesto eseguibile.  
  
 Il Driver OLE DB per l'oggetto origine dati di SQL Server espone le interfacce di inizializzazione OLE DB che consentono al consumer di connettersi a esistente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.  
  
 Ogni connessione eseguita tramite il Driver OLE DB per SQL Server imposta automaticamente queste opzioni:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 Questo esempio Usa la macro dell'identificatore di classe per creare un Driver OLE DB per SQL Server oggetto di origine e ottenere un riferimento al relativo **IDBInitialize** interfaccia.  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_MSOLEDBSQL, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 Seguito alla creazione di un'istanza di un Driver OLE DB per l'oggetto origine dati di SQL Server, l'applicazione consumer può proseguire inizializzando l'origine dati e creando sessioni. Le sessioni OLE DB presentano le interfacce che consentono l'accesso ai dati e la relativa modifica.  
  
 Il Driver OLE DB per SQL Server crea la prima connessione a un'istanza specificata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come parte di un'inizializzazione dell'origine dati completato. La connessione viene mantenuta, purché venga mantenuto un riferimento in alcuna interfaccia di inizializzazione di origine dati o fino a quando il **IDBInitialize:: UnInitialize** metodo viene chiamato.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Proprietà dell'origine dati & #40; OLE DB & #41;](../../oledb/ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [Proprietà delle informazioni di origine dati](../../oledb/ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [Proprietà di inizializzazione e autorizzazione](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [Sessioni](../../oledb/ole-db-data-source-objects/sessions.md)  
  
-   [Proprietà sessione - Driver OLE DB per SQL Server](../../oledb/ole-db-data-source-objects/session-properties-oledb-driver-for-sql-server.md)  
  
-   [Oggetti origine dati persistenti](../../oledb/ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per programmazione con SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
