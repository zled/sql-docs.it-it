---
title: Problemi noti di Machine Learning Services | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 20a3742c9dfc956accd902539524724cac3f9b8c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34563859"
---
# <a name="known-issues-in-machine-learning-services"></a>Problemi noti in servizi di Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo descrive i problemi noti o limitazioni con i componenti che vengono forniti come un'opzione in SQL Server 2016 e SQL Server 2017 di apprendimento automatico.

Le informazioni riportate di seguito si applicano a tutte le operazioni seguenti, se non diversamente indicato:

SQL Server 2016

- R Services (In-Database)
- Microsoft R Server (Standalone)

SQL Server 2017

- Machine Learning servizi per R (In-Database)
- Machine Learning Services per Python (In-Database)
- Machine Learning Server (Standalone)

## <a name="setup-and-configuration-issues"></a>Problemi di installazione e configurazione

Per una descrizione dei processi e domande comuni che riguardano l'installazione iniziale e la configurazione, vedere [domande frequenti sull'installazione e aggiornamento](r/upgrade-and-installation-faq-sql-server-r-services.md). Contiene informazioni sugli aggiornamenti, installazione side-by-side e l'installazione di nuovi componenti di R o Python.

### <a name="unable-to-install-sql-server-machine-learning-features-on-a-domain-controller"></a>Non è possibile installare le funzionalità di SQL Server machine learning in un controller di dominio

Se si tenta di installare SQL Server 2016 R Services o i servizi di SQL Server 2017 Machine Learning in un controller di dominio, l'installazione non riesce, con questi errori:

> *Si è verificato un errore durante il processo di installazione della funzionalità*
> 
> *Impossibile trovare il gruppo con identità*
> 
> *Codice di errore componente: 0x80131509*

L'errore si verifica perché, in un controller di dominio, il servizio non è possibile creare gli account locali 20 necessari per eseguire l'apprendimento. In generale, non è consigliabile installare SQL Server in un controller di dominio. Per ulteriori informazioni, vedere [bollettino supporto 2032911](https://support.microsoft.com/en-us/help/2032911/you-may-encounter-problems-when-installing-sql-server-on-a-domain-cont).

### <a name="install-the-latest-service-release-to-ensure-compatibility-with-microsoft-r-client"></a>Installare la versione più recente del servizio per garantire la compatibilità con Client di Microsoft R

Se si installa la versione più recente di Microsoft R Client e utilizzarlo per l'esecuzione di R in SQL Server in un contesto di calcolo remoto, è possibile che venga visualizzato un errore simile al seguente:

> *Si esegue 9.x.x versione di Microsoft R Client nel computer, non è compatibile con Microsoft R Server versione 8.x.x. Download and install a compatible version.* (Sul computer è in esecuzione la versione 9.0.0 di Microsoft R, che non è compatibile con Microsoft R Server versione 8.0.3. Scaricare e installare una versione compatibile.)

SQL Server 2016 richiede che le librerie di R nel client corrispondano esattamente le librerie di R nel server. La restrizione è stata rimossa per le versioni successive a R Server 9.0.1. Tuttavia, se si verifica questo errore, verificare la versione delle librerie R che viene utilizzata dal client e server e, se necessario, aggiorna il client in modo che corrisponda alla versione del server.

La versione di R che viene installato con SQL Server R Services viene aggiornata ogni volta che viene installata una versione del servizio SQL Server. Per assicurarsi che siano sempre le versioni aggiornate dei componenti di R, assicurarsi di installare tutti i service pack.

Per garantire la compatibilità con Client di Microsoft R 9.0.0, installare gli aggiornamenti descritti in questo [articolo del supporto tecnico](https://support.microsoft.com/kb/3210262).

Per evitare problemi con i pacchetti R, è inoltre possibile aggiornare la versione delle librerie R installati sul server, modificando il contratto di servizio a usare i criteri di supporto del ciclo di vita moderne, come descritto in [nella sezione successiva](#bkmk_sqlbindr). Quando si esegue questa operazione, la versione di R che viene installato con SQL Server viene aggiornata in base alla stessa pianificazione utilizzato per gli aggiornamenti di machine Learning Server (in precedenza Microsoft R Server).

**Si applica a:** SQL Server 2016 R Services, con R Server versione 9.0.0 o versioni precedenti

### <a name="r-components-missing-from-cu3-setup"></a>Componenti di R mancante dal programma di installazione CU3

Un numero limitato di macchine virtuali di Azure è stato eseguito il provisioning senza i file di installazione di R che devono essere inclusi in SQL Server. Il problema si applica alle macchine virtuali, il provisioning nel periodo da 2018-01-05-2018-01-23. Questo problema potrebbe influire sulle installazioni locali, se è applicato l'aggiornamento CU3 per SQL Server 2017 durante il periodo da 2018-01-05 2018-01-23.

Una versione del servizio è stata specificata che include la versione corretta del file di installazione di R.

+ [Pacchetto di aggiornamento cumulativo 3 per SQL Server 2017 KB4052987](https://www.microsoft.com/en-us/download/details.aspx?id=56128).

Per installare i componenti e ripristinare CU3 2017 di SQL Server, è necessario disinstallare CU3 e reinstallare la versione aggiornata:

1. Scaricare il file di installazione CU3 aggiornato, che include i programmi di installazione di R.
2. Disinstallare CU3. Nel Pannello di controllo, cercare **disinstallare un aggiornamento**, quindi selezionare "Hotfix 3015 per SQL Server 2017 (KB4052987) (64 bit)". Procedere con la procedura di disinstallazione.
3. Reinstallare l'aggiornamento CU3, facendo doppio clic sull'aggiornamento per KB4052987 appena scaricato: `SQLServer2017-KB4052987-x64.exe`. Seguire le istruzioni di installazione.

### <a name="unable-to-install-python-components-in-offline-installations-of-sql-server-2017-ctp-20-or-later"></a>Impossibile installare i componenti di Python nelle installazioni non in linea di SQL Server 2017 CTP 2.0 o versione successiva

Se si installa una versione non definitiva di SQL Server 2017 in un computer senza accesso a internet, il programma di installazione potrebbe non riuscire visualizzare la pagina che richiede il percorso dei componenti scaricati Python. In questo caso, è possibile installare la funzionalità di servizi di Machine Learning, ma non i componenti di Python.

Questo problema viene risolto nella versione di rilascio. Inoltre, questa limitazione non si applica ai componenti di R.

**Si applica a:** 2017 di SQL Server con Python

### <a name="bkmk_sqlbindr"></a> Avviso di versione non compatibile quando ci si connette a una versione precedente di SQL Server R Services da un client usando [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]

Quando si esegue il codice R nel contesto di calcolo di un SQL Server 2016, è possibile visualizzare l'errore seguente:

> *Si esegue la versione 9.0.0 di Microsoft R Client nel computer, non è compatibile con la versione 8.0.3 Microsoft R Server. Download and install a compatible version.* (Sul computer è in esecuzione la versione 9.0.0 di Microsoft R, che non è compatibile con Microsoft R Server versione 8.0.3. Scaricare e installare una versione compatibile.)

Questo messaggio viene visualizzato in presenza di una delle due istruzioni seguenti,

+ R Server (Standalone) è stato installato in un computer client tramite installazione guidata di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].
+ Si è installato Microsoft R Server mediante il [separare Windows installer](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

Per garantire che il server e i client usano la stessa versione potrebbe essere necessario utilizzare _associazione_supportati per Microsoft R Server 9.0 e versioni successive aggiornare i componenti di R in istanze di SQL Server 2016. Per determinare se il supporto per gli aggiornamenti disponibili per la versione di R Services, vedere [aggiornare un'istanza di servizi di R usando SqlBindR.exe](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

**Si applica a:** SQL Server 2016 R Services, con R Server versione 9.0.0 o versioni precedenti

### <a name="setup-for-sql-server-2016-service-releases-might-fail-to-install-newer-versions-of-r-components"></a>Durante l'installazione di alcune versioni del servizio SQL Server 2016 è possibile che le versioni più recenti dei componenti R non vengano installate

Quando si installa un aggiornamento cumulativo o installare un service pack per SQL Server 2016 in un computer che non è connesso a internet, l'installazione guidata potrebbe non riuscire a visualizzare il prompt che consente di aggiornare i componenti di R usando il file CAB scaricati. In genere questo errore si verifica quando più componenti sono stati installati con il motore di database.

In alternativa, è possibile installare la versione del servizio tramite la riga di comando e specificando la `MRCACHEDIRECTORY` argomento, come illustrato in questo esempio, che consente di installare gli aggiornamenti CU1:

`C:\<path to installation media>\SQLServer2016-KB3164674-x64.exe /Action=Patch /IACCEPTROPENLICENSETERMS /MRCACHEDIRECTORY=<path to CU1 CAB files>`

Per ottenere i programmi di installazione più recente, vedere [installare i componenti di machine learning senza accesso a internet](install/sql-ml-component-install-without-internet-access.md).

**Si applica a:** SQL Server 2016 R Services, con R Server versione 9.0.0 o versioni precedenti

### <a name="launchpad-services-fails-to-start-if-the-version-is-different-from-the-r-version"></a>Servizi di finestra di avvio non viene avviato se la versione è diversa dalla versione di R

Se si installa SQL Server R Services separatamente dal motore di database e le versioni di compilazione sono diverse, si potrebbe vedere il seguente errore nel registro eventi di sistema:

> *Il servizio Launchpad di SQL Server non è stato possibile avviare il seguente errore: il servizio non ha risposto alla richiesta di avvio o di controllo in modo tempestivo.*

Ad esempio, questo errore potrebbe verificarsi se si installa il motore di database utilizzando la versione di rilascio, applicare una patch per aggiornare il motore di database e quindi aggiungere la funzionalità di R Services utilizzando la versione di rilascio.

Per evitare questo problema, utilizzare un'utilità di gestione di File, ad esempio per confrontare le versioni di Launchpad.exe con la versione dei file binari SQL, ad esempio sqldk.dll. Tutti i componenti devono avere lo stesso numero di versione. Se si aggiorna un componente, assicurarsi di applicare lo stesso aggiornamento a tutti gli altri componenti installati.

Cercare nella finestra di avvio di `Binn` cartella per l'istanza. Ad esempio, in un'installazione predefinita di SQL Server 2016, il percorso potrebbe essere `C:\Program Files\Microsoft SQL Server\MSSQL.13.InstanceNameMSSQL\Binn`. 

### <a name="remote-compute-contexts-are-blocked-by-a-firewall-in-sql-server-instances-that-are-running-on-azure-virtual-machines"></a>Contesti di calcolo remoto bloccati da un firewall nelle istanze di SQL Server in esecuzione in macchine virtuali di Azure

Se è stato installato [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] in una macchina virtuale Windows Azure, potrebbe non essere in grado di utilizzare i contesti di calcolo che richiedono l'uso dell'area di lavoro della macchina virtuale. Il motivo è che, per impostazione predefinita, il firewall in macchine virtuali di Azure include una regola che blocca l'accesso per gli account utente di R locali rete.

In alternativa, nella macchina virtuale di Azure, aprire **Windows Firewall con sicurezza avanzata**selezionare **regole in uscita**e disabilitare la regola seguente: **bloccare l'accesso di rete per gli account utente locale di R in SQL Server instance MSSQLSERVER**. È anche possibile lasciare la regola attivata, ma modificare la proprietà di sicurezza in **Consenti se sicura**.

### <a name="implied-authentication-in-sqlexpress"></a>Autenticazione implicita in SQLEXPRESS

Quando si eseguono i processi R da una workstation di analisi scientifica dei dati remoti tramite l'autenticazione integrata di Windows, SQL Server utilizza *autenticazione implicita* per generare qualsiasi chiamata ODBC locale che potrebbe essere richiesti dallo script. Questa funzionalità, tuttavia, non funziona nella build RTM di SQL Server Express Edition.

Per risolvere il problema, è consigliabile eseguire l'aggiornamento a una versione più recente del servizio.

Se l'aggiornamento non è possibile, in alternativa, utilizzare un account di accesso SQL per eseguire processi remoti di R che potrebbero richiedere chiamate ODBC incorporate.

**Si applica a:** SQL Server 2016 R Services Express Edition

### <a name="performance-limits-when-libraries-used-by-sql-server-are-called-from-other-tools"></a>Limiti sulle prestazioni quando vengono chiamate librerie usate da SQL Server da altri strumenti

È possibile chiamare di machine learning librerie che vengono installate per SQL Server da un'applicazione esterna, ad esempio RGui. In questo modo potrebbe essere il modo più semplice per eseguire determinate attività, ad esempio nuovi pacchetti di installazione o esecuzione di test ad hoc su molto brevi esempi di codice. Tuttavia, all'esterno di SQL Server, potrebbero essere limitata sulle prestazioni. 

Ad esempio, anche se si utilizza SQL Server Enterprise Edition, R viene eseguito in modalità a thread singolo quando si esegue il codice R con strumenti esterni. Per ottenere i vantaggi delle prestazioni in SQL Server, avviare una connessione di SQL Server e utilizzare [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) per chiamare il runtime dello script esterno.

In generale, evitare le chiamate di machine learning librerie utilizzate da SQL Server da strumenti esterni. Se è necessario debug R o codice Python, risulta in genere più semplice eseguire questa operazione all'esterno di SQL Server. Per ottenere le stesse librerie in SQL Server, è possibile installare Microsoft R Client, [Machine Learning Server (Standalone) di SQL Server 2017](install/sql-machine-learning-standalone-windows-install.md), o [SQL Server 2016 R Server (Standalone)](install/sql-r-standalone-windows-install.md).

### <a name="sql-server-data-tools-does-not-support-permissions-required-by-external-scripts"></a>SQL Server Data Tools non supporta le autorizzazioni necessarie per gli script esterni

Quando si utilizza Visual Studio o SQL Server Data Tools per pubblicare un progetto di database, se un'entità dispone delle autorizzazioni specifiche per l'esecuzione dello script esterno, si potrebbe ricevere un errore simile alla seguente:

> *Modello TSQL: Errore rilevato durante la progettazione del database. L'autorizzazione non è stato riconosciuto e non è stato importato.*

Il modello DACPAC non supporta attualmente le autorizzazioni utilizzate servizi R e Machine Learning Services, ad esempio GRANT ANY EXTERNAL SCRIPT o EXECUTE ANY EXTERNAL SCRIPT. Questo problema verrà risolto in una versione futura.

In alternativa, eseguire la concessione di ulteriore istruzioni in uno script di post-distribuzione.

### <a name="external-script-execution-is-throttled-due-to-resource-governance-default-values"></a>Esecuzione dello script esterno è limitato a causa di valori predefiniti di governance delle risorse

In Enterprise Edition è possibile usare pool di risorse per gestire processi di script esterni. In alcune build di rilascio anticipato, la memoria massima allocata per i processi di R è il 20%. Pertanto, se il server ha 32 GB di RAM, i file eseguibili di R (RTerm.exe e BxlServer.exe) Impossibile utilizzare un massimo di 6,4 GB in una singola richiesta.

Se si verificano i limiti delle risorse, controllare il valore predefinito. Se il 20% non è sufficiente, vedere la documentazione relativa a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] su come modificare questo valore.

**Si applica a:** R Services SQL Server 2016, Enterprise Edition

## <a name="r-issues"></a>Problemi di R

In questa sezione contiene i problemi noti che sono specifici per l'esecuzione di R in SQL Server, nonché alcuni problemi che sono correlate alle librerie R e strumenti pubblicati da Microsoft, tra cui RevoScaleR.

Per altri problemi noti che potrebbero influire sulle soluzioni R, vedere il [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues) sito.

### <a name="access-denied-warning-when-executing-r-scripts-on-sql-server-in-a-non-default-location"></a>Accesso negato avviso durante l'esecuzione di script R in SQL Server in un percorso non predefinito

Se l'istanza di SQL Server è stato installato in un percorso non predefinito, ad esempio di fuori di `Program Files` cartella, l'avviso ACCESS_DENIED viene generato quando si tenta di eseguire gli script che installa un pacchetto. Esempio:

> *In `normalizePath(path.expand(path), winslash, mustWork)` : percorso [2] = "~ExternalLibraries/R/8/1": accesso negato*

Il motivo è che tenta di leggere il percorso di una funzione di R e non riesce se il gruppo users predefinito **SQLRUserGroup**, non dispone dell'accesso in lettura. L'avviso che viene generato non blocca l'esecuzione dello script R corrente, ma può ricorrere più volte il messaggio di avviso ogni volta che l'utente esegue tutti gli altri script R.

Se è stato installato SQL Server nel percorso predefinito, questo errore si verifica, perché le autorizzazioni di lettura in tutti gli utenti di Windows il `Program Files` cartella.

Questo problema ia risolto in una prossima service release. In alternativa, specificare il gruppo, **SQLRUserGroup**, con accesso in lettura per tutte le cartelle padre di `ExternalLibraries`.

### <a name="serialization-error-between-old-and-new-versions-of-revoscaler"></a>Errore di serializzazione tra le versioni precedenti e nuove di RevoScaleR

Quando si passa un modello utilizzando un formato serializzato a un'istanza remota di SQL Server, si potrebbe ricevere l'errore: 

> *Errore in memDecompress (dati, tipo = decomprimere) Errore interno -3 nel memDecompress(2).*

Questo errore viene generato se è stato salvato il modello utilizzando una versione aggiornata della funzione di serializzazione, [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel), ma l'istanza di SQL Server in cui si esegue la deserializzazione del modello è una versione precedente di APIs RevoScaleR, da SQL Server 2017 CU2 o versioni precedenti.

In alternativa, è possibile aggiornare l'istanza di SQL Server 2017 a CU3 o versioni successive.

L'errore non viene visualizzata se la versione dell'API è lo stesso, o se si sta spostando un modello salvato con una funzione di serializzazione precedente a un server che utilizza una versione più recente dell'API di serializzazione.

In altre parole, è possibile utilizzare la stessa versione di RevoScaleR operazioni di serializzazione e deserializzazione.

### <a name="real-time-scoring-does-not-correctly-handle-the-learningrate-parameter-in-tree-and-forest-models"></a>Punteggi in tempo reale non gestisce correttamente i _learningRate_ parametro nei modelli di albero e foresta

Se si crea un modello utilizzando un albero delle decisioni o un metodo di foresta delle decisioni e specifica la velocità di apprendimento, si potrebbero riscontrare risultati incoerenti quando si utilizza `sp_rxpredict` o SQL `PREDICT` (funzione), invece del `rxPredict`.

La causa è un errore dell'API che modella i processi di serializzazione ed è limitata al `learningRate` parametro: ad esempio, in [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees), o

Questo problema viene risolto in una prossima service release.

### <a name="limitations-on-processor-affinity-for-r-jobs"></a>Limitazioni relative all'affinità processori per i processi R

Nelle build di rilascio iniziale di SQL Server 2016, è possibile impostare l'affinità del processore solo per le CPU nel primo gruppo k. Ad esempio, se il server è un computer 2 socket con due gruppi k, processori soli del primo gruppo k vengono utilizzati per i processi R. La stessa limitazione si applica quando si configura la governance delle risorse per i processi di script R.

Questo problema è stato risolto in SQL Server 2016 Service Pack 1. È consigliabile eseguire l'aggiornamento alla versione più recente del servizio.

**Si applica a:** versione RTM di SQL Server 2016 R Services

### <a name="changes-to-column-types-cannot-be-performed-when-reading-data-in-a-sql-server-compute-context"></a>Non è possibile apportare modifiche ai tipi di colonna durante la lettura di dati in un contesto di calcolo di SQL Server

Se il contesto di calcolo è impostato sull'istanza di SQL Server, non è possibile usare l'argomento _colClasses_ (o altri argomenti simili) per modificare il tipo di dati delle colonne presenti nel codice R.

L'istruzione seguente, ad esempio, causerebbe un errore se la colonna CRSDepTimeStr non fosse già un numero intero:

```R
data <- RxSqlServerData(
  sqlQuery = "SELECT CRSDepTimeStr, ArrDelay  FROM AirlineDemoSmall", 
  connectionString = connectionString, 
  colClasses = c(CRSDepTimeStr = "integer"))
```

In alternativa, è possibile riscrivere la query SQL per l'utilizzo di CAST o CONVERTIRE e presentare i dati in R, utilizzando il tipo di dati corretto. In generale, le prestazioni sono migliori quando si lavora con i dati utilizzando SQL invece la modifica dei dati nel codice R.

**Si applica a:** R Services SQL Server 2016

### <a name="limits-on-size-of-serialized-models"></a>Limiti relativi alle dimensioni dei modelli serializzati

Quando si salva un modello in una tabella di SQL Server, è necessario serializzare il modello e salvarla in un formato binario. In teoria, le dimensioni massime di un modello che può essere archiviato con questo metodo sono 2 GB, ovvero la dimensione massima delle colonne varbinary di SQL Server.

Se è necessario utilizzare i modelli di dimensioni maggiori, sono disponibili soluzioni alternative seguenti:

+ Eseguire i passaggi per ridurre le dimensioni del modello. Alcuni pacchetti R open source includono una grande quantità di informazioni nell'oggetto modello e molte di queste informazioni può essere rimossi per la distribuzione. 
+ Utilizzare funzionalità di selezione per rimuovere colonne non necessarie.
+ Se si utilizza un algoritmo di origine aperti, prendere in considerazione un'implementazione simile utilizzando l'algoritmo corrispondente in MicrosoftML o RevoScaleR. Questi pacchetti sono stati ottimizzati per scenari di distribuzione.
+ Dopo che il modello è stato ragionato e ridurre le dimensioni utilizzando i passaggi precedenti, vedere se il [memCompress](https://www.rdocumentation.org/packages/base/versions/3.4.1/topics/memCompress) funzione in R di base può essere utilizzata per ridurre le dimensioni del modello prima di passarlo a SQL Server. Questa opzione è consigliabile quando il modello è prossimo al limite di 2 GB.
+ Per i modelli di dimensioni maggiori, è possibile utilizzare SQL Server [FileTable](..\relational-databases\blob\filetables-sql-server.md) funzionalità per archiviare i modelli, anziché utilizzare una colonna varbinary.

    Per usare le tabelle Filetable, è necessario aggiungere un'eccezione del firewall, poiché i dati archiviati nelle tabelle Filetable vengono gestiti dal driver del file System di Filestream in SQL Server e le regole firewall predefinite bloccano l'accesso ai file di rete. Per ulteriori informazioni, vedere [abilitare i prerequisiti per la tabella FileTable](../relational-databases/blob/enable-the-prerequisites-for-filetable.md). 

    Dopo avere abilitato FileTable, scrivere il modello, che ottenere un percorso da SQL tramite l'API FileTable e quindi scrivere il modello in tale posizione dal codice. Quando è necessario leggere il modello, ottenere il percorso da SQL, quindi chiamare il modello utilizzando il percorso dallo script. Per ulteriori informazioni, vedere [accesso a tabelle Filetable con API di File di Input-Output](../relational-databases/blob/access-filetables-with-file-input-output-apis.md).

### <a name="avoid-clearing-workspaces-when-you-execute-r-code-in-a-includessnoversionincludesssnoversion-mdmd-compute-context"></a>Non deselezionare le aree di lavoro quando si esegue il codice R in un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contesto di calcolo

Se si utilizza un comando di R per cancellare l'area di lavoro degli oggetti durante l'esecuzione di codice R in un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contesto di calcolo o se si deseleziona l'area di lavoro come parte di uno script R chiamato utilizzando [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), è possibile che venga visualizzato questo errore : *revoScriptConnection oggetto dell'area di lavoro non trovato*

`revoScriptConnection` è un oggetto dell'area di lavoro R che contiene informazioni su una sessione R chiamata da [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Se, tuttavia, il codice R include un comando per cancellare i dati dell'area di lavoro, ad esempio `rm(list=ls()))`, anche tutte le informazioni relative alla sessione e altri oggetti presenti nell'area di lavoro R vengono cancellati.

In alternativa, evitare di cancellazione indiscriminata di variabili e altri oggetti durante l'esecuzione R [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Anche se l'area di lavoro di cancellazione è comune quando si utilizza la console di R, può avere conseguenze impreviste.

* Per eliminare variabili specifiche, utilizzare l'oggetto R `remove` funzione: ad esempio, `remove('name1', 'name2', ...)`
* Se devono essere eliminate più variabili, salvare i nomi delle variabili temporanee in un elenco ed eseguire periodicamente operazioni di Garbage Collection.

### <a name="restrictions-on-data-that-can-be-provided-as-input-to-an-r-script"></a>Limitazioni sui dati che possono essere forniti come input per uno script R

Non è possibile usare in uno script R i tipi seguenti di risultati delle query:

- Dati da una query [!INCLUDE[tsql](../includes/tsql-md.md)] che fa riferimento alle colonne AlwaysEncrypted.
  
- Dati da una query [!INCLUDE[tsql](../includes/tsql-md.md)] che fa riferimento alle colonne mascherate.
  
     Se è necessario usare dati mascherati in uno script R, una possibile soluzione consiste nel creare una copia dei dati in una tabella temporanea e usare invece tali dati.

### <a name="use-of-strings-as-factors-can-lead-to-performance-degradation"></a>Utilizzo di stringhe come fattori che possono determinare un peggioramento delle prestazioni

L'utilizzo di variabili di tipo stringa come fattori possono aumentare notevolmente la quantità di memoria utilizzata per operazioni di R. Si tratta in genere un problema noto con R e sono disponibili molti articoli sull'argomento. Ad esempio, vedere [fattori non sono elementi di primaria importanza in R, per il montaggio di John, in R blogger)](https://www.r-bloggers.com/factors-are-not-first-class-citizens-in-r/) o [stringsAsFactors: una biografia non autorizzato, da Roger Peng](https://simplystatistics.org/2015/07/24/stringsasfactors-an-unauthorized-biography/). 

Anche se il problema non è specifico di SQL Server, possono influire notevolmente sulle prestazioni del codice R eseguire in SQl Server. Sono in genere archiviate come varchar o nvarchar e se una colonna di dati stringa dispone di molti valori univoci, il processo di conversione internamente questi numeri interi e tornare al stringhe da R può anche causare degli errori di allocazione di memoria.

Se non è assolutamente necessario un tipo di dati stringa per le altre operazioni, mapping dei valori di stringa a un valore numerico (intero) i tipi di dati come parte della preparazione dei dati sarebbe utile dal punto di vista delle prestazioni e scalabilità.

Per una descrizione di questo problema e altri suggerimenti, vedere [delle prestazioni per R Services - ottimizzazione dati](r/r-and-data-optimization-r-services.md).

### <a name="arguments-varstokeep-and-varstodrop-are-not-supported-for-sql-server-data-sources"></a>Argomenti *varsToKeep* e *varsToDrop* non sono supportati per le origini dati di SQL Server

Quando si utilizza la funzione rxDataStep per scrivere i risultati in una tabella, usando il *varsToKeep* e *varsToDrop* è un modo pratico per specificare le colonne da includere o escludere come parte dell'operazione. Tuttavia, questi argomenti non sono supportati per le origini dati di SQL Server.

### <a name="limited-support-for-sql-data-types-in-spexecuteexternalscript"></a>Un supporto limitato per i tipi di dati SQL in sp\_eseguire\_esterno\_script

Non tutti i tipi di dati che sono supportati in SQL possono essere utilizzati in R. In alternativa, prendere in considerazione il cast di tipo di dati non supportato su un tipo di dati supportati prima di passare i dati sp\_eseguire\_esterno\_script.

Per ulteriori informazioni, vedere [R librerie e tipi di dati](r/r-libraries-and-data-types.md).

### <a name="possible-string-corruption"></a>Possibile danneggiamento della stringa

Qualsiasi andata e ritorno di dati di tipo stringa [!INCLUDE[tsql](../includes/tsql-md.md)] a R e quindi a [!INCLUDE[tsql](../includes/tsql-md.md)] nuovamente può causare il danneggiamento. Ciò è dovuto alle diverse codifiche usate in R e in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], nonché alle diverse regole di confronto e lingue supportate in R e [!INCLUDE[tsql](../includes/tsql-md.md)]. Qualsiasi stringa in una codifica non ASCII può essere potenzialmente gestita in modo non corretto.

Quando si invia dati di tipo stringa a R, convertirli in una rappresentazione ASCII, se possibile.

Questa limitazione si applica ai dati passati tra SQL Server e Python, nonché. Caratteri multibyte devono essere passati come UTF-8 e archiviati in formato Unicode.

### <a name="only-one-value-of-type-raw-can-be-returned-from-spexecuteexternalscript"></a>Un solo valore di tipo `raw` può essere restituito da `sp_execute_external_script`

Quando un tipo di dati binari (R **raw** tipo di dati) viene restituito da R, il valore deve essere inviato nel frame di dati di output.

Con i dati di tipi diversi da **raw**, è possibile restituire i valori dei parametri e i risultati della stored procedure aggiungendo la parola chiave OUTPUT. Per ulteriori informazioni, vedere [parametri](https://docs.microsoft.com/sql/relational-databases/stored-procedures/parameters).

Se si desidera utilizzare più set di output che includono valori di tipo **raw**, una possibile soluzione alternativa è effettuare più chiamate della stored procedure o il risultato di inviare set nuovamente a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tramite ODBC.

### <a name="loss-of-precision"></a>Perdita di precisione

Poiché [!INCLUDE[tsql](../includes/tsql-md.md)] e R supportano diversi tipi di dati, tipi di dati numerici possono subire una perdita di precisione durante la conversione.

Per ulteriori informazioni sulla conversione implicita del tipo di dati, vedere [R librerie e tipi di dati](r/r-libraries-and-data-types.md).

### <a name="variable-scoping-error-when-you-use-the-transformfunc-parameter"></a>Variabile di errore dell'ambito quando si usa il parametro transformFunc

Per trasformare i dati mentre si modellano, è possibile passare un *transformFunc* argomento in una funzione, ad esempio `rxLinmod` o `rxLogit`. Tuttavia, le chiamate di funzione nidificata possono causare errori di ambito nel contesto di calcolo di SQL Server, anche se le chiamate funzionano correttamente nel contesto di calcolo locale.

> *Il set di dati di esempio per l'analisi non dispone di variabili*

Ad esempio, si supponga che siano state definite due funzioni, `f` e `g`, nell'ambiente globale locale, e `g` chiamate `f`. Nelle chiamate che implica remote o distribuite `g`, la chiamata a `g` potrebbe non riuscire con l'errore, perché `f` non viene trovato, anche se sono stati passati `f` e `g` alla chiamata remota.

Se si verifica questo problema, è possibile risolverlo incorporando la definizione di `f` all'interno della definizione di `g`, in qualsiasi punto prima che `g` chiamerebbe normalmente `f`.

Esempio:

```r
f <- function(x) { 2*x * 3 }
g <- function(y) {
              a <- 10 * y
               f(a)
}
```

Per evitare l'errore, riscrivere la definizione come indicato di seguito:

```r
g <- function(y){
              f <- function(x) { 2*x +3}
              a <- 10 * y
              f(a)
}
```

### <a name="data-import-and-manipulation-using-revoscaler"></a>Importazione e modifica dei dati con RevoScaleR

Quando **varchar** colonne vengono letti da un database, degli spazi vuoti. Per evitare questo problema, racchiudere le stringhe tra caratteri che non siano spazi vuoti.

Quando le funzioni come `rxDataStep` vengono utilizzati per creare le tabelle di database che presentano **varchar** colonne, la larghezza della colonna viene stimata in base a un campione di dati. Se la larghezza può variare, potrebbe essere necessario riempire tutte le stringhe a una lunghezza comune.

L'uso di una trasformazione per modificare il tipo di dati di una variabile non è supportato quando si usano chiamate ripetute a `rxImport` o a `rxTextToXdf` per importare e aggiungere righe, combinando più file di input in un singolo file XDF.

### <a name="limited-support-for-rxexec"></a>Supporto limitato per rxExec

In SQL Server 2016, il `rxExec` funzione che viene fornito per il RevoScaleR pacchetto può essere utilizzato solo in modalità a thread singolo.

Parallelismo per `rxExec` tra più processi è pianificata per una versione futura.

### <a name="increase-the-maximum-parameter-size-to-support-rxgetvarinfo"></a>Aumentare le dimensioni massime di parametro per supportare rxGetVarInfo

Se si utilizzano set di dati con un numero molto elevato di variabili (ad esempio, oltre 40.000), impostare il `max-ppsize` flag all'avvio R per utilizzare le funzioni, ad esempio `rxGetVarInfo`. Il flag `max-ppsize` specifica le dimensioni massime dello stack di protezione dell'indicatore di misura.

Se si utilizza la console di R (ad esempio, RGui.exe o RTerm.exe), è possibile impostare il valore di _max-ppsize_ su 500000 digitando:

```R
R --max-ppsize=500000
```

### <a name="issues-with-the-rxdtree-function"></a>Problemi con la funzione rxDTree

La funzione `rxDTree` attualmente non supporta le trasformazioni nella formula. In particolare, l'uso della sintassi `F()` per la creazione di fattori in tempo reale non è supportata. Tuttavia, i dati numerici vengano automaticamente categorizzati.

I fattori ordinati vengono trattati proprio come i fattori in tutte le funzioni di analisi RevoScaleR eccetto `rxDTree`.

## <a name="python-code-execution-or-python-package-issues"></a>Esecuzione del codice Python o problemi di pacchetti Python

In questa sezione contiene i problemi noti specifici all'esecuzione di Python su SQL Server, nonché i problemi relativi ai pacchetti Python pubblicati da Microsoft, tra cui [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) e [microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).

### <a name="call-to-pretrained-model-fails-if-path-to-model-is-too-long"></a>Chiamata al modello con training preliminare non riesce se il percorso al modello è troppo lungo

Se i modelli con training preliminare è stato installato in una versione preliminare di SQL Server 2017, il percorso completo del file di modello con training potrebbe essere troppo lungo per Python da leggere. Questa limitazione è stato risolto in una versione più recente del servizio.

Esistono diverse potenziali soluzioni alternative: 

+ Quando si installa i modelli con training preliminare, scegliere un percorso personalizzato.
+ Se possibile, installare l'istanza di SQL Server in un percorso di installazione personalizzata con un percorso più breve, ad esempio C:\SQL\MSSQL14. MSSQLSERVER.
+ Utilizzare l'utilità Windows [Fsutil](https://technet.microsoft.com/library/cc788097(v=ws.11).aspx) per creare un collegamento che associa il file del modello a un percorso più breve.
+ Aggiornare alla versione più recente del servizio.

### <a name="error-when-saving-serialized-model-to-sql-server"></a>Errore durante il salvataggio serializzato modello in SQL Server

Quando si passa un modello a un'istanza remota di SQL Server e tentare di leggere il modello binario utilizzando il `rx_unserialize` funzionare in [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package), è possibile che venga visualizzato l'errore: 

> *NameError: rx_unserialize_model' name' non è definito*

Questo errore viene generato se è stato salvato il modello utilizzando una versione aggiornata della funzione di serializzazione, ma l'istanza di SQL Server in cui si esegue la deserializzazione del modello non riconosce l'API di serializzazione.

Per risolvere il problema, aggiornare l'istanza di SQL Server 2017 a CU3 o versioni successive.

### <a name="failure-to-initialize-a-varbinary-variable-causes-an-error-in-bxlserver"></a>Errore di inizializzazione di una variabile di tipo varbinary causa un errore in BxlServer

Se si esegue codice Python in SQL Server utilizzando `sp_execute_external_script`e il codice include variabili di tipo varbinary (max), varchar (max) o tipi simili di output, la variabile deve essere inizializzata o impostare come parte dello script. In caso contrario, il componente di scambio di dati, BxlServer, genera un errore e smette di funzionare.

Questa limitazione verrà risolto in una prossima service release. In alternativa, assicurarsi che la variabile viene inizializzata all'interno dello script Python. Qualsiasi valore valido può essere utilizzato, come negli esempi seguenti:

```sql
declare @b varbinary(max);
exec sp_execute_external_script
  @language = N'Python'
  , @script = N'b = 0x0'
  , @params = N'@b varbinary(max) OUTPUT'
  , @b = @b OUTPUT;
go
```

```sql
declare @b varchar(30);
exec sp_execute_external_script
  @language = N'Python'
  , @script = N' b = ""  '
  , @params = N'@b varchar(30) OUTPUT'
  , @b = @b OUTPUT;
go
```

### <a name="telemetry-warning-on-successful-execution-of-python-code"></a>Avviso di telemetria al completamento dell'esecuzione di codice Python

A partire da SQL Server 2017 CU2, potrebbe essere visualizzato il seguente messaggio anche se il codice Python in caso contrario viene eseguito correttamente:

> *Messaggi STDERR dallo script esterno:*
> **~PYTHON_SERVICES\lib\site-packages\revoscalepy\utils\RxTelemetryLogger*
> *SyntaxWarning: telemetry_state è utilizzato prima della dichiarazione globale*


Questo problema è stato risolto in SQL Server 2017 aggiornamento cumulativo 3 (CU3). 

## <a name="revolution-r-enterprise-and-microsoft-r-open"></a>Revolution R Enterprise e Microsoft R Open

Questa sezione elenca i problemi specifici di connettività R, sviluppo e gli strumenti di prestazioni forniti da Revolution Analitica. Questi strumenti sono stati forniti nelle versioni definitive precedenti di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].

In generale, è consigliabile disinstallare le versioni precedenti e installare la versione più recente di SQL Server o Microsoft R Server.

### <a name="revolution-r-enterprise-is-not-supported"></a>Revolution R Enterprise non è supportata.

L'installazione con le versioni di Revolution R Enterprise side-by [!INCLUDE[rsql_productname_md](../includes/rsql-productname-md.md)] non è supportata.

Se si dispone di una licenza esistente per Revolution R Enterprise, è necessario inserirla in un computer separato da entrambe le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] istanza e qualsiasi workstation che si desidera utilizzare per connettersi al [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] istanza.

Alcune versioni non definitive di [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)] incluso un ambiente di sviluppo R per Windows che è stato creato da Revolution Analitica. Questo strumento non viene più fornito e non è supportato.

Per la compatibilità con [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)], si consiglia di installare Microsoft R Client. [Strumenti R per Visual Studio](https://www.visualstudio.com/vs/rtvs/) e [Visual Studio Code](https://code.visualstudio.com/) supporta anche le soluzioni di Microsoft R.

### <a name="compatibility-issues-with-sqlite-odbc-driver-and-revoscaler"></a>Problemi di compatibilità con il driver ODBC di SQLite e RevoScaleR

Revisione 0.92 del driver ODBC di SQLite è incompatibile con RevoScaleR. Le revisioni 0.88-0.91 e 0.93 e versioni successive sono noti per essere compatibili.

## <a name="see-also"></a>Vedere anche

[Novità di SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)

[Risoluzione dei problemi di apprendimento automatico in SQL Server](machine-learning-troubleshooting-faq.md)
