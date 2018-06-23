---
title: 'Issasynchstatus:: Abort (OLE DB) | Documenti Microsoft'
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
api_name:
- ISSAsynchStatus::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: 2a4bd312-839a-45a8-a299-fc8609be9a2a
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cf068643e99360ab5ca50b5afad9d9c06f1c0524
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167589"
---
# <a name="issasynchstatusabort-ole-db"></a>ISSAsynchStatus::Abort (OLE DB)
  Annulla un'operazione di esecuzione asincrona.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT Abort(  
  HCHAPTER hChapter,  
  DBASYNCHOP eOperation);  
```  
  
## <a name="arguments"></a>Argomenti  
 *hChapter*[in]  
 Handle del capitolo per il quale interrompere l'operazione. Se l'oggetto chiamato non è un oggetto set di righe o l'operazione non è applicabile a un capitolo, il chiamante deve impostare *hChapter* su DB_NULL_HCHAPTER.  
  
 *eOperation*[in]  
 Operazione da interrompere. Deve corrispondere al valore seguente:  
  
 DBASYNCHOP_OPEN: la richiesta di annullamento si applica all'apertura o al popolamento asincrono di un set di righe o all'inizializzazione asincrona di un oggetto origine dati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 La richiesta di annullare l'operazione asincrona è stata elaborata. Questo non garantisce che l'operazione stessa sia stata annullata. Per determinare se l'operazione è stata annullata, il consumer deve chiamare [issasynchstatus:: GetStatus](issasynchstatus-getstatus-ole-db.md) e verificare DB_E_CANCELED; tuttavia, potrebbe non essere restituito nella chiamata successiva.  
  
 DB_E_CANTCANCEL  
 Non è stato possibile annullare l'operazione asincrona.  
  
 DB_E_CANCELED  
 La richiesta di interrompere l'operazione asincrona è stata annullata durante le notifiche. L'operazione viene ancora eseguita in modo asincrono.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider.  
  
 E_INVALIDARG  
 Il *hChapter* parametro non è DB_NULL_HCHAPTER oppure *eOperation* non è DBASYNCH_OPEN.  
  
 E_UNEXPECTED  
 **Issasynchstatus:: Abort** è stato chiamato su un oggetto di origine dati su cui **IDBInitialize:: Initialize** non è stato chiamato o non è stata completata.  
  
 **Issasynchstatus:: Abort** è stato chiamato su un oggetto di origine dati su cui **IDBInitialize:: Initialize** è stato chiamato ma successivamente annullato prima dell'inizializzazione o è scaduta. L'oggetto origine dati è ancora non inizializzato.  
  
 **Issasynchstatus:: Abort** è stato chiamato su un set di righe in cui **ITransaction:: commit** o **ITransaction:: Abort** è stato chiamato in precedenza, e il set di righe non sono stati restare attiva quando il commit o interrompere e in uno stato non valido.  
  
 **Issasynchstatus:: Abort** è stato chiamato su un set di righe annullato in modo asincrono nella fase di inizializzazione. Il set di righe si trova in uno stato non valido.  
  
## <a name="remarks"></a>Remarks  
 L'interruzione dell'inizializzazione di un oggetto di origine dati o set di righe potrebbero lasciare l'oggetto di origine dati o set di righe in uno stato non valido, in modo che tutti i metodi diverso da **IUnknown** metodi restituiscono E_UNEXPECTED. Quando ciò accade, l'unica azione possibile per il consumer consiste nel rilasciare il set di righe o l'oggetto origine dati.  
  
 La chiamata **issasynchstatus:: Abort** e passa un valore per *eOperation* diverso da DBASYNCHOP_OPEN restituisce S_OK. Questo non implica che l'operazione sia stata completata o annullata.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di operazioni asincrone](../native-client/features/performing-asynchronous-operations.md)  
  
  