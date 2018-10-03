---
title: Completare l'aggiornamento al motore di database | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.prod: sql
ms.technology: install
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 3f08087e-e532-416c-8caa-e0ec88c57596
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 9073bdc80d110df5c4b56d8130f12bae723047e7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47824159"
---
# <a name="complete-the-database-engine-upgrade"></a>Completare l'aggiornamento al motore di database

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dopo aver completato l'aggiornamento a SQL Server, potrebbe essere necessario effettuare una serie di passaggi aggiuntivi. tra cui:  
  
Al termine dell'aggiornamento del [!INCLUDE[ssDE](../../includes/ssde-md.md)], completare le operazioni seguenti:  
  
- **Backup dei database:** eseguire un backup completo di ogni database.  

- **Abilitazione di nuove funzionalità:** in SQL Server 2016 e SQL Server 2017 alcune modifiche vengono abilitate solo dopo aver impostato il livello DATABASE_COMPATIBILITY di un database su 130 o superiore.  Per altre informazioni e per il flusso di lavoro consigliato, vedere [Modificare la modalità di compatibilità del database e usare l'archivio query](../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md). Se il database contiene tabelle ottimizzate per la memoria create in SQL Server 2014, vedere [Statistiche per tabelle ottimizzate per la memoria](../../relational-databases/in-memory-oltp/statistics-for-memory-optimized-tables.md).
  
- **Integration Services:**  
  
     Eseguire la migrazione di pacchetti di Integration Services nel formato [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Per altre informazioni, vedere [Upgrade Integration Services Packages](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
- **Reporting Services:** per un nuovo aggiornamento di installazione, ripristinare le chiavi di crittografia di Reporting Services. Per altre informazioni, vedere [Eseguire il backup e il ripristino delle chiavi di crittografia di Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).  
  
- **Master Data Services:**  aggiornare lo schema del database MDS e creare l'applicazione Web di SQL Server 2017. Per altre informazioni, vedere [Aggiornare Master Data Services](../../database-engine/install-windows/upgrade-master-data-services.md).  
  
- **Data Quality Services:** aggiornare lo schema del database DQS e verificarne l'aggiornamento. Per altre informazioni, vedere [Aggiornare Data Quality Services](../../database-engine/install-windows/upgrade-data-quality-services.md).  
  
- **Ricerca full-text:** ripopolare cataloghi full-text per garantire la coerenza semantica nei risultati delle query. Per altre informazioni sugli indici full-text, vedere [Popolamento degli indici full-text](../../relational-databases/search/populate-full-text-indexes.md).  
  
