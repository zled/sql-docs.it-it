---
title: Supporto delle transazioni locali | Documenti Microsoft
description: Transazioni locali nel Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- OLE DB Driver for SQL Server, transactions
- local transactions [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: de00c4aac3125209bb56a1867f07b1f395804cc8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="supporting-local-transactions"></a>Supporto delle transazioni locali
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Una sessione delimita l'ambito della transazione per un Driver OLE DB per la transazione locale di SQL Server. Quando, su indicazione di un consumer, il Driver OLE DB per SQL Server invia una richiesta per un'istanza connessa di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], la richiesta costituisce un'unità di lavoro per il Driver OLE DB per SQL Server. Le transazioni locali eseguono sempre il wrapping uno o più unità di lavoro in un singolo Driver OLE DB per la sessione di SQL Server.  
  
 Utilizza il Driver OLE DB per impostazione predefinita per la modalità autocommit SQL Server, una singola unità di lavoro viene considerata come l'ambito di una transazione locale. Solo un unità partecipa alla transazione locale. Quando viene creata una sessione, il Driver OLE DB per SQL Server avvia una transazione per la sessione. Al completamento di un'unità, viene eseguito il commit del lavoro. In caso di errore, viene eseguito il rollback di eventuali lavori iniziati e viene segnalato l'errore al consumer. In entrambi i casi, il Driver OLE DB per SQL Server avvia una nuova transazione locale per la sessione in modo che tutto il lavoro viene eseguito all'interno di una transazione.  
  
 Il Driver OLE DB per il consumer di SQL Server può indirizzare controllo più preciso sull'ambito della transazione locale usando il **ITransactionLocal** interfaccia. Quando una sessione del consumer inizia una transazione, tutte le unità di lavoro di sessione tra la transazione avviare punto e l'eventuale **Commit** o **Abort** chiamate al metodo vengono considerate come un'unità atomica. Il Driver OLE DB per SQL Server avvia in modo implicito una transazione quando verrà indicato a tale scopo dal consumer. Se il consumer non richiede la memorizzazione, la sessione ripristina il comportamento a livello di transazione padre, più comunemente la modalità AutoCommit.  
  
 Il Driver OLE DB per SQL Server supporta **ITransactionLocal:: StartTransaction** parametri come indicato di seguito.  
  
|Parametro|Description|  
|---------------|-----------------|  
|*isoLevel*[in]|Il livello di isolamento da utilizzare con questa transazione. Nelle transazioni locali il Driver OLE DB per SQL Server supporta quanto segue:<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> Nota: A partire da [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], ISOLATIONLEVEL_SNAPSHOT è valido per il *isoLevel* argomento o meno il controllo delle versioni è abilitata per il database. Se tuttavia l'utente tenta di eseguire un'istruzione e il controllo delle versioni non è abilitato e/o il database non è di sola lettura, si verifica un errore. Inoltre, si verificherà l'errore XACT_E_ISOLATIONLEVEL se ISOLATIONLEVEL_SNAPSHOT è specificato come il *isoLevel* quando si è connessi a una versione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] anteriore [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].|  
|*isoFlag*[in]|Il Driver OLE DB per SQL Server restituisce un errore per qualsiasi valore diverso da zero.|  
|*pOtherOptions*[in]|Se non è NULL, il Driver OLE DB per SQL Server richiede l'oggetto opzioni dall'interfaccia. Il Driver OLE DB per SQL Server restituisce XACT_E_NOTIMEOUT se l'oggetto opzioni *ulTimeout* membro non è zero. Il Driver OLE DB per SQL Server ignora il valore della *szDescription* membro.|  
|*pulTransactionLevel*[out]|Se non è NULL, il Driver OLE DB per SQL Server restituisce il livello nidificato della transazione.|  
  
 Per le transazioni locali, il Driver OLE DB per SQL Server implementa **ITransaction:: Abort** parametri come indicato di seguito.  
  
|Parametro|Description|  
|---------------|-----------------|  
|*pboidReason*[in]|Ignorato se impostato. Può essere NULL.|  
|*fRetaining*[in]|Quando è TRUE, una nuova transazione viene iniziata implicitamente per la sessione. È necessario che il consumer esegua il commit o termini la transazione. Se è FALSE, il Driver OLE DB per SQL Server passa alla modalità di autocommit per la sessione.|  
|*fAsync*[in]|Un'interruzione asincrona non è supportata dal Driver OLE DB per SQL Server. Il Driver OLE DB per SQL Server restituisce XACT_E_NOTSUPPORTED se il valore è FALSE.|  
  
 Per le transazioni locali, il Driver OLE DB per SQL Server implementa **ITransaction:: commit** parametri come indicato di seguito.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*fRetaining*[in]|Quando è TRUE, una nuova transazione viene iniziata implicitamente per la sessione. È necessario che il consumer esegua il commit o termini la transazione. Se è FALSE, il Driver OLE DB per SQL Server passa alla modalità di autocommit per la sessione.|  
|*grfTC*[in]|Asincrono e restituisce una fase non sono supportati dal Driver OLE DB per SQL Server. Il Driver OLE DB per SQL Server restituisce XACT_E_NOTSUPPORTED per qualsiasi valore diverso da XACTTC_SYNC.|  
|*grfRM*[in]|Deve essere 0.|  
  
 Il Driver OLE DB per SQL Server i set di righe nella sessione vengono mantenuti in fase di commit locale o interrompere l'operazione in base ai valori delle proprietà del set di righe DBPROP_ABORTPRESERVE e DBPROP_COMMITPRESERVE. Per impostazione predefinita, queste proprietà sono VARIANT_FALSE e tutti i Driver OLE DB per SQL Server i set di righe nella sessione vengono persi in seguito a un'interruzione o commit di operazione.  
  
 Il Driver OLE DB per SQL Server non implementa il **ITransactionObject** interfaccia. Un tentativo del consumer di recuperare un riferimento dell'interfaccia restituisce E_NOINTERFACE.  
  
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
 [Transazioni](../../oledb/ole-db-transactions/transactions.md)   
 [Utilizzo dell'isolamento dello Snapshot](../../oledb/features/working-with-snapshot-isolation.md)  
  
  
