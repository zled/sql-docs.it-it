---
title: Evento onReadyStateChange (RDS) | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- onReadyStateChange event [ADO]
ms.assetid: bf2ae3ac-bfe4-4709-b50a-ea7c282c3164
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cbc9538b623fdbd9182c98456a3a3b742fc878fe
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="onreadystatechange-event-rds"></a>Evento onReadyStateChange (RDS)
Il **onReadyStateChange** eventi viene chiamato ogni volta che il valore di [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md) le modifiche alle proprietà.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
onReadyStateChange  
```  
  
#### <a name="parameters"></a>Parametri  
 nessuna.  
  
## <a name="remarks"></a>Osservazioni  
 Il **ReadyState** proprietà riflette lo stato di avanzamento di un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto mentre recupera in modo asincrono i dati nel relativo [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto. Utilizzare il **onReadyStateChange** evento per monitorare le modifiche di **ReadyState** proprietà ogni volta che si verificano. Questo è più efficiente rispetto alla verifica periodicamente il valore della proprietà.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori di eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)



