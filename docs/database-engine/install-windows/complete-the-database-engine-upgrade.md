---
title: "Completare l&#39;aggiornamento al motore di database | Microsoft Docs"
ms.custom: ""
ms.date: "09/22/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f08087e-e532-416c-8caa-e0ec88c57596
caps.latest.revision: 10
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 10
---
# Completare l&#39;aggiornamento al motore di database
  Dopo aver completato l'aggiornamento a SQL Server 2016, potrebbe essere necessario effettuare una serie di passaggi aggiuntivi. tra cui:  
  
 Al termine dell'aggiornamento del [!INCLUDE[ssDE](../../includes/ssde-md.md)], completare le operazioni seguenti:  
  
-   **Backup dei database:** eseguire un backup completo di ogni database aggiornato.  
  
-   **Abilitazione di nuove funzionalità:** in SQL Server 2016 alcune modifiche vengono abilitate solo dopo aver impostato il livello DATABASE_COMPATIBILITY di un database su 130.  Per altre informazioni e per il flusso di lavoro consigliato, vedere [Modificare la modalità di compatibilità del database e usare l'archivio query](../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md).  
  
-   **Integration Services:**  
  
     Eseguire la migrazione di pacchetti di Integration Services nel formato [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Per altre informazioni, vedere [Upgrade Integration Services Packages](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
-   **Reporting Services:** per un nuovo aggiornamento di installazione, ripristinare le chiavi di crittografia di Reporting Services. Per altre informazioni, vedere [Eseguire il backup e il ripristino delle chiavi di crittografia di Reporting Services](../../reporting-services/install-windows/back-up-and-restore-reporting-services-encryption-keys.md).  
  
-   **Master Data Services:** aggiornare lo schema del database MDS e creare l'applicazione Web di SQL Server 2016. Per altre informazioni, vedere [Aggiornare Master Data Services](../../database-engine/install-windows/upgrade-master-data-services.md).  
  
-   **Data Quality Services:** aggiornare lo schema del database DQS e verificarne l'aggiornamento. Per altre informazioni, vedere [Aggiornare Data Quality Services](../../database-engine/install-windows/upgrade-data-quality-services.md).  
  
-   **Ricerca full-text:** ripopolare cataloghi full-text per garantire la coerenza semantica nei risultati delle query. Per altre informazioni, vedere [Popolamento degli indici full-text](../../relational-databases/search/populate-full-text-indexes.md).  
  
## Questo articolo è stato utile? Commenti e suggerimenti  
 Quali informazioni si stanno cercando? La ricerca ha restituito i risultati desiderati? Microsoft incoraggia gli utenti a inviare i propri commenti per migliorare i contenuti Inviare eventuali commenti all'indirizzo [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Complete%20the%20Database%20Engine%20Upgrade%20page)  
  
  