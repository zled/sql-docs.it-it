---
title: Pianificare e testare il piano di aggiornamento del motore di database | Microsoft Docs
ms.custom: 
ms.date: 07/20/2016
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19c5b725-7400-4881-af8f-fd232ca28234
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: cbe7bceca06dd5eef19b56433a8054c20d2e88d2
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="plan-and-test-the-database-engine-upgrade-plan"></a>Pianificare e testare il piano di aggiornamento del motore di database
  Per eseguire correttamente l'aggiornamento di [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] , indipendentemente dall'approccio, è opportuna un'accurata pianificazione.  
  
## <a name="release-notes-and-known-upgrade-issues"></a>Note sulla versione e problemi di aggiornamento noti  
 Prima di aggiornare il [!INCLUDE[ssDE](../../includes/ssde-md.md)], vedere:

- [Note sulla versione di SQL Server 2017](../../sql-server/sql-server-2017-release-notes.md) 
- [Note sulla versione di SQL Server 2016](../../sql-server/sql-server-2016-release-notes.md) 
- Argomento [Compatibilità con le versioni precedenti del motore di database di SQL Server](../../database-engine/sql-server-database-engine-backward-compatibility.md).  
  
## <a name="pre-upgrade-planning-checklist"></a>Elenco di controllo per la pianificazione pre-aggiornamento  
 Prima di aggiornare [!INCLUDE[ssDE](../../includes/ssde-md.md)], consultare il seguente elenco di controllo e gli argomenti correlati. Questi argomenti si applicano a tutti gli aggiornamenti, indipendentemente dal metodo di aggiornamento, e consentono di determinare il metodo di aggiornamento più appropriato: aggiornamento in sequenza, nuovo aggiornamento dell'installazione o aggiornamento sul posto. Ad esempio, potrebbe non essere possibile eseguire un aggiornamento in sequenza o sul posto se si esegue l'aggiornamento del sistema operativo, l'aggiornamento da SQL Server 2005 o l'aggiornamento da una versione a 32 bit di SQL Server. Per l'albero delle decisioni, vedere [Choose a Database Engine Upgrade Method](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md).  
  
-   **Requisiti hardware e software:** consultare i requisiti hardware e software per l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questi requisiti sono disponibili in: [Hardware and Software Requirements for Installing SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md). Nel ciclo di pianificazione dell'aggiornamento è opportuno considerare l'aggiornamento dell'hardware (un hardware più recente è più veloce e può ridurre il periodo di licenza a causa di un minor numero di processori o del consolidamento di database e server) e l'aggiornamento del sistema operativo. Questi tipi di modifiche hardware e software influiranno sul tipo di metodo di aggiornamento.  
  
-   **Ambiente corrente:** eseguire ricerche nell'ambiente corrente per comprendere i componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in uso e i client connessi all'ambiente.  
  
    -   **Provider client:** l'aggiornamento non richiede di aggiornare il provider dei singoli clienti, ma è possibile scegliere di eseguire questa operazione. Se si esegue l'aggiornamento da [!INCLUDE[sql14](../../includes/sssql14-md.md)] o versione precedente, le funzionalità [!INCLUDE[sql15](../../includes/sssql15-md.md)] seguenti richiedono un provider aggiornato per ogni client o il provider aggiornato fornirà funzionalità aggiuntive:  
  
       -   [Always Encrypted &#40;Motore di database&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
  
       -   [Estensione database](../../sql-server/stretch-database/stretch-database.md)  
  
       -   [Listener del gruppo di disponibilità, connettività client e failover dell'applicazione &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)  
  
       -   Aggiornamento della protezione SSL  

   >[!NOTE]
   >L'elenco precedente si applica anche a [!INCLUDE[sscurrent](../../includes/sscurrent-md.md)].
  
-   **Componenti di terze parti:** determinare la compatibilità dei componenti di terze parti, ad esempio il backup integrato.  
  
-   **Ambiente di destinazione:** verificare che l'ambiente di destinazione soddisfi i requisiti hardware e software e che supporti i requisiti del sistema originale. Ad esempio, l'aggiornamento potrebbe comportare il consolidamento di più istanze di SQL Server in un'unica e nuova istanza di [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] o la virtualizzazione dell'ambiente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] su un cloud privato o pubblico.  
  
-   **Edizione:** determinare la versione appropriata di [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] e i percorsi di aggiornamento appropriati per l'aggiornamento. Per informazioni dettagliate, vedere [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md). Prima di eseguire l'aggiornamento da un'edizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a un'altra, verificare che le funzionalità attualmente in uso siano supportate nell'edizione a cui si desidera eseguire l'aggiornamento.  
  
    > [!NOTE]  
    >  Quando si esegue l'aggiornamento a [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] da una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition, scegliere tra Enterprise Edition: licenze basate su core ed Enterprise Edition. Queste due edizioni differiscono solo per le modalità di gestione delle licenze. Per altre informazioni, vedere [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
-   **Compatibilità con le versioni precedenti:** consultare l'argomento sulla compatibilità con le versioni precedenti del motore di database di [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] per esaminare i cambiamenti nel comportamento tra la versione [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da cui si esegue l'aggiornamento. Vedere [SQL Server Database Engine Backward Compatibility](../../database-engine/sql-server-database-engine-backward-compatibility.md).  
  
-   **Preparazione aggiornamento:**  eseguire Preparazione aggiornamento di [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] per il supporto nell'analisi dei problemi che potrebbero bloccare il processo di aggiornamento o richiedere modifiche degli script esistenti o delle applicazioni a seguito di una modifica importante. [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] contiene una nuova versione di Preparazione aggiornamento per aiutare i clienti a prepararsi all'aggiornamento di un sistema esistente.  Questo strumento è anche in grado di verificare i database esistenti per verificare che possano sfruttare nuove funzionalità, ad esempio l'estensione delle tabelle, al termine dell'aggiornamento.   
    È possibile scaricare [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]Preparazione aggiornamento  [qui](https://www.microsoft.com/en-us/download/details.aspx?id=48119).  
  
-   **Controllo configurazione sistema:**  eseguire il Controllo configurazione sistema (SCC, System Configuration Checker) di [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] per determinare se il programma di installazione di SQL Server rileva problemi di blocco prima di pianificare effettivamente l'aggiornamento. Per altre informazioni, vedere [Check Parameters for the System Configuration Checker](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md).  
  
-   **Aggiornamento di tabelle con ottimizzazione per la memoria:** quando si aggiorna un'istanza del database SQL Server 2014 che contiene tabelle con ottimizzazione per la memoria in SQL Server 2016, il processo di aggiornamento richiederà più tempo per convertire le tabelle con ottimizzazione per la memoria nel nuovo formato su disco e il database rimane offline durante questa procedura.   La quantità di tempo dipende dalle dimensioni delle tabelle con ottimizzazione per la memoria e dalla velocità del sottosistema di I/O. L'aggiornamento richiede tre dimensioni di operazioni di dati per gli aggiornamenti sul posto e con nuova installazione (il passaggio 1 non è obbligatorio per gli aggiornamenti in sequenza, ma i passaggi 2 e 3 sono obbligatori):  
  
    1.  Eseguire il ripristino del database usano il formato su disco precedente (che include il caricamento di tutti i dati nelle tabelle con ottimizzazione per la memoria all'interno della memoria del disco).  
  
    2.  Serializzare i dati su disco nel nuovo formato su disco  
  
    3.  Eseguire il ripristino del database usano il nuovo formato su disco (che include il caricamento di tutti i dati nelle tabelle con ottimizzazione per la memoria all'interno della memoria del disco).  
  
     In aggiunta, l'insufficienza di spazio sul disco durante questo processo blocca l'esecuzione del ripristino. Verificare che sia disponibile spazio sufficiente su disco per archiviare i database esistenti e spazio di archiviazione aggiuntivo pari alla dimensione corrente dei contenitori nel filegroup MEMORY_OPTIMIZED_DATA all'interno del database per eseguire un aggiornamento sul posto o quando si associa un databae SQL Server 2014 a un'istanza di SQL Server 2016. Usare la query seguente per determinare lo spazio su disco necessario per il filegroup MEMORY_OPTIMIZED_DATA e quindi la quantità di spazio libero su disco necessario per completare correttamente l'aggiornamento:  
  
    ```  
    select cast(sum(size) as float)*8/1024/1024 'size in GB'   
    from sys.database_files  
    where data_space_id in (select data_space_id from sys.filegroups where type=N'FX')  
    ```  
  
## <a name="develop-and-test-the-upgrade-plan"></a>Sviluppare e testare il piano di aggiornamento  
 L'approccio migliore consiste nel considerare l'aggiornamento come qualsiasi progetto IT. È necessario organizzare un team dedicato all'aggiornamento che disponga di amministrazione del database, rete, estrazione, trasformazione e caricamento (ETL) e altre competenze necessarie per l'aggiornamento. Il team deve:  
  
-   **Scegliere il metodo di aggiornamento:** vedere [Scegliere un metodo di aggiornamento del motore di database](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md).  
  
-   **Sviluppare un piano di ripristino dello stato precedente:**. L'esecuzione di questo piano consentirà di ripristinare l'ambiente originale se è necessario eseguire il rollback.  
  
-   **Determinare i criteri di accettazione:** è necessario conoscere l'esito dell'aggiornamento prima di trasferire gli utenti nell'ambiente aggiornato.  
  
-   **Testare il piano di aggiornamento:** per testare le prestazioni con il carico di lavoro effettivo, usare l'utilità Riesecuzione distribuita di Microsoft SQL Server. L'utilità può usare più computer per rieseguire dati di traccia, simulando un carico di lavoro di importanza critica. Eseguendo una riesecuzione in un server di prova prima e dopo un aggiornamento di SQL Server, è possibile rilevare le differenze di prestazioni e individuare eventuali incompatibilità dell'applicazione con l'aggiornamento. Per altre informazioni, vedere [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md) e [Opzioni della riga di comando dello strumento di amministrazione &#40;Distributed Replay Utility&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md).  
  
## <a name="next-steps"></a>Passaggi successivi  
 [Aggiornare il motore di database](../../database-engine/install-windows/upgrade-database-engine.md)  
  
  

