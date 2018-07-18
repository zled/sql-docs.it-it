---
title: Riepilogo del modello a oggetti RDS | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS objects [ADO], object model summary
- RDS object model [ADO]
ms.assetid: 909f9af7-31db-4eec-ad52-650ce74dac2f
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01f4af73d416616eeba6d8bcba82c390b09c3b7f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="rds-object-model-summary"></a>Riepilogo del modello oggetto di servizi desktop remoto
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
|Oggetto|Description|  
|------------|-----------------|  
|[RDS.DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)|Questo oggetto contiene un metodo per ottenere un proxy server. Il proxy può essere il valore predefinito o un'applicazione server personalizzata (oggetto business). L'applicazione server può essere richiamata su Internet, intranet, una rete locale o da una libreria a collegamento dinamico locale.<br /><br /> Il **DataSpace** oggetto è sicuro per lo script.|  
|[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|Questo oggetto rappresenta l'applicazione server predefinita. Esegue il servizio dati di riferimento dati aggiornamento e recupero comportamento predefinito.<br /><br /> Il **DataFactory** oggetto non è sicuro per lo scripting.|  
|[RDS.DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)|Questo oggetto può richiamare automaticamente il **RDS. DataSpace** e **RDSServer** oggetti.<br /><br /> Utilizzare questo oggetto per richiamare il comportamento di aggiornamento o il recupero dei dati di servizi desktop remoto predefinito.<br /><br /> Questo oggetto consente inoltre ai controlli visuali di accesso restituito **Recordset** oggetto.<br /><br /> Il **DataControl** oggetto è sicuro per lo script.|  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni di base di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [Scenario di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Esercitazione di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Utilizzo e sicurezza per RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


