---
title: Panoramica di Data Migration Assistant (SQL Server) | Microsoft Docs
description: Informazioni su come usare Data Migration Assistant per eseguire la migrazione di database di SQL Server ad altri Server SQL o i database di Azure
ms.custom: ''
ms.date: 08/29/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, overview
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: fbf3441d82f2de405e1a227821834b3943db3285
ms.sourcegitcommit: fb269accc3786715c78f8b6e2ec38783a6eb63e9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/29/2018
ms.locfileid: "43152692"
---
# <a name="overview-of-data-migration-assistant"></a>Panoramica di Data Migration Assistant

La Data Migration Assistant (DMA) consente di eseguire l'aggiornamento a una piattaforma dati moderna individuando i problemi di compatibilità che possono influire sulla funzionalità del database nella nuova versione di SQL Server o del Database SQL di Azure. DMA consiglia miglioramenti di prestazioni e affidabilità per l'ambiente di destinazione e consente di spostare lo schema, dati e gli oggetti non contenuti dal server di origine al server di destinazione.

> [!NOTE] 
> Migrazioni di grandi dimensioni (in termini di numero e dimensioni dei database), è consigliabile usare la [Azure Database Migration Service](https://docs.microsoft.com/azure/dms/dms-overview), che può eseguire la migrazione di database su larga scala.
  
## <a name="capabilities"></a>Capabilities

- Consente di valutare le istanze di SQL Server in locale la migrazione a uno o più database SQL di Azure. Il flusso di lavoro di valutazione ti aiuta a rilevare i problemi che possono influire sulla migrazione del database SQL di Azure e fornisce indicazioni dettagliate su come risolverli.

  - Problemi di blocco della migrazione: consente di individuare i problemi di compatibilità che blocca la migrazione di SQL Server locale database s per i database SQL di Azure. DMA fornisce indicazioni che consentono di risolvere tali problemi.

  - Parzialmente supportate o funzionalità non supportate: rileva le funzionalità parzialmente supportate o non supportate che sono attualmente in uso nell'istanza di SQL Server di origine. DMA offre che un set completo di indicazioni, approcci alternativi disponibili in Azure e le procedure di mitigazione in modo che è possibile incorporare nei progetti di migrazione.

- Individuare i problemi che possono influire sull'aggiornamento a SQL Server in locale. Queste sono descritte come problemi di compatibilità e sono organizzate nelle categorie seguenti:

  - Modifiche di rilievo
  - Modifiche del comportamento
  - Funzionalità deprecate

- Individua le nuove funzionalità alla piattaforma di SQL Server di destinazione che il database può trarre vantaggio dalla dopo un aggiornamento. Queste sono descritti i consigli corrispondenti a funzionalità e sono organizzate nelle categorie seguenti:

  - restazioni
  - Security
  - Archiviazione

- Eseguire la migrazione di un'istanza di SQL Server locale a un'istanza di SQL Server moderna, ospitata in locale o in una macchina virtuale di Azure (VM) che è accessibile dalla rete locale. Macchina virtuale di Azure è accessibile tramite VPN o altre tecnologie. Il flusso di lavoro di migrazione consente di eseguire la migrazione i componenti seguenti:

  - Schema di database
  - I dati e gli utenti
  - Ruoli del server
  - Account di accesso di SQL Server e Windows

- Dopo la migrazione ha esito positivo, le applicazioni possono connettersi senza problemi per i database SQL server di destinazione.

## <a name="supported-source-and-target-versions"></a>Versioni supportate di origine e destinazione

DMA sostituisce tutte le versioni precedenti di preparazione aggiornamento di SQL Server e debba essere usato per gli aggiornamenti per la maggior parte delle versioni di SQL Server. Seguono le versioni supportate di origine e di destinazione.

**Origini**
- SQL Server 2005
- SQL Server 2008
- SQL Server 2008 R2
- SQL Server 2012 
- SQL Server 2014
- SQL Server 2016
- SQL Server 2017 in Windows

**Destinazioni**
- SQL Server 2012
- SQL Server 2014
- SQL Server 2016
- SQL Server 2017 in Windows e Linux
- Database SQL di Azure

> [!NOTE] 
> DMA non supporta attualmente istanza gestita di Azure SQL Database come destinazione.

## <a name="installation"></a>Installazione

Per installare DMA, scaricare la versione più recente dello strumento dal [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53595), quindi eseguire il **DataMigrationAssistant.msi** file.

## <a name="see-also"></a>Vedere anche

[Valutare la migrazione di SQL Server](../dma/dma-assesssqlonprem.md)

[Data Migration Assistant: Le impostazioni di configurazione](../dma/dma-configurationsettings.md)

[Eseguire la migrazione On-Premises SQL Server tramite Data Migration Assistant](../dma/dma-migrateonpremsql.md)

[Data Migration Assistant: Procedure consigliate](../dma/dma-bestpractices.md)



