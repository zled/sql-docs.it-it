---
title: Ridurre l'utilizzo dello spazio File di Log | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- log file space in RDS [ADO]
ms.assetid: 669662a0-e20f-483e-ab28-53f66c524c98
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43ec9c0f933c33b9e8b5e99cd68b3fbf23d80d0e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="minimizing-log-file-space-usage"></a>Ridurre l'utilizzo dello spazio File di Log
Un file di log può riempirsi rapidamente (sospendendo il server) se è presente un volume elevato di attività in un database di SQL Server. È possibile impostare il file di log **Truncate on Checkpoint** estendere in modo significativo il ciclo di vita del file di log per un database.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-65"></a>Per attivare Troncamento log in corrispondenza del Checkpoint in Microsoft SQL Server 6.5  
  
1.  Avviare Microsoft SQL Server Enterprise Manager, aprire la struttura ad albero per il Server e quindi aprire la struttura ad albero di dispositivi di Database.  
  
2.  Fare doppio clic sul nome del database in cui verrà abilitata questa funzionalità.  
  
3.  Dal **Database** , selezionare **Truncate**.  
  
4.  Dal **opzioni** , selezionare **Truncate Log on Checkpoint**, quindi fare clic su **OK**.  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-70"></a>Per attivare Troncamento log in corrispondenza del Checkpoint in Microsoft SQL Server 7.0  
  
1.  Avviare Microsoft SQL Server Enterprise Manager, aprire la struttura ad albero per il Server e quindi aprire la struttura di database.  
  
2.  Il nome del database in cui questa funzionalità verrà abilitata e scegliere destro **proprietà**.  
  
3.  Dal **opzioni** , selezionare **Truncate Log on Checkpoint**, quindi fare clic su **OK**.  
  
 Per ulteriori informazioni sul **Truncate on Checkpoint** funzionalità, vedere la documentazione di Microsoft SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali su RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


