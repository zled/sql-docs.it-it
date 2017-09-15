---
title: "Proprietà FetchOptions (RDS) | Documenti Microsoft"
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
- FetchOptions property [ADO]
ms.assetid: 7b2e254a-9354-4541-bc98-bb185276388f
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9ca6ede3ae154cbb3b6e13038185e4a54a466009
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="fetchoptions-property-rds"></a>Proprietà FetchOptions (RDS)
Indica il tipo di recupero asincrono.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="setting-and-return-values"></a>Impostazioni e valori restituiti  
 Imposta o restituisce uno dei valori seguenti.  
  
|Costante|Description|  
|--------------|-----------------|  
|**adcFetchUpFront**|Tutti i record del [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) vengono recuperati prima che il controllo viene restituito all'applicazione. L'intero **Recordset** viene recuperato prima che l'applicazione è possibile utilizzarlo.|  
|**valore adcFetchBackground**|Controllo può restituire all'applicazione, non appena il primo batch di record è stato recuperato. Una lettura successiva del **Recordset** che tenta di accedere a un record non recuperato nel primo batch verrà ritardata fino al recupero record ricercato è in realtà, in cui il tempo di controllo viene restituito all'applicazione.|  
|**adcFetchAsync**|Valore predefinito. Controllo viene restituito immediatamente all'applicazione durante i record vengono recuperati in background. Se l'applicazione tenta di leggere un record che non è ancora stato recuperato, verrà letto il record più vicino a quello ricercato e controllo restituirà immediatamente, che indica che alla fine corrente del **Recordset** è stato raggiunto. Ad esempio, una chiamata a [MoveLast](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md) spostare la posizione corrente all'ultimo record effettivamente recuperato, anche se altri record continueranno popolare il **Recordset**.|  
  
> [!NOTE]
>  Ogni file eseguibile sul lato client che utilizza queste costanti è necessario fornire le relative dichiarazioni. È possibile tagliare e incollare le dichiarazioni di costante desiderato dal file Adcvbs. Inc, che si trova nella cartella di installazione predefinito per la libreria di servizi desktop remoto.  
  
## <a name="remarks"></a>Osservazioni  
 In un'applicazione Web, è possibile utilizzare **adcFetchAsync** (valore predefinito), in quanto fornisce prestazioni migliori. In un'applicazione client compilata, è possibile utilizzare **il valore adcFetchBackground**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [ExecuteOptions e FetchOptions proprietà esempio (VBScript)](../../../ado/reference/rds-api/executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Metodo Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)



