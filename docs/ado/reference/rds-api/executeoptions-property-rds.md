---
title: "Proprietà ExecuteOptions (RDS) | Documenti Microsoft"
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
- ExecuteOptions property [ADO], VBScript example
ms.assetid: 62a4fd88-afc3-4f1f-b978-40710a30c4e9
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 29d46a26f7e4a80ae7a22954f388597552a5fb86
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="executeoptions-property-rds"></a>Proprietà ExecuteOptions (RDS)
Indica se è abilitata l'esecuzione asincrona.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Imposta o restituisce uno dei valori seguenti.  
  
|Costante|Description|  
|--------------|-----------------|  
|**adcExecSync**|Esegue l'aggiornamento successivo del [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) in modo sincrono.|  
|**adcExecAsync**|Valore predefinito. Esegue l'aggiornamento successivo del **Recordset** in modo asincrono.|  
  
> [!NOTE]
>  Ogni file eseguibile che utilizza queste costanti è necessario fornire le relative dichiarazioni. È possibile tagliare e incollare le dichiarazioni di costante desiderati dal file Adcvbs. Inc, che si trova nella cartella di installazione predefinito per la libreria di servizi desktop remoto.  
  
## <a name="remarks"></a>Osservazioni  
 Se **ExecuteOptions** è impostato su **adcExecAsync**, quindi si esegue in modo asincrono la successiva **aggiornamento** chiamare sul [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) dell'oggetto **Recordset**.  
  
 Se si tenta di chiamare [reimpostare](../../../ado/reference/rds-api/reset-method-rds.md), [aggiornamento](../../../ado/reference/rds-api/refresh-method-rds.md), [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md), [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md), o [Recordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) mentre un'altra operazione asincrona che modifichino la [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) dell'oggetto **Recordset** è in esecuzione, si verifica un errore.  
  
 Se si verifica un errore durante un'operazione asincrona, il **RDS. DataControl** dell'oggetto [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md) valore viene modificato da **adcReadyStateLoaded** a **adcReadyStateComplete**e  **Recordset** valore della proprietà rimane *nulla*.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [ExecuteOptions e FetchOptions proprietà esempio (VBScript)](../../../ado/reference/rds-api/executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Metodo Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)



