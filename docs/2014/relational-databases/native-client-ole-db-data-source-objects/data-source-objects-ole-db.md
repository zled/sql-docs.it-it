---
title: Oggetti (OLE DB) dell'origine dati | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], data source objects
- SQL Server Native Client, data source objects
- SQLNCLI, data source objects
- SQL Server Native Client OLE DB provider, data source objects
- OLE DB data source objects [SQL Server Native Client]
- data source objects [OLE DB]
- CLSID
ms.assetid: c1d4ed20-ad3b-4e33-a26b-38d7517237b7
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9f89825aaca32b542a6788fc9ef849975695f275
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156450"
---
# <a name="data-source-objects-ole-db"></a>Oggetti origine dati (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client utilizza il termine origine dati per il set di interfacce di OLE DB utilizzato per stabilire un collegamento a un archivio dati, ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Creazione di un'istanza dell'oggetto origine dati del provider è la prima attività di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumer Native Client.  
  
 Ogni provider OLE DB dichiara un identificatore di classe (CLSID) per se stesso. Il CLSID per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client è CLSID_SQLNCLI10 il GUID C/C++ (il simbolo SQLNCLI_CLSID risolverà corrette progid nel file che si fa riferimento a SQLNCLI. h). Con il CLSID, il consumer utilizza OLE **CoCreateInstance** funzione per produrre un'istanza dell'oggetto origine dati.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client è un server in-process. Le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gli oggetti di provider OLE DB Native Client vengono creati utilizzando la macro CLSCTX_INPROC_SERVER per indicare il contesto eseguibile.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oggetto origine dati del provider OLE DB Native Client espone le interfacce di inizializzazione OLE DB che consentono al consumer di connettersi a esistente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.  
  
 Ogni connessione eseguita tramite il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client imposta automaticamente queste opzioni:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 Questo esempio Usa la macro dell'identificatore di classe per creare una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oggetto origine di dati del provider OLE DB Native Client e ottenere un riferimento al relativo **IDBInitialize** interfaccia.  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL, CLSCTX_INPROC_SERVER,  
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
  
 Seguito alla creazione di un'istanza di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oggetto origine dati del provider OLE DB Native Client, l'applicazione consumer può proseguire inizializzando l'origine dati e creando sessioni. Le sessioni OLE DB presentano le interfacce che consentono l'accesso ai dati e la relativa modifica.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client crea la prima connessione a un'istanza specificata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come parte di un'inizializzazione dell'origine dati completato. Viene mantenuta la connessione, purché venga mantenuto un riferimento in alcuna interfaccia di inizializzazione di origine dati o finché il **IDBInitialize:: UnInitialize** metodo viene chiamato.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Proprietà dell'origine dati &#40;OLE DB&#41;](data-source-properties-ole-db.md)  
  
-   [Proprietà delle informazioni sulle origini dati](data-source-information-properties.md)  
  
-   [Proprietà di inizializzazione e di autorizzazione](initialization-and-authorization-properties.md)  
  
-   [Sessioni](sessions.md)  
  
-   [Proprietà della sessione](session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Oggetti di origine dati persistenti](persisted-data-source-objects.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  