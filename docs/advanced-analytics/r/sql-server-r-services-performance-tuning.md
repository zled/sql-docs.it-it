---
title: Ottimizzazione delle prestazioni di SQL Server R Services | Microsoft Docs
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf6f3b7d-f9f9-4e45-b0d1-07850b53e0c5
caps.latest.revision: "20"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a1f3db839e51a85151141149d7a2778ce8cd423b
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="performance-tuning-for-r-in-sql-server"></a>Ottimizzazione delle prestazioni di R in SQL Server

In questo articolo è il primo in una serie di quattro articoli che descrivono l'ottimizzazione delle prestazioni per R Services, in base alle due case study:

- Test delle prestazioni condotti dal team di sviluppo del prodotto per convalidare il profilo di prestazioni delle soluzioni R

- Ottimizzazione delle prestazioni dal team di analisi scientifica dei dati di Microsoft per uno scenario di apprendimento specifico spesso richiesto dai clienti.

L'obiettivo di questa serie è fornire informazioni aggiuntive sui tipi di tecniche che risultano più utili per eseguire processi R in SQL Server l'ottimizzazione delle prestazioni.

+ In questo argomento (primo) viene fornita una panoramica dell'architettura e alcuni problemi comuni durante l'ottimizzazione per le attività di analisi scientifica dei dati.
+ Il secondo articolo vengono illustrati i componenti hardware specifici e le ottimizzazioni di SQL Server.
+ Il terzo articolo descrive le ottimizzazioni nel codice R e risorse per rendere operativo il.
+ Il quarto articolo descrive i metodi di test in dettaglio e i risultati di report e le conclusioni.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

## <a name="performance-goals-and-targeted-scenarios"></a>Obiettivi di prestazioni e scenari di destinazione

La funzionalità di R Services è stato introdotto in SQL Server 2016 per supportare l'esecuzione di script R da SQL Server. Quando si utilizza questa funzionalità, il runtime di R opera in un processo separato dal motore di database, ma scambia dati in modo sicuro con il motore di database utilizzando le risorse del server e servizi che interagiscono con SQL Server, ad esempio la finestra di avvio attendibile.

In SQL Server 2017, è stato annunciato il supporto per l'esecuzione di script Python con la stessa architettura, lingua aggiuntiva da seguire in futuro.

Man mano che aumenta il numero di versioni supportate e della lingua, è importante che l'amministratore del database e un progettista del database siano consapevoli del potenziale di contesa delle risorse a causa di processi di machine learning e che sono in grado di configurare il server per supportare i nuovi carichi di lavoro. Sebbene mantenendo analitica dati Elimina spostamenti dei dati non protetta, sposta i carichi di lavoro analitici il portatile dell'esperto di dati e al server che ospita i dati.

Ottimizzazione delle prestazioni per machine learning non è chiaramente una proposta giusto. Le seguenti attività comuni potrebbe essere profili delle prestazioni molto diverse:

- Attività di formazione: creazione e di training di un modello di regressione e di formazione di una rete neurale
- Progettazione di funzionalità con R e l'estrazione di funzioni con T-SQL
- Punteggio in singole righe o batch di piccole dimensioni, e delle operazioni bulk tramite input tabulare di punteggio
- Esegue l'assegnazione dei punteggi in R e distribuzione di modelli nell'ambiente di produzione in SQL Server nelle stored procedure
- La modifica del codice R per ridurre al minimo il trasferimento dei dati o rimuovere le trasformazioni dei dati costosi
- Abilitare i test automatizzati e ripetizione di training dei modelli

Poiché la scelta di tecniche di ottimizzazione dipende da quale attività sono fondamentale per l'applicazione o un caso d'uso, i case study coprire suggerimenti sulle prestazioni generali e informazioni aggiuntive su come ottimizzare per uno scenario specifico, l'ottimizzazione di punteggio batch.

+ **Opzioni di ottimizzazione singoli in SQL Server**

    Nel primo prestazioni case study, sono stati eseguiti più test in un singolo set di dati utilizzando un solo tipo di modello. È stato utilizzato l'algoritmo di rxLinMod in RevoscaleR per compilare un modello e creare punteggi da esso, ma il codice, nonché le tabelle di dati sottostanti sono state modificate in modo sistematico per testare l'impatto di ogni modifica.

    In un'esecuzione dei test, ad esempio, il codice R è stato modificato in modo che sia stato eseguito un confronto tra Progettazione funzionalità utilizzando una funzione di trasformazione e pre-elaborazione le funzionalità e quindi il caricamento delle funzionalità da una tabella. In un'altra esecuzione dei test, le prestazioni di training del modello è stata confrontata tra l'utilizzo di una tabella con indicizzazione standard e dati in una tabella con vari tipi di compressione o nuovi tipi di indice.

+ **Ottimizzazione per uno specifico scenario di assegnazione dei punteggi di volumi elevati**

    L'attività di machine learning nel secondo caso di Studio prevede l'elaborazione di molti curriculum inviati per più posizioni e individuare il candidato migliore per ogni posizione del processo. Il modello di machine learning stesso viene formulato come un problema di classificazione binaria: accetta una descrizione resume e processo come input e genera la probabilità per ogni coppia resume-job. Poiché l'obiettivo consiste nel trovare la corrispondenza migliore, una soglia di probabilità definita dall'utente viene utilizzata per filtrare ulteriormente e di ottenere solo le corrispondenze valide.

    Per questa soluzione, l'obiettivo principale è stata per ottenere una bassa latenza durante l'assegnazione dei punteggi. Tuttavia, questa attività è onerosa anche durante il processo di punteggio, perché ogni nuovo processo deve essere confrontato con milioni di curriculum all'interno di un intervallo di tempo ragionevole. Inoltre, la fase di progettazione funzionalità produce funzionalità oltre 2000 per ogni processo o ripresa e un collo di bottiglia significativo delle prestazioni.

È consigliabile esaminare tutti i risultati del primo case study per determinare quali tecniche sono applicabili alla soluzione e valutare il potenziale impatto.

Quindi, esaminare i risultati del punteggio ottimizzazione case study per vedere come l'autore applicate diverse tecniche e ottimizzato il server per supportare un determinato carico di lavoro.

## <a name="performance-optimization-process"></a>Processo di ottimizzazione delle prestazioni

Configurazione e ottimizzazione delle prestazioni richiede la creazione di una base solida, in cui le ottimizzazioni di livello progettate per carichi di lavoro specifici:

- Scegliere un server appropriato per analitica host. In genere, un report secondario, del data warehouse o un altro server che è già in uso per altri report o analitica è preferito. Tuttavia, in una soluzione ibrida transazionale analytical processing, elaborazione (HTAP) sui dati operativi utilizzabile come input per R per il punteggio veloce.

- Configurare l'istanza di SQL Server in R e di bilanciare le operazioni del motore di database o di esecuzione ai livelli appropriati di script Python. Può trattarsi di modifica delle impostazioni predefinite di SQL Server per la memoria e utilizzo della CPU, NUMA e le impostazioni affinità processori e la creazione di gruppi di risorse.

- Ottimizzare i computer del server per supportare un utilizzo efficiente di script esterni. Può trattarsi di aumentare il numero di account utilizzati per l'esecuzione di script esterni, abilitare la gestione di pacchetto, e assegnare gli utenti ai relativi ruoli di sicurezza.

- L'applicazione ottimizzazioni specifiche per l'archiviazione dei dati e trasferimento in SQL Server, tra cui l'indicizzazione e strategie di statistiche, Progettazione query e l'ottimizzazione delle query e la struttura delle tabelle che vengono usati per machine learning. È inoltre possibile analizzare origini dati e i metodi di trasporto, dati o modificare i processi ETL per ottimizzare l'estrazione di funzioni.

- Ottimizzare il modello di analisi per evitare inefficienze. L'ambito delle ottimizzazioni possibili dipendono dalla complessità del codice R e i pacchetti e i dati in uso. Attività principali includono eliminando le trasformazioni costosi dei dati o il trasferimento di dati preparazione attività o delle funzionalità engineering da R o Python per i processi ETL o SQL. È inoltre potrebbe effettuare il refactoring di script, eliminare Installa pacchetto in linea, dividere il codice R in procedure separate per il training, l'assegnazione dei punteggi e valutazione o semplificare il codice per lavorare in modo più efficiente come una stored procedure.

## <a name="articles-in-this-series"></a>Articoli di questa serie

+ [Ottimizzazione delle prestazioni di R in SQL Server - hardware](..\r\sql-server-configuration-r-services.md)

    Vengono fornite indicazioni per la configurazione dell'hardware che [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] è installato e per la configurazione dell'istanza di SQL Server per supportare meglio gli script esterni. È particolarmente utile per **gli amministratori del database**.

+ [Ottimizzazione delle prestazioni di R in SQL Server - codice e i dati ottimizzazione](..\r\r-and-data-optimization-r-services.md)

    Vengono forniti suggerimenti specifici su come ottimizzare lo script esterno per evitare problemi noti. È più utile **data Scientist**.

    [!NOTE]
    > Mentre la maggior parte delle informazioni in questa sezione si applica a R in generale, alcune informazioni sono specifiche per le funzioni analitiche RevoScaleR. Linee guida dettagliate sulle prestazioni non è disponibile per **revoscalepy** e altre librerie di Python è supportato.

+ [Ottimizzazione delle prestazioni di R in SQL Server - metodi e i risultati](..\r\performance-case-study-r-services.md)

    Riepiloga i dati che è stata utilizzata due case study, la modalità in cui è stata testata le prestazioni e risultati di influenza le ottimizzazioni.
