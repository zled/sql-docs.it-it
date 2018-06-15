---
title: 'Issasynchstatus:: Abort (OLE DB) | Documenti Microsoft'
description: ISSAsynchStatus::Abort (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSAsynchStatus::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: a62b87d7c2d8d19ce1c5ee3542932b13c37fd056
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35305470"
---
# <a name="issasynchstatusabort-ole-db"></a>ISSAsynchStatus::Abort (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

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
 Operazione da interrompere. Deve essere usato il valore seguente:  
  
 DBASYNCHOP_OPEN: la richiesta di annullamento si applica all'apertura o al popolamento asincrono di un set di righe o all'inizializzazione asincrona di un oggetto origine dati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 La richiesta di annullare l'operazione asincrona è stata elaborata. Non garantisce che l'operazione stessa è stata annullata. Per determinare se l'operazione è stata annullata, il consumer deve chiamare [issasynchstatus:: GetStatus](../../oledb/ole-db-interfaces/issasynchstatus-getstatus-ole-db.md) e verificare DB_E_CANCELED; tuttavia, potrebbe non essere restituito nella chiamata successiva.  
  
 DB_E_CANTCANCEL  
 Non è stato possibile annullare l'operazione asincrona.  
  
 DB_E_CANCELED  
 La richiesta di interrompere l'operazione asincrona è stata annullata durante le notifiche. L'operazione viene ancora eseguita in modo asincrono.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider.  
  
 E_INVALIDARG  
 Il *hChapter* parametro non è DB_NULL_HCHAPTER oppure *eOperation* non è DBASYNCH_OPEN.  
  
 E_UNEXPECTED  
 **Issasynchstatus:: Abort** è stato chiamato su un oggetto di origine dati su cui **IDBInitialize:: Initialize** non è ancora stato chiamato o non è completata.  
  
 **Issasynchstatus:: Abort** è stato chiamato su un oggetto di origine dati su cui **IDBInitialize:: Initialize** è stato chiamato ma successivamente annullato prima dell'inizializzazione o è scaduta. L'oggetto origine dati è ancora non inizializzato.  
  
 **Issasynchstatus:: Abort** è stato chiamato su un set di righe in cui **ITransaction:: commit** o **ITransaction:: Abort** è stato chiamato in precedenza, e il set di righe non restare attiva quando il commit o interrompere e in uno stato non valido.  
  
 **Issasynchstatus:: Abort** è stato chiamato su un set di righe annullato in modo asincrono nella fase di inizializzazione. Il set di righe si trova in uno stato non valido.  
  
## <a name="remarks"></a>Remarks  
 L'interruzione dell'inizializzazione di un oggetto di origine dati o set di righe potrebbe lasciare l'oggetto origine dati o set di righe in uno stato non valido, in modo che tutti i metodi diversi da **IUnknown** metodi restituiscono E_UNEXPECTED. Quando ciò accade, l'unica azione possibile per il consumer consiste nel rilasciare il set di righe o l'oggetto origine dati.  
  
 La chiamata **issasynchstatus:: Abort** e passando un valore per *eOperation* diverso da DBASYNCHOP_OPEN restituisce S_OK. Ciò non implica che l'operazione è stata completata o è stata annullata.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di operazioni asincrone](../../oledb/features/performing-asynchronous-operations.md)  
  
  
