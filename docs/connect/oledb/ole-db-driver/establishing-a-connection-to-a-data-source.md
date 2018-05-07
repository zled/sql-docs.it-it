---
title: Stabilire una connessione a un'origine dati | Documenti Microsoft
description: Stabilire una connessione a un'origine dati tramite il Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [OLE DB Driver for SQL Server]
- connections [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, data source connections
- CoCreateInstance method
- OLE DB data sources [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 41a5890e7c7e3638267fc85723911c7f6c861276
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="establishing-a-connection-to-a-data-source"></a>Avvio di una connessione a un'origine dati
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Per accedere il Driver OLE DB per SQL Server, il consumer deve prima creare un'istanza di un oggetto origine dati chiamando il **CoCreateInstance** metodo. Un identificatore univoco di classe (CLSID) identifica ogni provider OLE DB. Per il Driver OLE DB per SQL Server, l'identificatore di classe è CLSID_MSOLEDBSQL. È inoltre possibile utilizzare il simbolo MSOLEDBSQL_CLSID che verrà risolto per il Driver OLE DB per SQL Server che viene utilizzata per msoledbsql.h cui si fa riferimento.  
  
 L'origine dati oggetto espone il **IDBProperties** interfaccia, il consumer utilizza per fornire informazioni di autenticazione di base, ad esempio nome del server, nome del database, l'ID utente e password. Il **IDBProperties:: SetProperties** metodo viene chiamato per impostare queste proprietà.  
  
 Se nel computer sono in esecuzione più istanze di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il nome del server viene specificato come NomeServer\NomeIstanza.  
  
 L'oggetto origine dati espone anche il **IDBInitialize** interfaccia. Dopo aver impostate le proprietà, viene stabilita connessione all'origine dati chiamando il **IDBInitialize:: Initialize** metodo. Esempio:  
  
```  
CoCreateInstance(CLSID_MSOLEDBSQL,   
                 NULL,   
                 CLSCTX_INPROC_SERVER,  
                 IID_IDBInitialize,   
                 (void **) &pIDBInitialize)  
```  
  
 Questa chiamata a **CoCreateInstance** crea un singolo oggetto della classe associata CLSID_MSOLEDBSQL (CSLID associato a dati e al codice che verrà utilizzato per creare l'oggetto). IID_IDBInitialize è un riferimento all'identificatore dell'interfaccia (**IDBInitialize**) da utilizzare per comunicare con l'oggetto.  
  
 Di seguito è riportata una funzione di esempio che inizializza e stabilisce una connessione all'origine dati.  
  
```  
void InitializeAndEstablishConnection() {  
   // Initialize the COM library.  
   CoInitialize(NULL);  
  
   // Obtain access to the OLE DB Driver for SQL Server.  
   hr = CoCreateInstance(CLSID_MSOLEDBSQL,   
                         NULL,   
                         CLSCTX_INPROC_SERVER,  
                         IID_IDBInitialize,   
                         (void **) &pIDBInitialize);  
   // Initialize property values needed to establish connection.  
   for (i = 0 ; i < 4 ; i++)   
      VariantInit(&InitProperties[i].vValue);  
  
   // Server name.  
   // See DBPROP structure for more information on InitProperties  
   InitProperties[0].dwPropertyID  = DBPROP_INIT_DATASOURCE;  
   InitProperties[0].vValue.vt    = VT_BSTR;  
   InitProperties[0].vValue.bstrVal=   
                     SysAllocString(L"Server");  
   InitProperties[0].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[0].colid       = DB_NULLID;  
  
   // Database.  
   InitProperties[1].dwPropertyID  = DBPROP_INIT_CATALOG;  
   InitProperties[1].vValue.vt    = VT_BSTR;  
   InitProperties[1].vValue.bstrVal= SysAllocString(L"database");  
   InitProperties[1].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[1].colid       = DB_NULLID;  
  
   // Username (login).  
   InitProperties[2].dwPropertyID  = DBPROP_AUTH_INTEGRATED;  
   InitProperties[2].vValue.vt    = VT_BSTR;  
   InitProperties[2].vValue.bstrVal= SysAllocString(L"SSPI");  
   InitProperties[2].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[2].colid       = DB_NULLID;  
   InitProperties[3].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[3].colid       = DB_NULLID;  
  
   // Construct the DBPROPSET structure(rgInitPropSet). The   
   // DBPROPSET structure is used to pass an array of DBPROP   
   // structures (InitProperties) to the SetProperties method.  
   rgInitPropSet[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgInitPropSet[0].cProperties   = 4;  
   rgInitPropSet[0].rgProperties   = InitProperties;  
  
   // Set initialization properties.  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties,   
                           (void **)&pIDBProperties);  
   hr = pIDBProperties->SetProperties(1, rgInitPropSet);   
   pIDBProperties->Release();  
  
   // Now establish the connection to the data source.  
   pIDBInitialize->Initialize();  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un driver OLE DB per applicazione SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
