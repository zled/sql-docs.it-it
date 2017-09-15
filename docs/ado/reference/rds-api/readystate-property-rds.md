---
title: "Proprietà ReadyState (RDS) | Documenti Microsoft"
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
- ReadyState property [ADO]
ms.assetid: 5be75bc7-1171-4440-a37e-c8cc6b5cd865
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cfcc72e79e90e10885d329208208db2f1a0267f5
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="readystate-property-rds"></a>Proprietà ReadyState (RDS)
Indica lo stato di un [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto mentre recupera i dati nel relativo [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Imposta o restituisce uno dei valori seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|**adcReadyStateLoaded**|La query corrente è ancora in esecuzione e non di righe recuperate. Il **DataControl** dell'oggetto **Recordset** non è disponibile per l'utilizzo.|  
|**adcReadyStateInteractive**|Un set iniziale di righe recuperate dalla query corrente è stato archiviato nel **DataControl** dell'oggetto **Recordset** e sono disponibili per l'utilizzo. Le righe rimanenti sono ancora recuperate.|  
|**adcReadyStateComplete**|Tutte le righe recuperate dalla query corrente sono state archiviate nel **DataControl** dell'oggetto **Recordset** e sono disponibili per l'utilizzo.<br /><br /> Questo stato si verificherà anche se un'operazione interrotta a causa di un errore o se il **Recordset** oggetto non inizializzato.|  
  
> [!NOTE]
>  Ogni file eseguibile sul lato client che utilizza queste costanti è necessario fornire le relative dichiarazioni. È possibile tagliare e incollare le dichiarazioni di costante desiderato dal file Adcvbs. Inc, che si trova nella cartella di installazione predefinito per la libreria di servizi desktop remoto.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il [onReadyStateChange](../../../ado/reference/rds-api/onreadystatechange-event-rds.md) evento per monitorare le modifiche di **ReadyState** proprietà durante un'operazione di query asincrona. Questo è più efficiente rispetto alla verifica periodicamente il valore della proprietà.  
  
 Se si verifica un errore durante un'operazione asincrona, il **ReadyState** le modifiche alle proprietà **adcReadyStateComplete**, [stato](../../../ado/reference/ado-api/state-property-ado.md) proprietà viene cambiata da **adStateExecuting** a **adStateClosed**e **Recordset** oggetto [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà rimane *Nothing *.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà ReadyState (VBScript)](../../../ado/reference/rds-api/readystate-property-example-vbscript.md)   
 [Metodo Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Proprietà ExecuteOptions (RDS)](../../../ado/reference/rds-api/executeoptions-property-rds.md)



