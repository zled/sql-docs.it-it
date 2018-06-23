---
title: Stabilire una connessione a un'origine dati | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [SQL Server Native Client]
- connections [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, data source connections
- CoCreateInstance method
- OLE DB data sources [SQL Server Native Client]
ms.assetid: 7ebd1394-cc8d-4bcf-92f3-c374a26e7ba0
caps.latest.revision: 43
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8354f8927cefd860ce2f212242cc7caea7976d27
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066061"
---
# <a name="establishing-a-connection-to-a-data-source"></a>Avvio di una connessione a un'origine dati
  Per l'accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client, il consumer deve prima creare un'istanza di un oggetto origine dati chiamando il **CoCreateInstance** metodo. Un identificatore univoco di classe (CLSID) identifica ogni provider OLE DB. Per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client, l'identificatore di classe è CLSID_SQLNCLI10. È inoltre possibile utilizzare il simbolo SQLNCLI_CLSID risolverà il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client che viene utilizzato nel SQLNCLI. h che si fa riferimento.  
  
 L'origine dati oggetto espone il **IDBProperties** interfaccia, il consumer utilizza per fornire informazioni di autenticazione di base, ad esempio nome del server, nome del database, ID utente e password. Il **IDBProperties:: SetProperties** metodo viene chiamato per impostare queste proprietà.  
  
 Se nel computer sono in esecuzione più istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il nome del server viene specificato come NomeServer\NomeIstanza.  
  
 L'oggetto origine dati espone anche il **IDBInitialize** interfaccia. Dopo aver configurate le proprietà, viene stabilita connessione all'origine dati chiamando il **IDBInitialize:: Initialize** metodo. Esempio:  
  
```  
CoCreateInstance(CLSID_SQLNCLI10,   
                 NULL,   
                 CLSCTX_INPROC_SERVER,  
                 IID_IDBInitialize,   
                 (void **) &pIDBInitialize)  
```  
  
 Questa chiamata a **CoCreateInstance** crea un singolo oggetto della classe associato a CLSID_SQLNCLI10 (CSLID associato a dati e al codice che verrà utilizzato per creare l'oggetto). IID_IDBInitialize è un riferimento all'identificatore dell'interfaccia (**IDBInitialize**) da utilizzare per comunicare con l'oggetto.  
  
 Di seguito è riportata una funzione di esempio che inizializza e stabilisce una connessione all'origine dati.  
  
```  
void InitializeAndEstablishConnection() {  
   // Initialize the COM library.  
   CoInitialize(NULL);  
  
   // Obtain access to the SQL Server Native Client OLE DB provider.  
   hr = CoCreateInstance(CLSID_SQLNCLI10,   
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
 [Creazione di un'applicazione del provider OLE DB di SQL Server Native Client](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  