---
title: Metodo Refresh (RDS) | Documenti Microsoft
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Refresh
- RDS.DataControl::Refresh
- DataControl::Refresh
helpviewer_keywords:
- Refresh method [RDS]
ms.assetid: c90a8050-0ff4-4c83-9925-261f2f2ccfe9
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee9fd5b4748d2343b78e2dc696e7826341223d53
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35288420"
---
# <a name="refresh-method-rds"></a>Metodo Refresh (RDS)
Riesegue l'origine dati specificata una query di [Connetti](../../../ado/reference/rds-api/connect-property-rds.md) proprietà e gli aggiornamenti, i risultati della query.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataControl.Refresh  
```  
  
#### <a name="parameters"></a>Parametri  
 *DataControl*  
 Una variabile oggetto che rappresenta un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto.  
  
## <a name="remarks"></a>Remarks  
 È necessario impostare il [Connetti](../../../ado/reference/rds-api/connect-property-rds.md), [Server](../../../ado/reference/rds-api/server-property-rds.md), e [SQL](../../../ado/reference/rds-api/sql-property.md) proprietà prima di utilizzare il **aggiornamento** metodo. Tutti i controlli con associazione a dati nel form di cui è associato un **RDS. DataControl** oggetto rifletterà il nuovo set di record. Pre-esistente [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto viene rilasciato e le modifiche non salvate vengono eliminate. Il **aggiornamento** metodo imposta automaticamente il primo record del record corrente.  
  
 È consigliabile chiamare il **aggiornamento** metodo periodicamente quando si utilizzano dati. Se si recuperano dati e quindi lasciato in un computer client per un periodo di tempo, è probabile che diventi obsoleto. È possibile che eventuali modifiche apportate avrà esito negativo, perché un altro utente sia stato modificato il record e inviati prima di procedere.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio del metodo Refresh (VB)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Esempio del metodo Refresh (VBScript)](../../../ado/reference/rds-api/refresh-method-example-vbscript.md)   
 [Pulsanti di Address Book comando](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [Metodo CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Metodo Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)   
 [Metodo SubmitChanges (Servizi Desktop remoto)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


