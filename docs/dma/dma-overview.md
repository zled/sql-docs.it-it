---
title: Panoramica di Data Migration Assistant (SQL Server) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2018
ms.prod: sql-non-specified
ms.prod_service: dma
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology:
- sql-dma
ms.tgt_pltfrm: 
ms.topic: article
keywords: 
helpviewer_keywords:
- Data Migration Assistant, overview
ms.assetid: 
caps.latest.revision: 
author: HJToland3
ms.author: jtoland
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c387e5bb2a0b5cef10217b32807f88a8aee6c627
ms.sourcegitcommit: 6b1618aa3b24bf6759b00a820e09c52c4996ca10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="overview-of-data-migration-assistant"></a>Panoramica dell'Assistente per la migrazione di dati

I dati della migrazione Assistente DMA () consente di eseguire l'aggiornamento a una piattaforma dati moderni rilevando problemi di compatibilità che possono influire sulla funzionalità del database nella nuova versione di SQL Server e Database SQL di Azure. DMA consiglia miglioramenti delle prestazioni e affidabilità per l'ambiente di destinazione e consente di spostare l'oggetto non contenuto, i dati e lo schema dal server di origine al server di destinazione.

> [!NOTE] 
> Per grandi dimensioni (in termini di numero e dimensioni di database) migrazioni, si consiglia di utilizzare il [servizio migrazione Database Azure](https://docs.microsoft.com/en-us/azure/dms/dms-overview), che può eseguire la migrazione di database su larga scala.
  
## <a name="capabilities"></a>Capabilities

- Valutare la migrazione a SQL Azure database istanze di SQL Server locale. Il flusso di lavoro di valutazione consente di rilevare i problemi che possono influire sulla migrazione di database SQL di Azure e fornisce indicazioni dettagliate su come risolverli.

  - Problemi di migrazione: consente di individuare i problemi di compatibilità che la migrazione di blocco in SQL Server locale database s per il database di SQL Azure. DMA fornisce indicazioni che consentono di risolvere tali problemi.

  - Parzialmente supportato o funzionalità non supportate: rileva le funzionalità parzialmente supportate o non supportate che sono attualmente in uso nell'istanza di SQL Server di origine. DMA fornisce che un set esaustivo di consigli, disponibile in Azure e attenuazione agli approcci alternativi, in modo che è possibile incorporare i progetti di migrazione.

- Individuare i problemi che possono influire sull'aggiornamento a un Server SQL locale. Questi sono descritte come problemi di compatibilità e sono organizzati nelle categorie seguenti:

  - Modifiche di rilievo
  - Modifiche del comportamento
  - Funzionalità deprecate

- Scoprire nuove funzionalità della piattaforma di SQL Server di destinazione che il database può trarre vantaggio da dopo un aggiornamento. Questi sono descritte come indicazioni di funzionalità e sono organizzati nelle categorie seguenti:

  - restazioni
  - Sicurezza
  - Archiviazione

- Eseguire la migrazione di un'istanza di SQL Server locale a un'istanza di SQL Server più recenti, ospitata in locale o in una macchina virtuale di Azure (VM) che è accessibile dalla rete locale. La macchina virtuale di Azure è possibile accedere tramite VPN o altre tecnologie. Il flusso di lavoro di migrazione consente di eseguire la migrazione dei componenti seguenti:

  - Schema di database
  - Dati e utenti
  - Ruoli del server
  - Account di accesso di SQL Server e Windows

- Dopo la migrazione ha esito positivo, le applicazioni possono connettersi ai database di destinazione SQL server senza problemi.

## <a name="supported-source-and-target-versions"></a>Versioni supportate di origine e di destinazione

DMA sostituisce tutte le versioni precedenti di preparazione aggiornamento di SQL Server e deve essere utilizzato per gli aggiornamenti per la maggior parte delle versioni di SQL Server. Seguono le versioni supportate di origine e di destinazione.

**Origini**
- SQL Server 2005
- SQL Server 2008
- SQL Server 2008 R2
- SQL Server 2012 
- SQL Server 2014
- SQL Server 2016
- SQL Server, 2017 in Windows

**Destinazioni**
- SQL Server 2012
- SQL Server 2014
- SQL Server 2016
- SQL Server, 2017 in Windows e Linux
- Azure SQL Database

> [!NOTE] 
> DMA non supporta attualmente istanza gestita di Azure SQL Database come destinazione.

## <a name="installation"></a>Installazione

Per installare DMA, scaricare la versione più recente dello strumento dal [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53595), quindi eseguire il **DataMigrationAssistant.msi** file.

## <a name="see-also"></a>Vedere anche

[Valutare la migrazione a SQL Server](../dma/dma-assesssqlonprem.md)

[Dati Migration Assistant: Le impostazioni di configurazione](../dma/dma-configurationsettings.md)

[Migrazione On-Premise SQL Server utilizzando dati Migration Assistant](../dma/dma-migrateonpremsql.md)

[Dati Migration Assistant: Procedure consigliate](../dma/dma-bestpractices.md)



