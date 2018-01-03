---
title: Riepilogo del modello a oggetti RDS | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDS objects [ADO], object model summary
- RDS object model [ADO]
ms.assetid: 909f9af7-31db-4eec-ad52-650ce74dac2f
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 09738022f51016f50986e8f6164db87eff24d5f2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="rds-object-model-summary"></a>Riepilogo del modello oggetto di servizi desktop remoto
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
|Object|Description|  
|------------|-----------------|  
|[RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)|Questo oggetto contiene un metodo per ottenere un proxy server. Il proxy può essere il valore predefinito o un'applicazione server personalizzata (oggetto business). L'applicazione server può essere richiamata su Internet, intranet, una rete locale o da una libreria a collegamento dinamico locale.<br /><br /> Il **DataSpace** oggetto è sicuro per lo script.|  
|[RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|Questo oggetto rappresenta l'applicazione server predefinita. Esegue il servizio dati di riferimento dati aggiornamento e recupero comportamento predefinito.<br /><br /> Il **DataFactory** oggetto non è sicuro per lo scripting.|  
|[RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)|Questo oggetto può richiamare automaticamente il **RDS. DataSpace** e **RDSServer** oggetti.<br /><br /> Utilizzare questo oggetto per richiamare il comportamento di aggiornamento o il recupero dei dati di servizi desktop remoto predefinito.<br /><br /> Questo oggetto consente inoltre ai controlli visuali di accesso restituito **Recordset** oggetto.<br /><br /> Il **DataControl** oggetto è sicuro per lo script.|  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni di base di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [Scenario di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Esercitazione di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Utilizzo e sicurezza per RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


