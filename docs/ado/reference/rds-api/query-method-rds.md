---
title: Eseguire una query (metodo) (RDS) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: Query method [ADO]
ms.assetid: 20f2480f-3758-405d-a379-05a0dce74796
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 32233e74eece2de258223599a682c8fb27d46fe6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="query-method-rds"></a>Metodo query (RDS)
Viene utilizzata una stringa di query SQL valida per restituire un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Set Recordset = DataFactory.Query(Connection, Query)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Recordset*  
 Una variabile oggetto che rappresenta un **Recordset** oggetto.  
  
 *Data factory*  
 Una variabile oggetto che rappresenta un [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) oggetto.  
  
 *Connessione*  
 Oggetto **stringa** valore che contiene le informazioni di connessione del server. È simile al [Connetti](../../../ado/reference/rds-api/connect-property-rds.md) proprietà.  
  
 *Query*  
 Oggetto **stringa** che contiene la query SQL.  
  
## <a name="remarks"></a>Osservazioni  
 La query deve utilizzare il sottolinguaggio SQL del server di database. Se si verifica un errore con la query che è stato eseguito, viene restituito uno stato del risultato. Il **Query** metodo non esegue alcuna sintassi per la **Query** stringa.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di oggetto DataFactory, metodo Query e metodo CreateObject (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)


