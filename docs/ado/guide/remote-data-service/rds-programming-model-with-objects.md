---
title: Modello di programmazione di servizi desktop remoto con gli oggetti | Documenti Microsoft
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
- RDS programming model [ADO]
- RDS objects [ADO]
ms.assetid: 07ce0ef0-72f1-48f4-823d-1b65d28c0926
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d0f2d2e5cfb50df5fa6a6b1eaace7ba285b0855e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="rds-programming-model-with-objects"></a>Modello di programmazione di servizi desktop remoto con gli oggetti
L'obiettivo di servizi desktop remoto è per accedere e aggiornare origini dati tramite un intermediario, ad esempio IIS. Il modello di programmazione specifica la sequenza di attività necessarie per raggiungere questo obiettivo. Il modello a oggetti specifica gli oggetti i cui metodi e proprietà influiscono sul modello di programmazione.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Servizi Desktop remoto consente di eseguire la sequenza di azioni seguente:  
  
-   Specificare il programma da richiamare sul server e ottenere un modo (proxy) per farvi riferimento dal client ([RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)).  
  
-   Richiamare il programma del server. Passare i parametri per l'applicazione server che identifica l'origine dati e il comando da eseguire (proxy o [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)).  
  
-   L'applicazione server Ottiene un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto dall'origine dati, in genere utilizzando ADO. Facoltativamente, il **Recordset** oggetto viene elaborato nel server ([RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)).  
  
-   L'applicazione server restituisce finale **Recordset** oggetto all'applicazione client (proxy).  
  
-   Nel client, il **Recordset** oggetto viene inserito in un form che può essere facilmente usato dai controlli visual (controllo visual e **RDS. DataControl**).  
  
-   Diventa il **Recordset** oggetto vengono inviati al server e utilizzato per aggiornare l'origine dati (**RDS. DataControl** o **RDSServer**).  
  
## <a name="see-also"></a>Vedere anche  
 [Riepilogo del modello oggetto di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-object-model-summary.md)   
 [Oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Oggetto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [Oggetto DataSpace (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)   
 [Scenario di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Esercitazione di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Utilizzo e sicurezza per RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


