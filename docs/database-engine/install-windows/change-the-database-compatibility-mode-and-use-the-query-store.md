---
title: "Modificare la modalità di compatibilità del database e usare l'archivio query | Microsoft Docs"
ms.custom: 
ms.date: 07/21/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- query plans [SQL Server], migrating
- upgrading SQL Server, migrating query plans
- plan guides [SQL Server], migrating query plans
ms.assetid: 7e02a137-6867-4f6a-a45a-2b02674f7e65
caps.latest.revision: "19"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: 514fe566dd9a26d4a6244e8fb067f97678d2dbc7
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="change-the-database-compatibility-mode-and-use-the-query-store"></a>Modificare la modalità di compatibilità del database e usare l'archivio query
In SQL Server 2016 e SQL Server 2017 alcune modifiche vengono abilitate solo dopo aver modificato il livello DATABASE_COMPATIBILITY di un database. Questa operazione viene eseguita per diversi motivi:  
  
- Poiché l'aggiornamento è un'operazione unidirezionale, in quanto non è possibile effettuare il downgrade del formato del file, è utile impostare l'abilitazione delle nuove funzionalità come un'operazione separata all'interno del database.  È possibile ripristinare un'impostazione a un livello di DATABASE_COMPATIBILITY precedente.  Il nuovo modello riduce il numero di operazioni che devono essere eseguite durante un intervallo di interruzione.  
  
- Le modifiche apportate a Query Processor possono avere effetti complessi.  Anche se una modifica "positiva" al sistema è ideale per la maggior parte dei clienti, potrebbe causare una regressione inaccettabile altrove in una query importante.  Separare la logica dal processo di aggiornamento consente a funzionalità quali l'archivio di query di ridurre rapidamente le regressioni della scelta del piano o persino di evitarle completamente nei server di produzione.  
  
> [!NOTE]  
>  Se il livello di compatibilità di un database utente era 100 o superiore prima dell'aggiornamento, rimane invariato dopo l'aggiornamento. Se il livello di compatibilità è 90 prima dell'aggiornamento, nel database aggiornato viene impostato su 100, ovvero sul livello di compatibilità supportato più basso in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. I livelli di compatibilità dei database tempdb, model, msdb e Resource vengono impostati sul livello di compatibilità corrente dopo l'aggiornamento. Per il database di sistema master viene mantenuto il livello di compatibilità precedente l'aggiornamento. 
  
 Il processo di aggiornamento per abilitare nuove funzionalità di Query Processor è correlato al modello di manutenzione post-rilascio del prodotto.  Alcune di queste correzioni vengono rilasciate con il flag di traccia 4199.  I clienti che necessitano di correzioni possono acconsentire esplicitamente a esse senza causare regressioni impreviste per altri clienti.  Il modello di manutenzione post-rilascio per gli aggiornamenti rapidi di Query Processor è documentato [qui](https://support.microsoft.com/en-us/kb/974006). A partire da SQL Server 2016 il passaggio a un nuovo livello di compatibilità implica che il flag di traccia 4199 non è più necessario, in quanto tali correzioni sono ora abilitate per impostazione predefinita nel livello di compatibilità più recente.  Come parte del processo di aggiornamento, è pertanto importante verificare che al termine del processo di aggiornamento il flag di traccia 4199 non sia abilitato.  
  
 Il flusso di lavoro consigliato per l'aggiornamento di Query Processor alla versione più recente del codice è:  
  
1.  Aggiornare un database a SQL Server 2016 senza modificare il livello di compatibilità del database, mantenendolo al livello precedente  
  
2.  Abilitare l'archivio query nel database. Per altre informazioni sull'abilitazione e l'uso dell'archivio query, vedere [Monitoring Performance By Using the Query Store](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md).  
  
3.  Attendere un tempo sufficiente per raccogliere dati rappresentativi del carico di lavoro.  
  
4.  Impostare il livello di compatibilità del database su quello attuale. 

   >[!NOTE]
   >Il livello di compatibilità più recente dipende dalla versione di SQL Server.
   >- SQL Server 2016: 130
   >- SQL Server 2017: 140

5. Valutare mediante SQL Server Management Studio se sono presenti regressioni delle prestazioni in query specifiche dopo la modifica del livello di compatibilità.
  
6.  Per i casi in cui sono presenti regressioni, forzare il piano precedente nell'archivio query.  
  
7.  Se non è possibile forzare i piani di query o se le prestazioni sono ancora insufficienti, è consigliabile ripristinare il livello di compatibilità all'impostazione precedente e contattare il supporto tecnico Microsoft.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare o modificare il livello di compatibilità di un database](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md)  
  
  
