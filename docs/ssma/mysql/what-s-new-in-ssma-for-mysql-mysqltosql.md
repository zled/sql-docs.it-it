---
title: "Novità &#39; s di SSMA per MySQL (MySQLToSql) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 08/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 1451a0b0-6713-4d0c-954f-ea3d8fce1d31
caps.latest.revision: 21
author: sabotta
ms.author: carlasab
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 80642503480add90fc75573338760ab86139694c
ms.openlocfilehash: 6dff8473750c454984d824eee17abb9358ce18fe
ms.contentlocale: it-it
ms.lasthandoff: 08/21/2017

---
# <a name="what39s-new-in-ssma-for-mysql-mysqltosql"></a>Novità &#39; s di SSMA per MySQL (MySQLToSql)
Questo argomento elenca SSMA per le modifiche di MySQL in ogni versione. 

## <a name="ssma-v74"></a>SSMA v7.4
La versione v7.4 di SSMA per MySQL contiene le seguenti modifiche:
- Il **timeout Query** l'opzione è disponibile durante l'individuazione di oggetti dello schema all'origine e di destinazione.
![valore di timeout query](../media/query-timeout_red.png)
- La metrica della qualità e la conversione è stata migliorata con le correzioni di destinazione, in base ai suggerimenti dei clienti.

> [!IMPORTANT]
> .NET 4.5.2 è un prerequisito per l'installazione di SSMA v7.4. Inoltre, a partire da v7.4, la versione a 32 bit di SSMA è stata sospesa. 

## <a name="ssma-v73"></a>SSMA v7.3
La versione v7.3 di SSMA per MySQL contiene le seguenti modifiche:
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
La versione a versione 7.2 di SSMA per MySQL contiene le seguenti modifiche:
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
La versione di maggio 2016 di SSMA per MySQL contiene le seguenti modifiche:.

-  Aggiunta del supporto per SQL Server 2016.
-  Resolver e il parser migliorate.
-  Rimuovere il controllo di programma di installazione per .net 2.0.
-  Aggiornato estensione dipendenza del Pack da .net 3.5 per .net 4.0.
-  Predefinito fisso BigInt typemapping per MySql.
-  Fisso "Salva"progetto "progetto aperto" comandi e per la Console di SSMA.
-  Comando predefinito "securepassword" per la Console di SSMA.
-  Fissa il conteggio di oggetti per il caricamento iniziale.
-  Il caricamento di oggetti MsSql fissi.
-  Correzione del bug nelle impostazioni globali.
 
## <a name="march-2016"></a>Marzo 2016  
La versione di anteprima di marzo 2016 di SSMA per MySQL contiene le seguenti modifiche:  
  
-  Aggiunta del supporto per la migrazione a SQL Server 2016. 
  
## <a name="january-2016"></a>Gennaio 2016  
La versione di gennaio 2016 manutenzione di SSMA per MySQL contiene le seguenti modifiche:  
  
-  Aggiunta Log menu Visualizza per SSMA (RFC 5706203).  
-  Aggiunta di telemetria.  
  
## <a name="july-2014"></a>Luglio 2014  
La versione di luglio 2014 di SSMA per MySQL contiene le seguenti modifiche:  
  
-  Conversione del codice di database SQL di Azure migliorata. 
-  Funzionalità di estensione pack spostato nello schema per il supporto di database SQL di Azure.  
-  Miglioramenti delle prestazioni testato per i database con più di 10k oggetti.  
-  Miglioramenti dell'interfaccia utente per la gestione con un numero elevato di oggetti.  
-  Evidenziazione degli schemi LOB "noti" (in modo che può essere ignorati nella conversione).  
-  Miglioramenti di velocità di conversione.  
-  Mostra conteggi oggetti nell'interfaccia utente.  
-  Riduzione delle dimensioni di report più del 25%.  
-  Messaggi di errore migliorati per i costrutti non analizzati.  
  
## <a name="april-2014"></a>Aprile 2014  
La versione di luglio 2011 di SSMA per MySQL contiene le seguenti modifiche:  
  
-  Aggiunta del supporto di Microsoft SQL Server 2014.  
-  Bug risolti sulla conversione in Azure  
-  Bug risolti per le pagine del report invisibile in Internet Explorer 10.  
  
## <a name="july-2011"></a>Luglio 2011  
La versione di luglio 2011 di SSMA per MySQL contiene le seguenti modifiche:  
  
-   Supporto per la conversione del limite per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] OFFSET "Denali".  
-   Una migliore segnalazione errori durante la migrazione dei dati.  
  
## <a name="april-2011"></a>Aprile 2011  
La versione di aprile 2011 di SSMA per MySQL contiene le seguenti modifiche:  
  
-   Singolo Installable di "SSMA per MySQL", che supporta [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali" e SQL Azure.  
-   La possibilità di connettersi [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali".  
-   Modulo di migrazione avanzata dei dati sul lato client, che supporta la migrazione parallela dei dati.  
-   Prestazioni migrazione di dati migliorate con semplici e di massa registrato i modelli di recupero.  
-   SSMA per MySQL Console versione supporta la compatibilità con le versioni precedenti. È possibile aprire i progetti creati con versioni precedenti a v 5.0 SSMA.  
-   SSMA per MySQL v 5.0 prodotto può essere installato affiancata (SxS) con le versioni precedenti del prodotto SSMA.  
  
## <a name="july-2010"></a>Luglio 2010  
La versione di luglio 2010 di SSMA per MySQL contiene le seguenti funzionalità:  
  
1.  **Miglioramenti all'interfaccia utente:**  
  
    -   Scheda 'Modalità di SQL' per gli oggetti di MySQL Database  
    -   Scheda 'Impostazioni' per gli oggetti di MySQL Database  
    -   Scheda 'Data' per le tabelle di MySQL  
    -   Impostazioni di progetto aggiornato nelle pagine di migrazione e di conversione  
    -   'Impostazioni di migrazione di dati' a livello di tabella  
  
2.  **Miglioramenti per la connessione a MySQL e SQL Server:**  
  
    -   Connettività SSL di MySQL  
    -   Connettività crittografata in SQL Server  
  
3.  **Miglioramenti alla Metabase MySQL Explorer:**  
  
    -   Durante il caricamento di tutti gli oggetti di Database MySQL e le rispettive schede.  
  
4.  **Miglioramenti per la conversione degli oggetti:**  
  
    -   Conversione di oggetti della Metabase di MySQL: procedure, funzioni, viste, trigger e le istruzioni.  
    -   Supporto limitato per i tipi di dati spaziali nelle tabelle.  
    -   Opzione per convertire le funzioni di MySQL in Stored procedure di SQL Server  
    -   Opzione per applicare il mapping di modalità di SQL e set di caratteri durante la conversione degli oggetti  
  
5.  **Miglioramenti alla migrazione dei dati:**  
  
    -   Supporto per la migrazione dei dati tramite motori di migrazione dei dati sul lato Client e lato Server  
    -   Supporto per la migrazione di dati spaziali  
    -   SQL personalizzata per la migrazione dei dati per le tabelle  
  
6.  **SSMA per la Console di MySQL:**  
  
    -   Supporto di funzionalità della Console per SSMA per MySQL  
    -   Supporto per l'interfaccia a livello di Script  
  
## <a name="january-2010"></a>Gennaio 2010  
La versione di gennaio 2010 di SSMA per MySQL è la versione iniziale. Contiene le seguenti funzionalità:  
  
-   Aggiunta del supporto per la migrazione sia locale di SQL Server e SQL Azure.  
  
-   **Funzionalità Snapshot:** migrazione di schemi e dati di tabelle/indici o vincoli di MySQL.
