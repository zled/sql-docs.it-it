---
title: 'Aggiornato: avanzato Analitica per i documenti del Server SQL | Documenti Microsoft'
description: Visualizzare i frammenti di contenuto aggiornato per modificati di recente nella documentazione, Analitica avanzato per Microsoft SQL Server.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.workload: advanced-analytics
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: fb6185aae04a1fb53a4db03cbab267e3f52dc779
ms.contentlocale: it-it
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Nuovi e aggiornati: Advanced Analitica per SQL Server



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo degli aggiornamenti di date:* &nbsp; **2017-07-18** &nbsp; - a - &nbsp; **2017-09-11**
- *Area di interesse:* &nbsp; **Analitica avanzate per SQL Server**.

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti portano a nuovi articoli che sono stati aggiunti di recente.


1. [Come eseguire l'assegnazione dei punteggi in tempo reale o punteggio nativo in SQL Server](r/how-to-do-realtime-scoring.md)
2. [Installare training preliminare di machine learning i modelli in SQL Server](r/install-pretrained-models-sql-server.md)
3. [Punteggio nativo](sql-native-scoring.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione vengono estratti gli aggiornamenti raccolti dagli articoli di cui si sono verificati recentemente un aggiornamento di grandi dimensioni.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compact vengono forniti collegamenti a tutti gli articoli aggiornati che sono elencati nella sezione estratti.

1. [Impostare Python Machine Learning Services (In-Database)](#TitleNum_1)
2. [Introduzione a revoscalepy](#TitleNum_2)
3. [Differenze nelle funzionalità di apprendimento automatico tra le edizioni di SQL Server](#TitleNum_3)
4. [Rendere operativo il codice R (servizi di Machine Learning)](#TitleNum_4)
5. [Prestazioni per R Services: risultati e le risorse](#TitleNum_5)
6. [Prestazioni per R Services - ottimizzazione dati](#TitleNum_6)
7. [Gestione dei pacchetti R per SQL Server](#TitleNum_7)
8. [Configurare SQL Server Machine Learning Services (In-Database)](#TitleNum_8)
9. [Configurazione di SQL Server per l'uso con R](#TitleNum_9)
10. [Ottimizzazione delle prestazioni di R in SQL Server](#TitleNum_10)
11. [Scenari di analisi scientifica dei dati e modelli di soluzioni](#TitleNum_11)
12. [Novità di servizi di Machine Learning in SQL Server](#TitleNum_12)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-set-up-python-machine-learning-services-in-databasepythonsetup-python-machine-learning-servicesmd"></a>1. &nbsp;[Impostare Python Machine Learning Services (In-Database)](python/setup-python-machine-learning-services.md)

*Ultimo aggiornamento: 2017-09-07* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Avanti](#TitleNum_2))

<!-- Source markdown line 263.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 fbe2ef55a5caecd64bb21ce854617a10b2d65567 8cd65baf77f27db00a0a4f07f3129a4231edb48b  (PR=3084  ,  Filename=setup-python-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\python\  ,  MergeCommitSha40=05976158e43d7dfafaf02289462d1537f5beeb36) -->



     [Modify the user account pool for SQL Server R Services--../r/modify-the-user-account-pool-for-sql-server-r-services.md)

Se si utilizza SQL Server Standard Edition e non dispone di carichi, è possibile utilizzare viste a gestione dinamica e gli eventi estesi per gestire le risorse del server. È inoltre possibile utilizzare il monitoraggio degli eventi di Windows per questo scopo. Per ulteriori informazioni, vedere [gestione e monitoraggio R Services--... /r/Managing-and-Monitoring-r-Solutions.MD).

**Eseguire l'aggiornamento di machine learning componenti**


Quando si installa Servizi di Machine Learning tramite SQL Server 2017, ottenere la versione dei componenti al momento che la versione è stata pubblicata. Ogni volta che si patch o aggiornare l'istanza di SQL Server, i componenti di machine learning vengono aggiornati anche.

È possibile eseguire l'aggiornamento di machine learning componenti in una pianificazione più veloce rispetto a quelle supportate da versioni di SQL Server, per l'installazione di Microsoft Machine Learning Server. Quando si esegue questa operazione, è anche possibile ottenere tutte le nuove funzionalità supportate nella versione più recente di Machine Learning Server, ad esempio:

+ Gli aggiornamenti ai pacchetti Python per [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) e [microsoftml per Python](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).
+ [Pretrained modelli](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models) per l'analisi di classificazione e il testo di immagine.

Per informazioni su come aggiornare un'istanza, vedere [componenti R aggiornare tramite associazione--... \r\use-sqlbindr-exe-to-upgrade-an-instance-of-SQL-Server.MD).

> [!NOTE]
>
> La versione corrente contiene la versione più recente di tutti i componenti di machine learning. Pertanto, anche se gli aggiornamenti tramite Microsoft Machine Learning Server sono supportati per SQL Server 2017, si applica l'aggiornamento che è attualmente disponibile solo per le istanze di SQL Server 2016.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-introducing-revoscalepypythonwhat-is-revoscalepymd"></a>2. &nbsp;[Introduzione revoscalepy](python/what-is-revoscalepy.md)

*Ultimo aggiornamento: 2017-08-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_1) | [Avanti](#TitleNum_3))

<!-- Source markdown line 79.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 33f4e0e2421fa79fc11931dc7f29bff4432c6f5a d2eac3313a74bc5d5afd754fc357b3693e6801e1  (PR=2939  ,  Filename=what-is-revoscalepy.md  ,  Dirpath=docs\advanced-analytics\python\  ,  MergeCommitSha40=91098c850b0f6affb8e4831325d0f18fd163d71a) -->



| (column_1) | (Colonna_2) | (column_3) |
| :-- | :-- | :-- |
|`rx_btrees` | Gli alberi delle decisioni con Boosting di Adatta sfumatura stocastica|`rx_btrees_ex`Nella versione CTP 2.0|
|`rx_dforest` | Adatta una classificazione e regressione foreste delle decisioni|`rx_dforest_ex`Nella versione CTP 2.0|
|`rx_dtree` | Alberi di classificazione e regressione appropriati |`rx_dtree_ex`Nella versione CTP 2.0|
|`rx_lin_mod` | Creare un modello lineare|`rx_lin_mod_ex`Nella versione CTP 2.0|
|`rx_logit` | Creare un modello di regressione logistica|`rx_logit_ex`Nella versione CTP 2.0|
|`rx_predict` | Generare stime da un modello con training|`rx_predict_ex`Nella versione CTP 2.0|
|`rx_summary` | Generare un riepilogo del modello||

Nuovi algoritmi di machine learning vengono anche forniti dalla versione di Python [MicrosoftML](https://docs.microsoft.com/en-us/r-server/python-reference/microsoftml/microsoftml-package):

| Funzione| Description|
| ------ | ------ |
|`rx_fast_forest` |Creare un modello di foresta delle decisioni|
|`rx_fast_linear` | Regressione lineare con stocastico ascent coordinate doppio|
|`rx_fast_trees` | Creare un modello di struttura ad albero con Boosting |
|`rx_logistic_regression` | Creare un modello di regressione logistica|
|`rx_neural_network` | Creare un modello di rete neurale personalizzabile |
|`rx_oneclass_svm` | Crea un modello SVM un set di dati sbilanciati, per utilizzare il rilevamento delle anomalie|

> [!TIP]
> Molti di questi algoritmi sono già forniti come moduli in Azure Machine Learning.

MicrosoftML per Python include anche un'ampia gamma di trasformazioni e le funzioni di supporto, ad esempio:

+ `rx_predict`Genera stime da un modello con training e può essere utilizzato per l'assegnazione dei punteggi in tempo reale
+ funzioni featurization immagine
+ funzioni per l'estrazione di elaborazione e la valutazione di testo

Per informazioni dettagliate, vedere [Introduzione a MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)


> [!NOTE]
> La community di Python utilizza le convenzioni di codifica che potrebbero essere diverse rispetto a ciò che si è abituati, incluse tutte le lettere minuscole e caratteri di sottolineatura anziché sulla convenzione camel per i nomi dei parametri. Inoltre, forse si notato che il **revoscalepy** libreria è sempre in minuscola. Giusto! Un'altra convenzione Python.



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-differences-in-machine-learning-features-between-editions-of-sql-serverrdifferences-in-r-features-between-editions-of-sql-servermd"></a>3. &nbsp;[Differenze nelle funzionalità di machine learning tra le edizioni di SQL Server](r/differences-in-r-features-between-editions-of-sql-server.md)

*Ultimo aggiornamento: 2017-08-28* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_2) | [Avanti](#TitleNum_4))

<!-- Source markdown line 47.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b5890e212063f3ef228e69afe54e226320d2467f 4e0357701d960c0b8dbda1ac8d56a82f3335c77f  (PR=2964  ,  Filename=differences-in-r-features-between-editions-of-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=7b4f037616e0559ac62bbae5dbe04aeffe529b06) -->



     Only Express Edition with Advanced Services includes the machine learning features. The performance limitations are similar to Standard Edition. Web edition is not intended for tasks such as creating machine learning models; however, you can use the PREDICT function to perform scoring using models trained elsewhere.

-   **Database SQL di Azure**

     Funzionalità di apprendimento macchina, ad esempio R e Python script non sono attualmente supportate in Database SQL di Azure.

     Per ulteriori informazioni e annunci sugli quando la funzionalità specificata sarà disponibile, vedere il blog di SQL Server: [Python in SQL Server 2017: avanzato nel database machine learning](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)


**Lingue supportate in tutte le edizioni**


Per tutte le edizioni, sono supportate le seguenti lingue di machine learning:

+ SQL Server 2017: R e Python
+ SQL Server 2016: R solo

Microsoft R Open è incluso in tutte le edizioni.



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-operationalize-r-code-machine-learning-servicesroperationalizing-your-r-codemd"></a>4. &nbsp;[Codice R rendere operative (servizi di Machine Learning)](r/operationalizing-your-r-code.md)

*Ultimo aggiornamento: 2017-07-27* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_3) | [Avanti](#TitleNum_5))

<!-- Source markdown line 56.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7e11d9a5db93932ec89ca96b5337aa4ea03c1d13 0779f06444b5b73ae2dff8bc190d0e388b4ae8e7  (PR=2660  ,  Filename=operationalizing-your-r-code.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=70a1fd4dbec68d22187585de69a1d603c39e259e) -->



+ [In tempo reale,... / reale tempo-scoring.md) di punteggio, ottimizzata per i batch di piccole dimensioni
+ Assegnazione dei punteggi, in cui viene chiamato da un'applicazione a riga singola
+ [Nativo punteggio-... / sql-nativo-scoring.md), per la stima batch rapido da SQL Server senza chiamare R

Questa procedura dettagliata vengono forniti esempi di assegnazione dei punteggi utilizzando una stored procedure in batch sia la modalità a riga singola:

+ [End-to procedura dettagliata di analisi scientifica dei dati di R in SQL Server,... / tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

Visualizzare questi modelli di soluzioni per gli esempi di integrazione in un'applicazione di punteggio:

+ [Previsioni di vendita al dettaglio](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [Rilevazione di frodi](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/FraudDetection/Introduction.md)
+ [Cliente clustering](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

**Aumentare le prestazioni e scalabilità**


Sebbene il linguaggio R open source è noto per le limitazioni, il pacchetto RevoScaleR API possono operare su grandi set di dati e trarre vantaggio da multithread, multicore, multiprocesso nel database.

Se la soluzione R Usa aggregazioni complesse o comporta grandi set di dati, è possibile sfruttare le aggregazioni in memoria estremamente efficiente e gli indici columnstore di SQL Server e lasciare che il codice R gestisca i calcoli statistici e assegnazione dei punteggi.

Per ulteriori informazioni su come migliorare le prestazioni in SQL Server Machine Learning, vedere:

+ [Ottimizzazione delle prestazioni per SQL Server R Services,... /.. / advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [Suggerimenti di ottimizzazione delle prestazioni](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

**Adattare il codice R per altre piattaforme o contesti di calcolo**




&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-performance-for-r-services-results-and-resourcesrperformance-case-study-r-servicesmd"></a>5. &nbsp;[Delle prestazioni per R Services: risultati e le risorse](r/performance-case-study-r-services.md)

*Ultimo aggiornamento: 2017-07-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_4) | [Avanti](#TitleNum_6))

<!-- Source markdown line 282.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 40c8cd255ead88edc60531d45dd0377ecbaf7c9b eeca5eed96e2223508910b246dbff18173eecea3  (PR=2565  ,  Filename=performance-case-study-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=cf8509cab2424529ca0ed16c936fa63a139dfca4) -->



RevoScaleR sia MicrosoftML pacchetti sono stati utilizzati per il training di un modello predittivo in una soluzione di R complessa che coinvolgono grandi set di dati. Le query SQL e codice R sono identici. Tutti i test sono stati eseguiti in una singola macchina virtuale Azure con SQL Server installato. L'autore quindi confrontata punteggio volte con e senza queste ottimizzazioni fornite da SQL Server:

- Tabelle in memoria
- Soft-NUMA
- Resource Governor

Per valutare l'effetto di soft-NUMA nell'esecuzione dello script R, il team di analisi scientifica dei dati sottoposti a test la soluzione in una macchina virtuale Azure con 20 core fisici. In questi core fisici e quattro nodi soft-NUMA sono stati creati automaticamente, in modo che ogni nodo di contenuto in cinque Core.

Affinità della CPU è stata applicata per valutare l'impatto sui processi R lo scenario corrispondente resume. Quattro **pool di risorse SQL** e quattro **pool di risorse esterne** sono stati creati, e l'affinità della CPU è stato specificato per assicurarsi che lo stesso set di CPU potrebbe essere utilizzato in ogni nodo.

Ognuno dei pool di risorse è stato assegnato a un gruppo di carico di lavoro diversi, per ottimizzare l'utilizzo dell'hardware. Il motivo è che Soft-NUMA e affinità di CPU non è possibile dividere la memoria fisica in nodi NUMA fisici. Pertanto, per definizione tutti i nodi NUMA soft basati sullo stesso nodo NUMA fisico devono utilizzare memoria nello stesso blocco di memoria del sistema operativo. In altre parole, non è senza affinità del processore della memoria.

Per creare questa configurazione è stata usata la seguente procedura:

1. Ridurre la quantità di memoria allocata per impostazione predefinita di SQL Server.

2. Creare quattro nuovi pool per l'esecuzione di processi di R in parallelo.

3. Creare quattro gruppi di carico di lavoro in modo che ogni gruppo di carico di lavoro è associato a un pool di risorse.

4. Riavviare Resource Governor con i nuovi gruppi di carico di lavoro e le assegnazioni.

5. Creare una funzione di classificazione definita dall'utente (UDF) per assegnare varie attività sui gruppi del carico di lavoro diverso.

6. Aggiornare la configurazione di Resource Governor per utilizzare la funzione per i gruppi di carico di lavoro appropriato.



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-performance-for-r-services---data-optimizationrr-and-data-optimization-r-servicesmd"></a>6. &nbsp;[Delle prestazioni per R Services - ottimizzazione dati](r/r-and-data-optimization-r-services.md)

*Ultimo aggiornamento: 2017-07-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_5) | [Avanti](#TitleNum_7))

<!-- Source markdown line 107.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2ae2e54e8c5c8a3ec92fd2017088dd6ee879a9a1 9cb06bdce4ad6dfa2e9dc19da49103a6cd9817b3  (PR=2565  ,  Filename=r-and-data-optimization-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=cf8509cab2424529ca0ed16c936fa63a139dfca4) -->



> Se viene specificata una tabella nell'origine dati anziché una query, R Services utilizza l'approccio euristico interno per determinare le colonne necessarie per recuperare dalla tabella. Tuttavia, questo approccio è improbabile che l'esecuzione in parallelo.

Per garantire che i dati possono essere analizzati in parallelo, la query utilizzata per recuperare i dati debba essere racchiuse in modo che il motore di database può creare un piano di query parallele. Se il codice o l'algoritmo utilizza grandi volumi di dati, assicurarsi che la query in base a `RxSqlServerData` è ottimizzato per l'esecuzione parallela. Una query che non implica un piano di esecuzione parallela può comportare un singolo processo per il calcolo.

Se si desidera lavorare con grandi set di dati, è possibile utilizzare Management Studio o un altro SQL query analyzer prima di eseguire codice R, per analizzare il piano di esecuzione. Quindi, eseguire le procedure consigliate per migliorare le prestazioni della query. Ad esempio, un indice mancante in una tabella può influire sul tempo impiegato per eseguire una query. Per ulteriori informazioni, vedere [monitoraggio e ottimizzazione delle prestazioni--... /.. / relational-databases/performance/monitor-and-tune-for-performance.md).

Un altro errore comune che può influire sulle prestazioni è che una query recupera più colonne rispetto a quelle necessarie. Ad esempio, se una formula si basa su tre colonne, ma la tabella di origine contiene 30 colonne, ma lo spostamento dati inutilmente.

 + Evitare di utilizzare `SELECT *`!
 + Richiedere del tempo per esaminare le colonne nel set di dati e identificare solo quelli necessari per l'analisi
 + Rimuovere le query di tutte le colonne che contengono i tipi di dati che non sono compatibili con il codice R, ad esempio GUID e ROWGUID
 + Verifica della data non supportato e formati di ora
 + Invece di caricare una tabella, creare una visualizzazione che consente di selezionare determinati valori o esegue il cast di colonne per evitare errori di conversione

**Ottimizzare l'algoritmo di apprendimento automatico**


In questa sezione fornisce suggerimenti e le risorse che sono specifiche per RevoScaleR e altre opzioni disponibili in Microsoft R.



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-r-package-management-for-sql-serverrr-package-management-for-sql-server-r-servicesmd"></a>7. &nbsp;[Gestione dei pacchetti R per SQL Server](r/r-package-management-for-sql-server-r-services.md)

*Ultimo aggiornamento: 2017-08-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_6) | [Avanti](#TitleNum_8))

<!-- Source markdown line 22.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2add5a7e1aef02487ac875e353c51161658050a4 5da92dd8b5402266a837172bda9aaabed3162ce8  (PR=2939  ,  Filename=r-package-management-for-sql-server-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=91098c850b0f6affb8e4831325d0f18fd163d71a) -->



In questo argomento vengono descritte le funzionalità di gestione di pacchetto che è possibile utilizzare per gestire i pacchetti R vengono eseguiti in un'istanza di SQL Server.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

**Gestione dei pacchetti utilizzando T-SQL**


È possibile continuare a installare pacchetti R come amministratore nel computer, se si dispone di questi privilegi, e se si è l'unica persona che utilizza il server per i processi di machine learning.

Tuttavia, se si desidera condividere i pacchetti con altri utenti o più utenti necessitano di eseguire i processi di machine learning nel server, è più efficiente per configurare una libreria condivisa pacchetto. SQL Server supporta questo tramite i ruoli predefiniti del database.

L'amministratore del database è responsabile della configurazione dei ruoli e aggiungere utenti ai ruoli. Tramite i ruoli, l'amministratore del database è possibile controllare chi dispone dell'autorizzazione per aggiungere o rimuovere pacchetti R dall'ambiente di SQL Server e controllare l'installazione del pacchetto.

**Ruoli predefiniti del database per la gestione dei pacchetti**


I nuovi ruoli del database seguenti supportano l'installazione sicura e gestione di pacchetti R in SQL Server:

- `rpkgs-users`: Consente agli utenti di usare tutti i pacchetti condivisi che sono stati installati da membri del `rpkgs-shared` ruolo.

- `rpkgs-private`: Fornisce l'accesso ai pacchetti condivisi con le stesse autorizzazioni di `rpkgs-users` ruolo. I membri di questo ruolo possono inoltre installare, rimuovere e usare pacchetti con ambito privato.

-  `rpkgs-shared`: Fornisce le stesse autorizzazioni di `rpkgs-private` ruolo. Gli utenti membri di questo ruolo possono anche installare o rimuovere i pacchetti condivisi.

- `db_owner`: Contiene le stesse autorizzazioni di `rpkgs-shared` ruolo. Può inoltre concedere agli utenti il diritto di installare o rimuovere pacchetti sia condivisi che privati.

**Creazione di una libreria pacchetto esterno utilizzando T-SQL**


Inoltre, SQL Server 2017 supporta l'istruzione T-SQL, **creare libreria esterna**, per supportare la gestione di amministratori di database di librerie esterne. Attualmente è possibile utilizzare questa istruzione per creare raccolte basate su Windows per R. aggiuntive previsto il supporto in futuro per i pacchetti Python e per i pacchetti scritti per l'esecuzione su altre piattaforme, ad esempio Linux.



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-set-up-sql-server-machine-learning-services-in-databaserset-up-sql-server-r-services-in-databasemd"></a>8. &nbsp;[Configurare SQL Server Machine Learning Services (In-Database)](r/set-up-sql-server-r-services-in-database.md)

*Ultimo aggiornamento: 2017-09-07* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_7) | [Avanti](#TitleNum_9))

<!-- Source markdown line 240.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 452dc36b4d0097f9562642238ba49eea0373d25b 4d355f6494b417dd90dce3943e7176eaece7336e  (PR=3070  ,  Filename=set-up-sql-server-r-services-in-database.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=0b832a9306244210e693bde7c476269455e9b6d8) -->



Se si crea una soluzione di R in un computer client di analisi scientifica dei dati ed è necessario eseguire il codice utilizzando il computer SQL Server come contesto di calcolo, è possibile utilizzare un account di accesso SQL o l'autenticazione integrata di Windows.

* Per gli account di accesso SQL: assicurarsi che l'account abbia le autorizzazioni appropriate sul database in cui si leggeranno i dati. È possibile farlo mediante l'aggiunta di *connettersi* e *selezionare* autorizzazioni, o aggiungendo l'account di accesso di *db_datareader* ruolo. Per gli account di accesso necessarie per creare oggetti, aggiungere *ruoli DDL_admin* diritti. Per gli account di accesso deve salvare dati in tabelle, aggiungere l'account di accesso di *db_datawriter* ruolo.

* Per l'autenticazione di Windows: È necessario configurare un'origine dati ODBC nel client di analisi scientifica dei dati che specifica il nome dell'istanza e altre informazioni di connessione. Per ulteriori informazioni, vedere [Amministrazione origine dati ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

**Passaggi successivi**


Dopo aver verificato che la funzionalità di esecuzione dello script viene eseguita in SQL Server, è possibile eseguire i comandi di R e Python da SQL Server Management Studio, codice di Visual Studio o qualsiasi altro client che può inviare istruzioni T-SQL per il server.

Tuttavia, è consigliabile apportare alcune modifiche alla configurazione del sistema per supportare un uso massiccio di machine learning, o aggiungere nuovi pacchetti di R.

Questa sezione vengono elencate alcune modifiche comuni che è possibile apportare per supportare l'apprendimento.

**Aggiungere altri account di lavoro**


Se si ritiene che è possibile usare R frequentemente o se si prevede che molti utenti da script in esecuzione contemporaneamente, è possibile aumentare il numero di account di lavoro assegnati per il servizio Launchpad. Per ulteriori informazioni, vedere [modificare il pool di account utente per SQL Server R Services--modify-the-user-account-pool-for-sql-server-r-services.md).

**<a name="bkmk_optimize"></a>Ottimizzare il server per l'esecuzione dello script esterno**




&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-sql-server-configuration-for-use-with-rrsql-server-configuration-r-servicesmd"></a>9. &nbsp;[Configurazione di SQL Server per l'uso con R](r/sql-server-configuration-r-services.md)

*Ultimo aggiornamento: 2017-07-27* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_8) | [Avanti](#TitleNum_10))

<!-- Source markdown line 149.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3f57bae70e3c118c1e2bcd57017322940bae83f8 f296242d470db47077cba4215ef420bd0c60bf33  (PR=2660  ,  Filename=sql-server-configuration-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=70a1fd4dbec68d22187585de69a1d603c39e259e) -->



Se la query restituisce un solo nodo di memoria (nodo 0), non si dispone dell'hardware NUMA o l'hardware è configurato come interleaved (non NUMA). SQL Server ignora inoltre hardware NUMA quando non esiste un numero inferiore o quattro CPU, o se almeno un nodo è solo una CPU.

Se il computer con più processori, ma non dispone di hardware NUMA, è inoltre possibile utilizzare [Soft-NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server) per suddividere le CPU in gruppi più piccoli.  In SQL Server 2016 e SQL Server 2017, la funzionalità di Soft-NUMA viene attivata automaticamente all'avvio del servizio SQL Server.

Quando Soft-NUMA è abilitato, SQL Server gestisce automaticamente i nodi. Tuttavia, per ottimizzare i carichi di lavoro specifici, è possibile disabilitare _affinità soft_ e configurare manualmente l'affinità della CPU per i nodi NUMA soft. Ciò consente di visualizzare un maggiore controllo su cui i carichi di lavoro assegnati a quali nodi, in particolare se si utilizza un'edizione di SQL Server che supporta la governance delle risorse. Specificando l'affinità di CPU e allineamento dei pool di risorse con i gruppi di CPU, è possibile ridurre la latenza e verificare che i processi correlati vengano eseguiti nello stesso nodo NUMA.

Il processo generale per la configurazione soft-NUMA e affinità di CPU per supportare i carichi di lavoro R è il seguente:

1. Abilita soft-NUMA, se disponibile
2. Definire l'affinità processori
3. Creare pool di risorse per i processi esterni, utilizzando [Resource Governor,... /r/Resource-governance-for-r-Services.MD)
4. Assegnare i [gruppi di carico di lavoro.... /.. / relational-databases/resource-governor/resource-governor-workload-group.md) a specifici gruppi di affinità

Per informazioni dettagliate, incluso il codice di esempio, vedere l'esercitazione: [SQL ottimizzazione suggerimenti (Ke Huang)](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

**Altre risorse:**



&nbsp;

&nbsp;

---

<a name="TitleNum_10"/>

### <a name="10-nbsp-performance-tuning-for-r-in-sql-serverrsql-server-r-services-performance-tuningmd"></a>10. &nbsp;[Ottimizzazione delle prestazioni di R in SQL Server](r/sql-server-r-services-performance-tuning.md)

*Ultimo aggiornamento: 2017-07-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_9) | [Avanti](#TitleNum_11))

<!-- Source markdown line 76.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9c30753efdec81e499d5654b5b7a07f0cfe5b003 136a9f483bc8c9e1f69cf9d340d1472c21a52ec4  (PR=2565  ,  Filename=sql-server-r-services-performance-tuning.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=cf8509cab2424529ca0ed16c936fa63a139dfca4) -->



- Configurare l'istanza di SQL Server in R e di bilanciare le operazioni del motore di database o di esecuzione ai livelli appropriati di script Python. Può trattarsi di modifica delle impostazioni predefinite di SQL Server per la memoria e utilizzo della CPU, NUMA e le impostazioni affinità processori e la creazione di gruppi di risorse.

- Ottimizzare i computer del server per supportare un utilizzo efficiente di script esterni. Può trattarsi di aumentare il numero di account utilizzati per l'esecuzione di script esterni, abilitare la gestione di pacchetto, e assegnare gli utenti ai relativi ruoli di sicurezza.

- L'applicazione ottimizzazioni specifiche per l'archiviazione dei dati e trasferimento in SQL Server, tra cui l'indicizzazione e strategie di statistiche, Progettazione query e l'ottimizzazione delle query e la struttura delle tabelle che vengono usati per machine learning. È inoltre possibile analizzare origini dati e i metodi di trasporto, dati o modificare i processi ETL per ottimizzare l'estrazione di funzioni.

- Ottimizzare il modello di analisi per evitare inefficienze. L'ambito delle ottimizzazioni possibili dipendono dalla complessità del codice R e i pacchetti e i dati in uso. Attività principali includono eliminando le trasformazioni costosi dei dati o il trasferimento di dati preparazione attività o delle funzionalità engineering da R o Python per i processi ETL o SQL. È inoltre potrebbe effettuare il refactoring di script, eliminare Installa pacchetto in linea, dividere il codice R in procedure separate per il training, l'assegnazione dei punteggi e valutazione o semplificare il codice per lavorare in modo più efficiente come una stored procedure.

**Articoli di questa serie**


+ [Ottimizzazione delle prestazioni di R in SQL Server - hardware:... \r\sql-Server-Configuration-r-Services.MD)

    Vengono fornite indicazioni per la configurazione dell'hardware che.... Includi-NotShown - ssNoVersion_md-... \..\includes\ssnoversion-md.md)] viene installato e per la configurazione dell'istanza di SQL Server per supportare meglio gli script esterni. È particolarmente utile per **gli amministratori del database**.

+ [Ottimizzazione delle prestazioni di R in SQL Server - ottimizzazione di codice e i dati--... \r\r-and-Data-Optimization-r-Services.MD)



&nbsp;

&nbsp;

---

<a name="TitleNum_11"/>

### <a name="11-nbsp-data-science-scenarios-and-solution-templatestutorialsdata-science-scenarios-and-solution-templatesmd"></a>11. &nbsp;[Scenari di analisi scientifica dei dati e modelli di soluzioni](tutorials/data-science-scenarios-and-solution-templates.md)

*Ultimo aggiornamento: 2017-08-28* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_10) | [Avanti](#TitleNum_12))

<!-- Source markdown line 45.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 22c621731015f2192cb0b8d61b22062a4be50e70 6cf9e3f0a3803ed2bce9c4ffadfd7314f15f6b51  (PR=2964  ,  Filename=data-science-scenarios-and-solution-templates.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=7b4f037616e0559ac62bbae5dbe04aeffe529b06) -->



[Prevedere come e quando contattare lead](https://microsoft.github.io/r-server-campaign-optimization/)

**Novità:** questa soluzione Usa dati settore assicurazione per stimare i lead in base a dati demografici, i dati cronologici di risposta e dettagli specifici del prodotto.  Indicazioni vengono generate anche per indicare la migliore canale e l'ora agli utenti di approccio per influenzare il comportamento di acquisto.

**Procedura:** la soluzione creata e confronta più modelli. La soluzione illustra inoltre l'integrazione automatica dei dati e la preparazione dei dati tramite le stored procedure. Esempi di parallela vengono forniti per SQL Server in-database, in Azure e HDInsight Spark.

**Sanità: stimare durata della permanenza in ospedale**


[Durata della permanenza in ospedale un numero di stima](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

**Novità:** prevedere con precisione quali pazienti potrebbero richiedere ricovero a lungo termine è una parte importante di attenzione e pianificazione. Gli amministratori devono essere in grado di determinare quali strutture richiedono ulteriori risorse e operatori sanitari desidera garantire che soddisfino le esigenze di pazienti.

**Procedura:** questa soluzione Usa la macchina virtuale di analisi scientifica dei dati e include un'istanza di SQL Server con machine learning abilitato. Include inoltre un set di report di Power BI che è possibile utilizzare per interagire con un modello distribuito.

**Varianza del cliente**


[Modello di stima della varianza del cliente (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/Churn/Introduction.md)

**Novità:** analisi e stima della varianza del cliente è importante ogni settore in cui deve essere gestita e ha impedita la perdita di clienti alla concorrenza: banking, telecomunicazioni e delle vendite al dettaglio, solo per citarne alcune. L'obiettivo dell'analisi dell'abbandono dei clienti è l'identificazione dei clienti con alta probabilità di abbandono e l'adozione di misure appropriate per mantenere tali clienti e la loro attività.



&nbsp;

&nbsp;

---

<a name="TitleNum_12"/>

### <a name="12-nbsp-whats-new-in-machine-learning-services-in-sql-serverwhat-s-new-in-sql-server-machine-learning-servicesmd"></a>12. &nbsp;[Novità di servizi di Machine Learning in SQL Server](what-s-new-in-sql-server-machine-learning-services.md)

*Ultimo aggiornamento: 2017-08-02* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_11))

<!-- Source markdown line 33.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 025e68a93895a3788a63847cd91bff068775acf3 6dc0be2920c670235038a126d135e08d6f16ec3a  (PR=2712  ,  Filename=what-s-new-in-sql-server-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\  ,  MergeCommitSha40=ea75391663eb4d509c10fb785fcf321558ff0b6e) -->



> Servizi di Machine learning, incluso l'uso di R o Python, non sono attualmente supportati quando si esegue SQL Server in Linux o in database SQL di Azure. Cercare le modifiche in una versione successiva.
>
> Tuttavia, il punteggio nativa utilizzando la funzione di stima è attualmente supportato nell'edizione Linux.

**Integrazione di Python nel database**


È possibile eseguire Python nelle stored procedure, o eseguire Python in remoto utilizzando il computer SQL Server come contesto di calcolo. Questa integrazione apre nuove strade per vasta community di Python dati e gli sviluppatori esperti per sfruttare la potenza di SQL Server e per esplorare le innovazioni da Microsoft, ad esempio **revoscalepy** e **microsoftml**.

Gli sviluppatori di SQL Server ottengono l'accesso alle librerie Python estese da dell'ecosistema di origine aperti, inclusi Framework famosi come scikit-informazioni su, Tensorflow, Caffe e Theano/Keras.

Ma è in esecuzione nel database non è sufficiente per machine learning; Python Esistono numerose di altre applicazioni potenziali per l'integrazione di Python con SQL, sfruttando i punti di forza dei rispettivi linguaggi per fornire potenti soluzioni più intelligenti.

+ **revoscalepy**

    Questa versione include la versione finale di **revoscalepy**, che fornisce Pythonic equivalenti di scalabile, streaming algoritmi in RevoScaleR. È possibile creare modelli di Python per la regressione lineare e logistica, gli alberi delle decisioni, alberi con Boosting e foreste casuali, tutti gli eseguibili in parallelo e in grado di in esecuzione in contesti di calcolo remoto.

    Per ulteriori informazioni, vedere [novità revoscalepy - python/simulazione-è-revoscalepy.md).

+ Contesti di calcolo remoti per Python

    Questa versione supporta l'utilizzo di più origini dati e i contesti di calcolo remoto. L'esperto di dati o lo sviluppatore può eseguire codice Python in un Server SQL remoto, per esplorare i dati e compilare modelli senza spostare i dati. L'uso di contesti di calcolo remoto richiede **revoscalepy**.







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Questa sezione sono elencati gli articoli molto simili per gli articoli aggiornati di recente in altre aree di interesse, entro l'archivio pubblico di GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (3 + 12): **Analitica avanzate per SQL** documenti](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (5 + 0): **Connect to SQL** documenti](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (5 + 1): **motore di Database per SQL** documenti](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (19 + 82): **Integration Services per SQL** documenti](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (1 + 8): **Linux per SQL** documenti](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (12 + 1): **database relazionali di SQL** documenti](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (0 + 1): **Reporting Services per SQL** documenti](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (7 + 1): **Microsoft SQL Server** documenti](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (1 + 1): **SQL Server Data Tools (SSDT)** documenti](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (0 + 2): **SQL Server Migration Assistant (SSMA)** documenti](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (1 + 4): **SQL Server Management Studio (SSMS)** documenti](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornati (4 + 1): **Transact-SQL** documenti](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (0 + 1): **Tools per SQL** documenti](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0 + 0): **Analysis Services per SQL** documenti](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0 + 0): **Master Data Services (MDS) per SQL** documenti](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)



