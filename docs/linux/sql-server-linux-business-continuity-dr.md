---
title: Ripristino di emergenza di SQL Server in Linux | Documenti Microsoft
description: 
author: mihaelab
ms.author: mihaelab
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: c75717c8-c677-4033-8ca6-d0ac93aee04d
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 86f41971e06efb767dde336cf93f9224a204176d
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="business-continuity-and-database-recovery-sql-server-on-linux"></a>Continuità aziendale e database di ripristino SQL Server in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

SQL Server in Linux consente alle organizzazioni di raggiungere una vasta gamma di obiettivi di contratto di servizio per soddisfare i requisiti aziendali diversi.

Le soluzioni più semplice di sfruttare le tecnologie di virtualizzazione per ottenere un elevato livello di resilienza agli errori a livello di host, la tolleranza di errore da errori hardware, nonché l'elasticità e Massimizzazione delle risorse. Questi sistemi è possono eseguire in locale, in un cloud pubblico o privato o in ambienti ibridi. La forma più semplice di protezione e ripristino di emergenza è il backup del database. Semplice soluzioni disponibili in SQL Server 2017 RC2 includono:

- **Failover della macchina virtuale**
    - Resilienza per gli errori a livello del sistema operativo e di guest
    - Eventi pianificati e non pianificati
    - Tempo di inattività minimo per l'applicazione di patch e aggiornamenti
    - RTO in minuti


- [**Ripristino e backup del database**](sql-server-linux-backup-and-restore-database.md) 
    - Protezione contro il danneggiamento dei dati accidentali o intenzionali
    - Protezione con ripristino di emergenza
    - RTO in minuti, ore

Tecniche di ripristino di emergenza e disponibilità elevata standard offrono una protezione a livello di istanza combinata con un'infrastruttura affidabile archiviazione condivisa. Per SQL Server 2017 RC2 standard a disponibilità elevata include:

- [**Cluster di failover**](sql-server-linux-shared-disk-cluster-configure.md)
    - Protezione a livello di istanza
    - Failover e il rilevamento automatico di errore
    - Resilienza in caso di errori del sistema operativo e SQL Server
    - RTO in secondi a minuti


## <a name="summary"></a>Riepilogo

SQL Server 2017 RC2 in Linux include i cluster di virtualizzazione, backup e ripristino e il failover per il supporto a disponibilità elevata e ripristino di emergenza. 
