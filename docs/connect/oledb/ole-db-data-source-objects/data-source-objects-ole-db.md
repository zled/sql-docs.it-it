---
title: (OLE DB) di oggetti origine dei dati | Microsoft Docs
description: Oggetti origine dati (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: 58007040bc4f96749172644b229dba4769929d66
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2018
ms.locfileid: "39106077"
---
# <a name="data-source-objects-ole-db"></a>Oggetti origine dati (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il driver OLE DB per SQL Server usa il termine origine dati per il set di interfacce OLE DB usate per stabilire un collegamento a un archivio dati, ad esempio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Creazione di un'istanza dell'oggetto origine dati del provider è la prima attività di un Driver OLE DB per il consumer di SQL Server.  
  
 Ogni provider OLE DB dichiara un identificatore di classe (CLSID) per se stesso. Il CLSID per il Driver OLE DB per SQL Server è CLSID_MSOLEDBSQL il GUID C/C++ (il simbolo MSOLEDBSQL_CLSID risolverà il corretto progid nel file msoledbsql.h cui viene fatto riferimento). Con il CLSID, il consumer usa la funzione OLE **CoCreateInstance** per produrre un'istanza dell'oggetto origine dati.  
  
 Driver OLE DB per SQL Server è un server in-process. Le istanze degli oggetti del driver OLE DB per SQL Server vengono create usando la macro CLSCTX_INPROC_SERVER per indicare il contesto di esecuzione.  
  
 L'oggetto origine dati del driver OLE DB per SQL Server espone le interfacce di inizializzazione OLE DB che consentono al consumer di connettersi ai database [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] esistenti.  
  
 Ogni connessione eseguita tramite il Driver OLE DB per SQL Server imposta automaticamente queste opzioni:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 In questo esempio viene usata la macro dell'identificatore di classe per creare un oggetto origine dati del driver OLE DB per SQL Server e ottenere un riferimento alla relativa interfaccia **IDBInitialize**.  
  
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
  
 In seguito alla creazione di un'istanza di un oggetto origine dati del driver OLE DB per SQL Server, l'applicazione consumer può proseguire inizializzando l'origine dati e creando le sessioni. Le sessioni OLE DB presentano le interfacce che consentono l'accesso ai dati e la relativa modifica.  
  
 Il driver OLE DB per SQL Server crea la prima connessione a un'istanza specificata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come parte di una corretta inizializzazione dell'origine dati. La connessione viene mantenuta a condizione che venga mantenuto un riferimento in una delle interfacce di inizializzazione dell'origine dati o fino a quando non viene chiamato il metodo **IDBInitialize::Uninitialize**.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Proprietà delle origini dati &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [Proprietà delle informazioni sulle origini dati](../../oledb/ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [Proprietà di inizializzazione e di autorizzazione](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [Sessioni](../../oledb/ole-db-data-source-objects/sessions.md)  
  
-   [Proprietà sessione - Driver OLE DB per SQL Server](../../oledb/ole-db-data-source-objects/session-properties-oledb-driver-for-sql-server.md)  
  
-   [Oggetti di origine dati persistenti](../../oledb/ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per programmazione con SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
