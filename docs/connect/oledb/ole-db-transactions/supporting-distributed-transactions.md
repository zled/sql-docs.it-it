---
title: Supporto delle transazioni distribuite | Documenti Microsoft
description: Transazioni distribuite nel Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- distributed transactions [OLE DB]
- MS DTC
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
- ITransactionJoin interface
- MS DTC, about distributed transaction support
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8e738e8bb125350d8d4aec91317495fc4c1fa489
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="supporting-distributed-transactions"></a>Supporto di transazioni distribuite
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il Driver OLE DB per i consumer di SQL Server può utilizzare il **ITransactionJoin:: Jointransaction** (metodo) deve far parte di una transazione distribuita coordinata da Microsoft Distributed Transaction Coordinator (MS DTC).  
  
 MS DTC espone oggetti COM che consentono ai client di avviare e partecipare a transazioni coordinate tra più connessioni a un'ampia gamma di archivi dati. Per avviare una transazione, il Driver OLE DB per il consumer di SQL Server utilizza MS DTC **ITransactionDispenser** interfaccia. Il **BeginTransaction** membro di **ITransactionDispenser** restituisce un riferimento in un oggetto di transazione distribuita. Questo riferimento viene passato per il Driver OLE DB per SQL Server utilizzando **JoinTransaction**.  
  
 MS DTC supporta il commit asincrono e l'interruzione nelle transazioni distribuite. Per la notifica sullo stato di transazione asincrona, il consumer implementa il **ITransactionOutcomeEvents** l'interfaccia e si connette l'interfaccia a un oggetto transazione MS DTC.  
  
 Per le transazioni distribuite, il Driver OLE DB per SQL Server implementa **ITransactionJoin:: Jointransaction** parametri come indicato di seguito.  
  
|Parametro|Description|  
|---------------|-----------------|  
|*punkTransactionCoord*|Puntatore a un oggetto transazione MS DTC.|  
|*IsoLevel*|Ignorata dal Driver OLE DB per SQL Server. Il livello di isolamento per le transazioni coordinate da MS DTC viene determinato quando il consumer acquisisce un oggetto transazione da MS DTC.|  
|*IsoFlag*|Deve essere 0. Il Driver OLE DB per SQL Server restituisce XACT_E_NOISORETAIN se qualsiasi altro valore viene specificato dal consumer.|  
|*POtherOptions*|Se non è NULL, il Driver OLE DB per SQL Server richiede l'oggetto opzioni dall'interfaccia. Il Driver OLE DB per SQL Server restituisce XACT_E_NOTIMEOUT se l'oggetto opzioni *ulTimeout* membro non è zero. Il Driver OLE DB per SQL Server ignora il valore della *szDescription* membro.|  
  
 In questo esempio viene coordinata la transazione tramite MS DTC.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*       pIDBCreateSession   = NULL;  
ITransactionJoin*       pITransactionJoin   = NULL;  
IDBCreateCommand*       pIDBCreateCommand   = NULL;  
IRowset*                pIRowset            = NULL;  
  
// Transaction dispenser and transaction from MS DTC.  
ITransactionDispenser*  pITransactionDispenser = NULL;  
ITransaction*           pITransaction       = NULL;  
  
    HRESULT             hr;  
  
// Get the command creation interface for the session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
// Get a transaction dispenser object from MS DTC and  
// start a transaction.  
if (FAILED(hr = DtcGetTransactionManager(NULL, NULL,  
    IID_ITransactionDispenser, 0, 0, NULL,  
    (void**) &pITransactionDispenser)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
if (FAILED(hr = pITransactionDispenser->BeginTransaction(  
    NULL, ISOLATIONLEVEL_READCOMMITTED, ISOFLAG_RETAIN_DONTCARE,  
    NULL, &pITransaction)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
  
// Join the transaction.  
if (FAILED(pIDBCreateCommand->QueryInterface(IID_ITransactionJoin,  
    (void**) &pITransactionJoin)))  
    {  
    // Process failure to get an interface, release any references, and  
    // then return.  
    }  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) pITransaction, 0, 0, NULL)))  
    {  
    // Process join failure, release any references, and then return.  
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
    // Get error from update, then abort.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, 0, 0)))  
        {  
        // Get error from failed commit.  
        //  
        // If a distributed commit fails, application logic could  
        // analyze failure and retry. In this example, terminate. The   
        // consumer must resolve this somehow.  
        pITransaction->Abort(NULL, FALSE, FALSE);  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Un-enlist from the distributed transaction by setting   
// the transaction object pointer to NULL.  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) NULL, 0, 0, NULL)))  
    {  
    // Process failure, and then return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Transazioni](../../oledb/ole-db-transactions/transactions.md)  
  
  
