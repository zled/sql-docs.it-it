---
title: I deadlock con livello di isolamento Repeatable Read | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deadlocks in RDS [ADO]
- read repeatable in RDS [ADO]
ms.assetid: 29f3683f-12f3-4304-8a54-fe133c25a423
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c871d2786202c74945aeec84c3de06a361d54801
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273980"
---
# <a name="deadlocks-with-read-repeatable-isolation-level"></a>Deadlock con livello di isolamento Repeatable Read
Se un oggetto business personalizzato utilizza un livello di isolamento di lettura ripetibile per accedere a SQL Server e l'oggetto business viene chiamato contemporaneamente da due client di inviare una query e aggiornare la stessa transazione, è possibile un deadlock. Remote Data Service è progettato per consentire a uno dei processi di timeout per rilasciare il deadlock, ma l'aggiornamento avrà esito negativo per quel client.  
  
 Utilizzare il [servizio cursore](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) **timeout del comando** proprietà dinamiche per modificare la durata del timeout.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali su RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)



