---
title: Metodo SubmitChanges (RDS) | Documenti Microsoft
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: SubmitChanges method [ADO]
ms.assetid: 250062a4-13c4-4bed-807d-8b9ad81536d4
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fc04a3ac77d6363c86f684b474fb5fa9a06c3c5e
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="submitchanges-method-rds"></a>Metodo SubmitChanges (RDS)
Invia le modifiche di locale memorizzato nella cache e aggiornabile in sospeso [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) all'origine dati specificata nel [Connetti](../../../ado/reference/rds-api/connect-property-rds.md) proprietà o [URL](../../../ado/reference/rds-api/url-property-rds.md) proprietà.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataControl.SubmitChanges DataFactory.SubmitChanges Connection, Recordset  
```  
  
#### <a name="parameters"></a>Parametri  
 *DataControl*  
 Una variabile oggetto che rappresenta un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto.  
  
 *Data factory*  
 Una variabile oggetto che rappresenta un [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) oggetto.  
  
 *Connessione*  
 Oggetto **stringa** valore che rappresenta la connessione creata con la **RDS. DataControl** dell'oggetto [Connetti](../../../ado/reference/rds-api/connect-property-rds.md) proprietà.  
  
 *Recordset*  
 Una variabile oggetto che rappresenta un **Recordset** oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 Il [Connetti](../../../ado/reference/rds-api/connect-property-rds.md), [Server](../../../ado/reference/rds-api/server-property-rds.md), e [SQL](../../../ado/reference/rds-api/sql-property.md) devono essere impostate prima di poter usare il **SubmitChanges** metodo con il  **RDS. DataControl** oggetto.  
  
 Se si chiama il [CancelUpdate](../../../ado/reference/rds-api/cancelupdate-method-rds.md) metodo dopo aver chiamato **SubmitChanges** per lo stesso **Recordset** oggetto, il **CancelUpdate** chiamata non riesce perché le modifiche sono già state eseguite.  
  
 Esito positivo o negativo di tutte le modifiche contemporaneamente, solo i record modificati vengono inviati per la modifica e tutte le modifiche.  
  
 È possibile utilizzare **SubmitChanges** solo con il valore predefinito **RDSServer** oggetto. Gli oggetti di business personalizzata non è possibile utilizzare questo metodo.  
  
 Se il **URL** proprietà è stata impostata, **SubmitChanges** invierà le modifiche nel percorso specificato dall'URL.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[Oggetto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo SubmitChanges (VBScript)](../../../ado/reference/rds-api/submitchanges-method-example-vbscript.md)   
 [Pulsanti di Address Book comando](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [Metodo CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Metodo Refresh (Servizi Desktop remoto)](../../../ado/reference/rds-api/refresh-method-rds.md)



