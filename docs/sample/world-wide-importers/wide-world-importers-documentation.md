---
title: Documentazione di Wide World Importers | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: samples
ms.technology: samples
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17cabd9d-cb2f-436c-ad9c-ce02225808b7
caps.latest.revision: "3"
author: BarbKess
ms.author: barbkess
manager: jhubbard
robots: noindex,nofollow
ms.workload: On Demand
ms.openlocfilehash: a2510ee889f57f7ab51c0f45574a8fa6e86abb47
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="wide-world-importers-documentation"></a>Documentazione di Wide World Importers
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Wide World Importers è il nuovo database di esempio per SQL Server 2016 e Database SQL di Azure. Illustra le funzionalità principali di SQL Server 2016 e Database SQL di Azure per l'elaborazione delle transazioni (OLTP), data warehouse e carichi di lavoro analitica (OLAP), nonché ibrida transaction e carichi di elaborazione (HTAP) analitica.

## <a name="about-this-sample"></a>Su questo esempio

Wide World Importers è un esempio di database completo che illustra la progettazione del database e viene illustrato come è possono sfruttare le funzionalità di SQL Server in un'applicazione.

Si noti che l'esempio deve essere rappresentativo di un tipico database. Non include tutte le funzionalità di SQL Server. La progettazione del database segue un set comune di standard, ma esistono diversi modi uno potrebbe creare un database.

**Versione più recente**: [wide-world importers release](http://go.microsoft.com/fwlink/?LinkID=800630)

**Codice sorgente per l'esempio**: [wide mondo](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers).

**Commenti e suggerimenti**: Invia a [ sqlserversamples@microsoft.com ](mailto:sqlserversamples@microsoft.com).

La documentazione per l'esempio è organizzata come segue:

## <a name="overview"></a>Panoramica

Panoramica della società di esempio Wide World Importers e i flussi di lavoro risolti dall'esempio.

## <a name="main-oltp-database-wideworldimporters"></a>WideWorldImporters Database OLTP principale

Istruzioni per l'installazione e configurazione di base del database WideWorldImporters che viene utilizzato per l'elaborazione delle transazioni (OLTP, OnLine Transaction Processing) e operativo analitica (HTAP - l'elaborazione transazionale/analitica ibrida).

Descrizione degli schemi e le tabelle utilizzate nel database WideWorldImporters.  

Viene descritto come WideWorldImporters sfrutta le funzionalità di SQL Server core.

Query di esempio per il database WideWorldImporters.

## <a name="data-warehousing-and-analytics-database-wideworldimportersdw"></a>Data Warehousing e Analitica Database WideWorldImportersDW

Istruzioni per l'installazione e configurazione di OLAP WideWorldImportersDW del database.

Descrizione degli schemi e le tabelle utilizzate nel database WideWorldImportersDW, ovvero il database di esempio per il data warehousing e l'elaborazione analitica (OLAP).

Flusso di lavoro per il processo ETL (Extract, Transform, Load) che esegue la migrazione di dati dal database transazionale WideWorldImporters nel data warehouse WideWorldImportersDW.

Viene descritto come il WideWorldImportersDW sfrutta le funzionalità di SQL Server per l'elaborazione analitica.

Query di esempio analitica sfruttando il database WideWorldImportersDW.

## <a name="data-generation"></a>Generazione di dati

Viene descritto come altri dati possono essere generati nel database di esempio, inserire, ad esempio vendite e acquistare dati fino alla data corrente.
