---
title: Supporto delle transazioni locali | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- SQL Server Native Client OLE DB provider, transactions
- local transactions [OLE DB]
ms.assetid: 78f2e5fc-b6fb-4eda-9f71-991a4d6c4902
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4b277f287580431c42f601e0257be0ab141ecefe
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="supporting-local-transactions"></a>Supporto delle transazioni locali
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Una sessione delimita l'ambito della transazione per un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transazione locale di provider OLE DB Native Client. Quando la direzione di un consumer, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client invia una richiesta a un'istanza connessa di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la richiesta costituisce un'unità di lavoro per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client. Le transazioni locali eseguono sempre il wrapping uno o più unità di lavoro in un unico [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sessione del provider OLE DB Native Client.  
  
 Utilizzando il valore predefinito [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] modalità autocommit del provider OLE DB Native Client, una singola unità di lavoro viene considerata come l'ambito di una transazione locale. Solo un unità partecipa alla transazione locale. Quando viene creata una sessione, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client inizia una transazione per la sessione. Al completamento di un'unità, viene eseguito il commit del lavoro. In caso di errore, viene eseguito il rollback di eventuali lavori iniziati e viene segnalato l'errore al consumer. In entrambi i casi il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client inizia una nuova transazione locale per la sessione in modo che tutto il lavoro viene eseguito all'interno di una transazione.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumer del provider OLE DB Native Client può indirizzare un controllo più preciso sull'ambito di transazione locale utilizzando il **ITransactionLocal** interfaccia. Quando una sessione del consumer inizia una transazione, tutte le unità di lavoro di sessione tra la transazione avviare punto e l'eventuale **Commit** o **Abort** chiamate al metodo vengono considerate come un'unità atomica. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client inizia implicitamente una transazione quando diretto a tale scopo dal consumer. Se il consumer non richiede la memorizzazione, la sessione ripristina il comportamento a livello di transazione padre, più comunemente la modalità AutoCommit.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta **ITransactionLocal:: StartTransaction** parametri come indicato di seguito.  
  
|Parametro|Description|  
|---------------|-----------------|  
|*isoLevel*[in]|Il livello di isolamento da utilizzare con questa transazione. Nelle transazioni locali il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta i seguenti:<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> Nota: A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], ISOLATIONLEVEL_SNAPSHOT è valido per il *isoLevel* argomento o meno il controllo delle versioni è abilitata per il database. Se tuttavia l'utente tenta di eseguire un'istruzione e il controllo delle versioni non è abilitato e/o il database non è di sola lettura, si verifica un errore. Inoltre, si verificherà l'errore XACT_E_ISOLATIONLEVEL se ISOLATIONLEVEL_SNAPSHOT è specificato come il *isoLevel* quando si è connessi a una versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anteriore [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|*isoFlag*[in]|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce un errore per qualsiasi valore diverso da zero.|  
|*pOtherOptions*[in]|Se non è NULL, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client richiede l'oggetto opzioni dall'interfaccia. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce XACT_E_NOTIMEOUT se l'oggetto di opzioni *ulTimeout* membro non è zero. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client ignora il valore della *szDescription* membro.|  
|*pulTransactionLevel*[out]|Se non è NULL, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce il livello nidificato della transazione.|  
  
 Per le transazioni locali il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementa provider OLE DB Native Client **ITransaction:: Abort** parametri come indicato di seguito.  
  
|Parametro|Description|  
|---------------|-----------------|  
|*pboidReason*[in]|Ignorato se impostato. Può essere NULL.|  
|*fRetaining*[in]|Quando è TRUE, una nuova transazione viene iniziata implicitamente per la sessione. È necessario che il consumer esegua il commit o termini la transazione. Se è FALSE, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client verrà ripristinata la modalità autocommit per la sessione.|  
|*fAsync*[in]|Interruzione asincrona non è supportata la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce XACT_E_NOTSUPPORTED se il valore è FALSE.|  
  
 Per le transazioni locali il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementa provider OLE DB Native Client **ITransaction:: commit** parametri come indicato di seguito.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*fRetaining*[in]|Quando è TRUE, una nuova transazione viene iniziata implicitamente per la sessione. È necessario che il consumer esegua il commit o termini la transazione. Se è FALSE, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client verrà ripristinata la modalità autocommit per la sessione.|  
|*grfTC*[in]|Asincrono e restituisce una fase non sono supportati dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce XACT_E_NOTSUPPORTED per qualsiasi valore diverso da XACTTC_SYNC.|  
|*grfRM*[in]|Deve essere 0.|  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set di righe OLE DB Native Client provider nella sessione vengono mantenuti in un locale commit o interrompere l'operazione in base ai valori delle proprietà set di righe DBPROP_ABORTPRESERVE e DBPROP_COMMITPRESERVE. Per impostazione predefinita, queste proprietà sono VARIANT_FALSE sia tutti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set di righe OLE DB Native Client provider nella sessione vengono persi in seguito a un'operazione di interruzione o commit.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non implementa il **ITransactionObject** interfaccia. Un tentativo del consumer di recuperare un riferimento dell'interfaccia restituisce E_NOINTERFACE.  
  
 Questo esempio viene utilizzato **ITransactionLocal**.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Transazioni](../../relational-databases/native-client-ole-db-transactions/transactions.md)   
 [Utilizzo dell'isolamento dello Snapshot](../../relational-databases/native-client/features/working-with-snapshot-isolation.md)  
  
  
