---
title: 'Issasynchstatus:: (OLE DB) | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
apitype: COM
helpviewer_keywords:
- WaitForAsynchCompletion method
ms.assetid: 9f65e9e7-eb93-47a1-bc42-acd4649fbd0e
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1e8674fe49659d71dd825c9501a7215f523df1e4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="issasynchstatuswaitforasynchcompletion-ole-db"></a>ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Resta in attesa fino al completamento dell'operazione di esecuzione asincrona o fino al verificarsi di un timeout.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT WaitForAsynchCompletion(   
        DWORD dwMillisecTimeOut);  
```  
  
## <a name="arguments"></a>Argomenti  
 *dwMillisecTimeOut*[in]  
 Timeout in millisecondi.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito.  
  
 E_UNEXPECTED  
 Un set di righe è in uno stato inutilizzato perché **ITransaction:: commit** o **ITransaction:: Abort** è stato chiamato o il set di righe è stata annullata durante la fase di inizializzazione.  
  
 DB_E_CANCELED  
 L'elaborazione asincrona è stata annullata durante il popolamento del set di righe o l'inizializzazione dell'oggetto origine dati.  
  
 DB_S_ASYNCHRONOUS  
 L'operazione non è stata ancora completata anche se è stato raggiunto il timeout specificato.  
  
> [!NOTE]  
>  Oltre ai valori restituiti elencati in precedenza, il **issasynchstatus::** metodo supporta anche i valori di codice restituito restituiti da OLE DB principali **ICommand:: Execute** e **IDBInitialize:: Initialize** metodi.  
  
## <a name="remarks"></a>Osservazioni  
 Il **issasynchstatus::** non restituirà fino a quando non ha superato il valore di timeout (in millisecondi) o viene eseguito l'operazione in sospeso. Il **comando** oggetto ha un **CommandTimeout** proprietà che controlla il numero di secondi prima del timeout verrà eseguita una query. Il **CommandTimeout** proprietà verrà ignorata se utilizzata in combinazione con **issasynchstatus::** metodo.  
  
 La proprietà di timeout viene ignorata per le operazioni asincrone. Il parametro di timeout di **issasynchstatus::** specifica la quantità massima di tempo che deve trascorrere prima che il controllo viene restituito al chiamante. Se questo timeout scade, verrà restituito DB_S_ASYNCHRONOUS. I timeout non annullano mai operazioni asincrone. Se l'applicazione deve annullare un'operazione asincrona che non viene completata entro il periodo di timeout, deve attendere lo scadere del timeout e quindi annullare in modo esplicito l'operazione se viene restituito DB_S_ASYNCHRONOUS.  
  
> [!NOTE]  
>  Quando si utilizzano i componenti servizi OLE DB, potrebbe essere restituito S_OK quando è previsto DB_S_ASYNCHRONOUS, pertanto le applicazioni devono chiamare [issasynchstatus:: GetStatus](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-getstatus-ole-db.md) per verificare il completamento quando viene restituito S_OK o DB_S_ASYNCHRONOUS.  
  
 Se il *dwMillisecTimeOut* è impostato su INFINITE, il **issasynchstatus::** metodo si blocca fino a quando non viene eseguita l'operazione. Se il *dwMillisecTimeOut* è impostato su 0, quindi il metodo restituirà immediatamente lo stato dell'operazione in sospeso. Se il timeout scade prima del completamento dell'operazione, viene restituito DB_S_ASYNCHRONOUS.  
  
 Se l'operazione viene completata prima dello scadere del timeout, il valore HRESULT restituito sarà quello restituito dall'operazione, ovvero il valore HRESULT che sarebbe stato restituito se l'operazione fosse stata eseguita in modo sincrono.  
  
 È stata inoltre aggiunta la proprietà SSPROP_ISSAsynchStatus al set di proprietà DBPROPSET_SQLSERVERROWSET. I provider che supportano il [ISSAsynchStatus](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-ole-db.md) interfaccia deve implementare questa proprietà con un valore VARIANT_TRUE.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di operazioni asincrone](../../relational-databases/native-client/features/performing-asynchronous-operations.md)   
 [ISSAsynchStatus & #40; OLE DB & #41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
