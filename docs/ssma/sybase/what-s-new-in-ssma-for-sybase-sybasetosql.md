---
title: "Novità &#39; s di SSMA per Sybase (SybaseToSQL) | Documenti Microsoft"
ms.custom: 
ms.date: 08/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 2be0cf8d-6dbe-443a-abbd-036249922205
caps.latest.revision: 21
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 80642503480add90fc75573338760ab86139694c
ms.openlocfilehash: 1054c9279039eda01320e1afd9745b6a53200b3f
ms.contentlocale: it-it
ms.lasthandoff: 08/21/2017

---
# <a name="what39s-new-in-ssma--for-sybase-sybasetosql"></a>Novità &#39; s di SSMA per Sybase (SybaseToSQL)
In questo argomento vengono elencati SSMA per Sybase modifiche in ogni versione. 

## <a name="ssma-v74"></a>SSMA v7.4
La versione v7.4 di SSMA per Sybase contiene le seguenti modifiche:
- Il **timeout Query** l'opzione è disponibile durante l'individuazione di oggetti dello schema all'origine e di destinazione.
![valore di timeout query](../media/query-timeout_red.png)
- La metrica della qualità e la conversione è stata migliorata con le correzioni di destinazione, in base ai suggerimenti dei clienti.

> [!IMPORTANT]
> .NET 4.5.2 è un prerequisito per l'installazione di SSMA v7.4. Inoltre, a partire da v7.4, la versione a 32 bit di SSMA è stata sospesa.  

## <a name="ssma-v73"></a>SSMA v7.3
La versione v7.3 di SSMA per Sybase contiene le seguenti modifiche:
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
La versione a versione 7.2 di SSMA per Sybase contiene le seguenti modifiche:
- Metrica qualità e la conversione migliorata con le correzioni di destinazione in base ai suggerimenti dei clienti.
- Miglioramenti di telemetria per fornire una migliore punti dati per risolvere i problemi dei clienti e migliorare il tasso di conversione di SSMA.

## <a name="ssma-v71"></a>V 7.1 SSMA
La versione v 7.1 di SSMA per l'accesso contiene le seguenti modifiche:
- 2017 di SQL Server in Windows e Linux CTP1 è una piattaforma di destinazione supportate per la migrazione. Questa funzionalità è disponibile in anteprima tecnica e supporta lo spostamento di dati e lo schema a server SQL di destinazione.
- SSMA supporta ora gli aggiornamenti automatici per scaricare la versione più recente di SSMA è disponibile.
- I file binari installabili SSMA ora vengono recapitati tramite file di pacchetto di Windows installer (MSI).

**Risorse**

[Estensione delle funzionalità di SQL Server Migration Assistant conversione](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)

[Valutare e migrare i dati da piattaforme di dati non Microsoft per SQL Server *(con un esempio di Oracle)*](https://blogs.msdn.microsoft.com/datamigration/2016/11/16/sql-server-migration-assistant-how-to-assess-and-migrate-databases-from-non-microsoft-data-platforms-to-sql-server/) 

## <a name="may-2016"></a>Maggio 2016  
La versione di maggio 2016 di SSMA per Sybase contiene le seguenti modifiche:  

-  Aggiunta del supporto per SQL Server 2016.
-  Rimuovere il controllo di programma di installazione per .net 2.0.
-  Aggiornato estensione dipendenza del Pack da .net 3.5 per .net 4.0.
-  Fisso "Salva"progetto "progetto aperto" comandi e per la Console di SSMA.
-  Comando predefinito "securepassword" per la Console di SSMA.
-  Fissa il conteggio di oggetti per il caricamento iniziale.
-  Correzione del bug nelle impostazioni globali.

## <a name="march-2016"></a>Marzo 2016  
La versione di anteprima di marzo 2016 di SSMA per Sybase contiene le seguenti modifiche:  
  
-  Aggiunta del supporto per la migrazione a SQL Server 2016.  
  
## <a name="january-2016"></a>Gennaio 2016  
La versione di gennaio 2016 manutenzione di SSMA per Sybase contiene le seguenti modifiche:  
  
-  Aggiunta Log menu Visualizza per SSMA (RFC 5706203).  
-  Aggiunta di telemetria. 
  
## <a name="july-2014"></a>Luglio 2014  
La versione di luglio 2014 di SSMA per Sybase contiene le seguenti modifiche:  
  
-  Conversione del codice di database SQL di Azure migliorata.  
-  Spostare la funzionalità di estensione pack allo schema per supportare i database SQL di Azure.  
-  Miglioramenti delle prestazioni aggiunti testato per i database con più di 10k oggetti.  
-  Aggiunti miglioramenti dell'interfaccia utente per la gestione con un numero elevato di oggetti.  
-  Aggiunta la possibilità di selezionare gli schemi LOB "noti" (in modo che può essere ignorati nella conversione).  
-  Aggiunti miglioramenti di velocità di conversione.  
-  Aggiunta la possibilità di visualizzare il numero di oggetti nell'interfaccia utente. 
-  Dimensioni del report ridotta da più di 25%.  
-  Messaggi di errore migliorati per i costrutti non analizzati.  
  
## <a name="april-2014"></a>Aprile 2014  
La versione di aprile 2014 di SSMA per Sybase contiene le seguenti modifiche:  
  
-   Aggiunta del supporto di Microsoft SQL Server 2014.  
-   Bug risolti sulla conversione in Azure.  
-   Bug risolti per le pagine del report invisibile in Internet Explorer 10.  
  
## <a name="january-2012"></a>Gennaio 2012  
La versione di gennaio 2012 di SSMA per Sybase contiene le seguenti modifiche:  
  
-   Aggiunta del supporto per la conversione di trigger di rollback.  
-   Fornito di correzione per la conversione@ROWCOUNT e @@ERROR nella stessa istruzione SET.  
  
## <a name="july-2011"></a>Luglio 2011  
La versione di luglio 2011 di SSMA per Sybase contiene le seguenti modifiche:  
  
-   Una migliore segnalazione errori durante la migrazione dei dati.  
  
## <a name="april-2011"></a>Aprile 2011  
La versione di aprile 2011 di SSMA per Sybase contiene le seguenti modifiche:  
  
-   Singolo prodotto "SSMA per Sybase", che supporta [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali" e SQL Azure.  
-   Aggiunto il supporto per la connessione e la migrazione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali".  
-   Aggiungere una nuova funzionalità per convertire e la migrazione dei database di Sybase a SQL Azure.  
-   Modulo di migrazione avanzata dei dati sul lato client, che supporta la migrazione parallela dei dati.  
-   Prestazioni migrazione di dati migliorate con semplici e di massa registrato i modelli di recupero.  
-   Aggiunta la possibilità di convertire correttamente e migrazione dei database di Sybase distinzione tra maiuscole e minuscole di SQL Server.  
-   Aggiunta del supporto per la conversione di istruzioni join Sybase ASE Non ANSI istruzioni join ANSI di SQL Server è stato esteso per eliminare e aggiornare le istruzioni.  
-   Fornite opzioni di connettività aggiuntivo per la connessione al server di Sybase ASE utilizzando provider Sybase ASE ODBC e provider Sybase ASE ADO.Net.  
-   Rimuovere la dipendenza da un database separato denominato **SysDB**, che contiene le funzioni di emulazione di Sybase (installate come parte del pacchetto di estensione).  
-   Aggiunta la possibilità di installare SSMA per Sybase estensione Pack [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] cluster.  
-   Aggiunta di compatibilità con le versioni precedenti dei progetti creati con versioni precedenti di SSMA (v 4.0 e v 4.2).  
-   Aggiunta la possibilità di installare SSMA per Sybase v 5.0 prodotti side-by-side (SxS) con le versioni precedenti di SSMA (v 4.0 e v 4.2).  
  
## <a name="july-2010"></a>Luglio 2010  
La versione di luglio 2010 di SSMA per Sybase contiene le seguenti modifiche:  
  
-   Aggiunta del supporto per la migrazione a SQL Server 2008 R2.  
-   Aggiungere una nuova applicazione Console di SSMA per l'esecuzione della riga di comando.  
-   Aggiunta del supporto per la migrazione dei dati tramite motori di migrazione dei dati sul lato Client e lato Server.  
-   Aggiunta del supporto per l'istruzione "SELECT personalizzata" nella migrazione dei dati.  
-   Aggiunta del supporto per la migrazione da Sybase ASE 15.0.3 e 15,5.  
  
## <a name="june-2008"></a>Giugno 2008  
La versione di giugno 2008 di SSMA per Sybase contiene le seguenti modifiche:  
  
-   Aggiunta SSMA Tester, che consente di verificare automaticamente la conversione di oggetti di database e la migrazione dei dati apportate da SSMA. Al termine di tutti i passaggi di migrazione di SSMA, è possibile utilizzare il Tester di SSMA per verificare che gli oggetti convertiti funzionano nello stesso modo e che tutti i dati è stato trasferito correttamente.  
-   Conversione di versioni precedenti a SQL aggiuntiva. Utente ora può specificare la tabella temporanea (e altri oggetti) le dichiarazioni per ogni procedura di origine da utilizzare nella conversione.  
-   Aggiunti miglioramenti per la conversione di oggetti:  
    -   Crea un join conversione rivista.  
    -   Funzioni di aggregazione e non aggregati senza con/Raggruppa clausole.  
    -   La funzione IDENTITY con un'istruzione SELECT INTO.  
    -   Indici in dati solo bloccato e dei vincoli cluster.  
    -   Tabelle temporanee create da SELECT INTO.  
    -   Vincoli / indici per le tabelle temporanee.  
    -   Nuovo [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 datetime sono supportati.  
    -   Supporto di tipi di dati e la connettività 15.0 Sybase.  
  
## <a name="may-2007"></a>Maggio 2007  
La versione di maggio 2007 di SSMA per Sybase contiene le seguenti modifiche:  
  
-   Aggiunta la possibilità di caricare più velocemente del contenuto del database durante il salvataggio di un progetto.  
-   Aggiunta del supporto per i commenti immessi dall'utente in SQL Server in formato modalità SQL.  
-   Aggiunti miglioramenti per la conversione di oggetti.  
  
Il file della Guida non è stato aggiornato per questa versione. Per ulteriori informazioni, vedere la sezione Note relative alla documentazione più avanti in questo argomento.  
  
## <a name="november-2006"></a>Novembre 2006  
La versione di novembre 2006 di SSMA per Sybase contiene le seguenti modifiche:  
  
-   Aggiunte nuove impostazioni globali:  
    -   È possibile scegliere di visualizzare i numeri di riga nelle finestre dell'editor.  
    -   È possibile configurare SSMA per la richiesta di sostituire gli oggetti duplicati o sempre o mai sostituire oggetti duplicati durante la conversione dello schema.  
-   Aggiunta una nuova opzione di conversione che consente di configurare la modalità SSMA gestisce inoltre le situazioni seguenti:  
    -   Un'istruzione CAST o CONVERT che contiene una stringa binaria.  
    -   Verifica dei valori null nelle espressioni di uguaglianza.  
    -   Tabelle di proxy.  
    -   Numeri di errore messaggio utente per RAISERROR.  
    -   AGGIORNARE le istruzioni che contengono gli identificatori non risolti.  
-   Aggiunta una nuova opzione di migrazione che consente di specificare la modalità SSMA deve gestire le date che si trovano all'esterno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] intervallo di date.  
-   Aggiunto un **formattato SQL** impostazione di **SQL** scheda, che formatta il codice per una migliore leggibilità.  
-   Correzioni di bug che includono quanto segue:  
    -   SSMA è ora possibile convertita la tabella blocco *tabella* IN {SHARED | Istruzioni in modalità esclusiva} aggiungendo un hint TABLOCK o TABLOCKX per la query SELECT successive sulla tabella.  
    -   I cast necessari vengono aggiunti a questo punto quando tipi binari utilizzati nelle espressioni di caratteri.  
    -   Memoria e miglioramenti delle prestazioni.  
  
## <a name="july-2006"></a>Luglio 2006  
La versione di SSMA per Sybase di luglio 2006 costituisce la versione iniziale.  
  
## <a name="see-also"></a>Vedere anche  
[Introduzione a SSMA per Sybase &#40; SybaseToSQL &#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)
