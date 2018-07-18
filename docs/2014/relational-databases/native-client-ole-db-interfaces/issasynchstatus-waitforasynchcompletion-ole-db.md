---
title: 'Issasynchstatus:: Waitforasynchcompletion (OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- WaitForAsynchCompletion method
ms.assetid: 9f65e9e7-eb93-47a1-bc42-acd4649fbd0e
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10fa772517ac96f59510245ab25ef0e5a05438d8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425851"
---
# <a name="issasynchstatuswaitforasynchcompletion-ole-db"></a>ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
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
 Un set di righe è in uno stato inutilizzato perché **ITransaction** oppure **ITransaction:: Abort** è stato chiamato o il set di righe è stata annullata durante la fase di inizializzazione.  
  
 DB_E_CANCELED  
 L'elaborazione asincrona è stata annullata durante il popolamento del set di righe o l'inizializzazione dell'oggetto origine dati.  
  
 DB_S_ASYNCHRONOUS  
 L'operazione non è stata ancora completata anche se è stato raggiunto il timeout specificato.  
  
> [!NOTE]  
>  Oltre ai valori restituiti elencati in precedenza, il **issasynchstatus:: Waitforasynchcompletion** metodo supporta anche i valori restituiti da OLE DB principali **ICommand:: Execute** e **IDBInitialize:: Initialize** metodi.  
  
## <a name="remarks"></a>Note  
 Il **issasynchstatus:: Waitforasynchcompletion** non torna al metodo fino a quando non ha superato il valore di timeout (in millisecondi) o viene eseguita l'operazione in sospeso. Il **comandi** oggetto dispone di un **CommandTimeout** proprietà che controlla il numero di secondi prima del timeout viene eseguita una query. Il **CommandTimeout** proprietà verrà ignorata se utilizzata in combinazione con **issasynchstatus:: Waitforasynchcompletion** (metodo).  
  
 La proprietà di timeout viene ignorata per le operazioni asincrone. Il parametro di timeout della **issasynchstatus:: Waitforasynchcompletion** specifica la quantità massima di tempo che deve trascorrerà prima che il controllo viene restituito al chiamante. Se questo timeout scade, verrà restituito DB_S_ASYNCHRONOUS. I timeout non annullano mai operazioni asincrone. Se l'applicazione deve annullare un'operazione asincrona che non viene completata entro il periodo di timeout, deve attendere lo scadere del timeout e quindi annullare in modo esplicito l'operazione se viene restituito DB_S_ASYNCHRONOUS.  
  
> [!NOTE]  
>  Quando vengono utilizzati i componenti servizi OLE DB, potrebbe essere restituito S_OK quando è previsto DB_S_ASYNCHRONOUS, pertanto le applicazioni devono chiamare [issasynchstatus:: GetStatus](issasynchstatus-getstatus-ole-db.md) per verificare il completamento quando viene restituito S_OK o DB_S_ASYNCHRONOUS.  
  
 Se il *dwMillisecTimeOut* è impostato su INFINITE e il **issasynchstatus:: Waitforasynchcompletion** metodo si blocca fino a quando non viene eseguita l'operazione. Se il *dwMillisecTimeOut* valore è impostato su 0, quindi il metodo restituirà immediatamente lo stato dell'operazione in sospeso. Se il timeout scade prima del completamento dell'operazione, viene restituito DB_S_ASYNCHRONOUS.  
  
 Se l'operazione viene completata prima dello scadere del timeout, il valore HRESULT restituito sarà quello restituito dall'operazione, ovvero il valore HRESULT che sarebbe stato restituito se l'operazione fosse stata eseguita in modo sincrono.  
  
 È stata inoltre aggiunta la proprietà SSPROP_ISSAsynchStatus al set di proprietà DBPROPSET_SQLSERVERROWSET. I provider che supportano il [ISSAsynchStatus](issasynchstatus-ole-db.md) interfaccia deve implementare questa proprietà con un valore VARIANT_TRUE.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di operazioni asincrone](../native-client/features/performing-asynchronous-operations.md)   
 [ISSAsynchStatus &#40;OLE DB&#41;](issasynchstatus-ole-db.md)  
  
  
