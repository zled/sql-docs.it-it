---
title: Novità di SSMA per DB2 (DB2ToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 03/01/2018
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 1cc38f85-3caa-42d0-8c76-a380c1d15c67
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ddfcf888930c5667d815783d3a0c7052b7c11c0a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="whats-new-in-ssma-for-db2-db2tosql"></a>Novità di SSMA per DB2 (DB2ToSQL)
Questo argomento elenca SSMA per le modifiche di DB2 in ogni versione.  

## <a name="ssma-v77"></a>SSMA v7.7
La versione v7.7 di SSMA per DB2 contiene le seguenti modifiche:
- SSMA per DB2 è stata migliorata con le correzioni di destinazione che consentono di migliorare le metriche di qualità e la conversione.
- In base a grande richiesta, la versione a 32 bit di SSMA per DB2 è nuovo. Se confrontato con l'implementazione precedente (prima v7.4), sono disponibili due pacchetti di installazione, ma non possono essere installati side-by-side. Di conseguenza, è necessario scegliere la versione più appropriata in base ai componenti di connettività che è. È sempre preferibile usare la versione a 64 bit, se possibile.

> [!IMPORTANT]
> Con SSMA v7.4 e versioni successive, .net 4.5.2 è un prerequisito di installazione.

## <a name="ssma-v76"></a>SSMA v7.6
La versione v7.6 di SSMA per DB2 è stata migliorata con le correzioni di destinazione che consentono di migliorare le metriche di qualità e la conversione e con il supporto per SQL Server 2017 (anteprima pubblica). Supporto per SQL Server 2017 in Windows e Linux è disponibile in anteprima pubblica e non deve essere utilizzato per le migrazioni di produzione.

> [!IMPORTANT]
> Con SSMA v7.4 e versioni successive, .net 4.5.2 è un prerequisito di installazione e la versione a 32 bit dello strumento è stata interrotta.

## <a name="ssma-v75"></a>SSMA v7.5
La versione v7.5 di SSMA per DB2 è stata migliorata con numerosi miglioramenti per garantire maggiore accessibilità per persone affette da disabilità.

> [!IMPORTANT]
> .NET 4.5.2 è un prerequisito per l'installazione di SSMA v7.5. Inoltre, a partire da v7.4, la versione a 32 bit di SSMA è stata sospesa.

## <a name="ssma-v74"></a>SSMA v7.4
La versione v7.4 di SSMA per DB2 contiene le seguenti modifiche:
- Il **timeout Query** l'opzione è disponibile durante l'individuazione di oggetti dello schema all'origine e di destinazione.
![valore di timeout query](../media/query-timeout_red.png)

- La metrica della qualità e la conversione è stata migliorata con le correzioni di destinazione, in base ai suggerimenti dei clienti.

> [!IMPORTANT]
> .NET 4.5.2 è un prerequisito per l'installazione di SSMA v7.4. Inoltre, a partire da v7.4, la versione a 32 bit di SSMA è stata sospesa.

## <a name="ssma-v73"></a>SSMA v7.3
La versione v7.3 di SSMA per DB2 contiene le seguenti modifiche:
- Metrica qualità e la conversione migliorata con le correzioni di destinazione in base ai suggerimenti dei clienti.
- Framework di estendibilità SSMA esposta tramite gli elementi seguenti:
  - La funzionalità di esportazione per un progetto di SQL Server Data Tools (SSDT).
    -   È ora possibile esportare script dello schema da SSMA a un progetto SSDT. È possibile utilizzare gli script di schema per apportare ulteriori modifiche dello schema e distribuire il database.
![Comando progetto SSDT Salva con nome](../media/export-schema-scripts_red.png)
  - Librerie che possono essere utilizzate da SSMA per l'esecuzione di conversioni personalizzate.
    - È ora possibile creare codice in grado di gestire le conversioni di sintassi personalizzata e che non sono stati precedentemente gestite dal SSMA.
      - Le istruzioni su come costruire un convertitore personalizzato sono disponibili in questo post di blog [funzionalità di conversione della estensione SQL Server Migration Assistant](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/).
      - Progetto di esempio per la conversione possibile scaricare questo [post di blog](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/).

## <a name="ssma-v72"></a>Versione 7.2 SSMA
La versione a versione 7.2 di SSMA per DB2 contiene le seguenti modifiche:
- Metrica qualità e la conversione migliorata con le correzioni di destinazione in base ai suggerimenti dei clienti.
- Miglioramenti di telemetria per fornire una migliore punti dati per risolvere i problemi dei clienti e migliorare il tasso di conversione di SSMA.

## <a name="ssma-v71"></a>V 7.1 SSMA
La versione v 7.1 di SSMA per l'accesso contiene le seguenti modifiche:
- 2017 di SQL Server in Windows e Linux CTP1 è una piattaforma di destinazione supportate per la migrazione. Questa funzionalità è disponibile in anteprima tecnica e consente lo spostamento di dati e lo schema per i server SQL di destinazione.
- SSMA supporta ora gli aggiornamenti automatici per scaricare la versione più recente di SSMA è disponibile.
- I file binari installabili SSMA ora vengono recapitati tramite file di pacchetto di Windows installer (MSI).

**Risorse**

[Estensione delle funzionalità di SQL Server Migration Assistant conversione](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)

[Valutare e migrare i dati da piattaforme di dati non Microsoft per SQL Server *(con un esempio di Oracle)*](https://blogs.msdn.microsoft.com/datamigration/2016/11/16/sql-server-migration-assistant-how-to-assess-and-migrate-databases-from-non-microsoft-data-platforms-to-sql-server/) 

## <a name="may-2016"></a>Maggio 2016  
La versione di maggio 2016 di SSMA per DB2 contiene le seguenti modifiche:  

-  Aggiunta del supporto per SQL Server 2016.
-  Aggiunta conversione delle tabelle in memoria e regolare di DB2 alle funzionalità di SQL Server in-memory e hekaton.
-  Conversione aggiunta di controlli di accesso DB2 agli oggetti Criteri di SQL Server (protezione di livello di riga per DB2).
-  Aggiunta conversione delle tabelle con controllo delle versioni del sistema DB2 su tabelle temporali di SQL Server.
-  Parser di DB2 e resolver migliorati.
-  Rimuovere il controllo di programma di installazione per .net 2.0.
-  Rimosso *. dll non necessari dal programma di installazione di Db2.
-  Fisso "Salva"progetto "progetto aperto" comandi e per la Console di SSMA.
-  Comando predefinito "securepassword" per la Console di SSMA.
-  Fissa il conteggio di oggetti per il caricamento iniziale.
-  Correzione del bug nelle impostazioni globali.
  
## <a name="march-2016"></a>Marzo 2016  
La versione di anteprima di marzo 2016 di SSMA per DB2 contiene le seguenti modifiche:  
  
-  Aggiunta del supporto per la migrazione a SQL Server 2016.  
  
## <a name="january-2016"></a>Gennaio 2016  
La versione di gennaio 2016 manutenzione di SSMA per DB2 contiene le seguenti modifiche:  
  
-  Aggiunta del supporto per il numero di funzioni standard.  
-  Correzione di errori del Parser di DB2.  
-  ZOS di v9 DB2 predefinito supporto (RFC 5690920).  
-  Errori di identificatore non risolti da DB2 predefinito durante la conversione.  
-  Aggiunta Log menu Visualizza per SSMA (RFC 5706203).  
-  Aggiunta di telemetria.
  
## <a name="november-2014"></a>Novembre 2014  
La versione di novembre 2014 di SSMA per DB2 è la versione iniziale.
