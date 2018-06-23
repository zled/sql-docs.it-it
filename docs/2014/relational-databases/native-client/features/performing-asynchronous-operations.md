---
title: Eseguire le operazioni asincrone | Documenti Microsoft
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
- initialization [SQL Server Native Client]
- database connections [SQL Server Native Client]
- data access [SQL Server Native Client], asynchronous operations
- connections [SQL Server Native Client]
- asynchronous operations [SQL Server Native Client]
- rowsets [SQL Server], initializing
- SQLNCLI, asynchronous operations
- SQL Server Native Client, asynchronous operations
ms.assetid: 8fbd84b4-69cb-4708-9f0f-bbdf69029bcc
caps.latest.revision: 45
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3649167d51f86e8540bc21cc5d932d9203b98369
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156224"
---
# <a name="performing-asynchronous-operations"></a>Esecuzione di operazioni asincrone
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] consente alle applicazioni di eseguire operazioni asincrone sul database. L'elaborazione asincrona consente la restituzione immediata dei metodi senza bloccare il thread chiamante. Questa caratteristica offre molto della potenza e della flessibilità del multithreading, senza richiedere allo sviluppatore la creazione esplicita di thread o la gestione della sincronizzazione. Le applicazioni richiedono l'elaborazione asincrona in caso di inizializzazione di una connessione al database o di inizializzazione del risultato dall'esecuzione di un comando.  
  
## <a name="opening-and-closing-a-database-connection"></a>Apertura e chiusura di una connessione al database  
 Quando si utilizza il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client, le applicazioni progettate per inizializzare in modo asincrono un oggetto origine dati possono impostare il bit DBPROPVAL_ASYNCH_INITIALIZE nella proprietà DBPROP_INIT_ASYNCH prima di chiamare  **IDBInitialize:: Initialize**. Quando questa proprietà è impostata, il provider restituisce immediatamente dalla chiamata a **inizializzare** con S_OK, se l'operazione è stata completata immediatamente oppure DB_S_ASYNCHRONOUS, se l'inizializzazione continua in modo asincrono. Le applicazioni possono eseguire query per il **IDBAsynchStatus** oppure [ISSAsynchStatus](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)interfaccia sull'oggetto origine dati e quindi chiamare **idbasynchstatus:: GetStatus** o[ Issasynchstatus:: Waitforasynchcompletion](../../native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md) per ottenere lo stato dell'inizializzazione.  
  
 È stata inoltre aggiunta la proprietà SSPROP_ISSAsynchStatus al set di proprietà DBPROPSET_SQLSERVERROWSET. I provider che supportano la **ISSAsynchStatus** interfaccia deve implementare questa proprietà con un valore VARIANT_TRUE.  
  
 **Idbasynchstatus:: Abort** oppure [issasynchstatus:: Abort](../../native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md) può essere chiamato per annullare asincrona **inizializzare** chiamare. Il consumer deve richiedere in modo esplicito l'inizializzazione asincrona dell'origine dati. In caso contrario, **IDBInitialize:: Initialize** non termina finché l'oggetto origine dati sia completamente inizializzato.  
  
> [!NOTE]  
>  Oggetti origine dati utilizzati per il pool di connessioni non è possibile chiamare il **ISSAsynchStatus** interfaccia nel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client. Il **ISSAsynchStatus** interfaccia non è esposta per gli oggetti origine dati in pool.  
>   
>  Se un'applicazione forza in modo esplicito l'utilizzo del motore del cursore **IOpenRowset:: OPENROWSET** e **IMultipleResults:: GetResult** non supporterà l'elaborazione asincrona.  
>   
>  Inoltre, non è possibile chiamare la dll proxy/stub remoting (in MDAC 2.8) il **ISSAsynchStatus** interfaccia nelle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Il **ISSAsynchStatus** interfaccia non è esposta attraverso la comunicazione remota.  
>   
>  Componenti del servizio non supportano **ISSAsynchStatus**.  
  
## <a name="execution-and-rowset-initialization"></a>Esecuzione e inizializzazione del set di righe  
 Le applicazioni progettate per aprire in modo asincrono il risultato dall'esecuzione di un comando possono impostare il bit DBPROPVAL_ASYNCH_INITIALIZE nella proprietà DBPROP_ROWSET_ASYNCH. Quando si imposta questo bit prima di chiamare **IDBInitialize:: Initialize**, **ICommand:: Execute**, **IOpenRowset:: OPENROWSET** o **IMultipleResults:: GetResult**, il *riid* argomento deve essere impostato su IID_IDBAsynchStatus, IID_ISSAsynchStatus o IID_IUnknown.  
  
 Il metodo restituisce immediatamente S_OK se l'inizializzazione di set di righe viene completata immediatamente oppure db_s_asynchronous se il set di righe continua a essere inizializzato in modo asincrono, con *ppRowset* attivata l'interfaccia richiesta la set di righe. Per il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client, questa interfaccia può essere solo **IDBAsynchStatus** o **ISSAsynchStatus**. Fino a quando il set di righe è completamente inizializzato, l'interfaccia si comporta come se fosse in stato di sospensione e chiamare **QueryInterface** per le interfacce diverse da **IID_IDBAsynchStatus** o **IID _ ISSAsynchStatus** può restituire E_NOINTERFACE. A meno che il consumer non richieda in modo esplicito l'elaborazione asincrona, il set di righe viene inizializzato in modo sincrono. Tutte le interfacce richieste sono disponibili quando **idbasynchstaus:: GetStatus** oppure **Waitforasynchcompletion** restituisce l'indicazione che l'operazione asincrona è stata completata. Ciò non significa necessariamente che il set di righe è completamente popolato, ma che è completo e del tutto funzionale.  
  
 Se il comando eseguito restituisce un set di righe, restituisce comunque immediatamente con un oggetto che supporta **IDBAsynchStatus**.  
  
 Se è necessario ottenere più risultati dall'esecuzione di comandi asincrona, effettuare le operazioni seguenti:  
  
-   Impostare il bit DBPROPVAL_ASYNCH_INITIALIZE della proprietà DBPROP_ROWSET_ASYNCH prima di eseguire il comando.  
  
-   Chiamare **ICommand:: Execute**e richiesta **IMultipleResults**.  
  
 Il **IDBAsynchStatus** e **ISSAsynchStatus** interfacce possono quindi essere ottenute eseguendo una query il più interfaccia risultati utilizzando **QueryInterface**.  
  
 Quando il comando è stata eseguita, **IMultipleResults** può essere utilizzato come al solito, con un'eccezione dal caso sincrono: può essere restituito DB_S_ASYNCHRONOUS, nel qual caso **IDBAsynchStatus** o **ISSAsynchStatus** può essere utilizzato per determinare quando è stata completata l'operazione.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente l'applicazione chiama un metodo non bloccante, esegue altre attività di elaborazione e quindi torna a elaborare i risultati. **Issasynchstatus:: Waitforasynchcompletion** attende l'oggetto evento interno fino al completamento dell'operazione di esecuzione in modo asincrono o la quantità di tempo specificato da *dwMilisecTimeOut* viene passato.  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
  
DBPROPSET CmdPropset[1];  
DBPROP CmdProperties[1];  
  
CmdPropset[0].rgProperties = CmdProperties;  
CmdPropset[0].cProperties = 1;  
CmdPropset[0].guidPropertySet = DBPROPSET_ROWSET;  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
CmdProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
  
hr = pICommandProps->SetProperties(1, CmdPropset);  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if ( hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 **Issasynchstatus:: Waitforasynchcompletion** rimane in attesa per l'oggetto evento interno fino al completamento dell'operazione di esecuzione in modo asincrono o la *dwMilisecTimeOut* valore viene passato.  
  
 Nell'esempio seguente viene illustrata l'elaborazione asincrona con più set di risultati:  
  
```  
DBPROP CmdProperties[1];  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_IMultipleResults,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pIMultipleResults);  
  
// Use GetResults for ISSAsynchStatus.  
hr = pIMultipleResults->GetResult(IID_ISSAsynchStatus, (void **) &pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if (hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 Per impedire il blocco, il client può controllare lo stato di un'operazione asincrona in esecuzione, come nell'esempio seguente:  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);   
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   do{  
      // Do some work...  
      hr = pISSAsynchStatus->GetStatus(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN, NULL, NULL, &ulAsynchPhase, NULL);  
   }while (DBASYNCHPHASE_COMPLETE != ulAsynchPhase)  
   if SUCCEEDED(hr)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
   }  
   pIDBAsynchStatus->Release();  
}  
```  
  
 Nell'esempio seguente viene illustrato come annullare l'operazione asincrona attualmente in esecuzione:  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work...  
   hr = pISSAsynchStatus->Abort(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità di SQL Server Native Client](sql-server-native-client-features.md)   
 [Proprietà e comportamenti dei set di righe](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)   
 [ISSAsynchStatus &#40;OLE DB&#41;](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  