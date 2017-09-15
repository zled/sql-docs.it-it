---
title: Problemi noti di Machine Learning Services | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 06/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b37a63a-5ff5-478e-bcc2-d13da3ac241c
caps.latest.revision: 53
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 754242a86367b07b98caa9f70f457b70d0840075
ms.openlocfilehash: d5d36a57d73bd0f37d9e8aee6a4d154fb096f375
ms.contentlocale: it-it
ms.lasthandoff: 09/12/2017

---
# <a name="known-issues-in-machine-learning-services"></a>Problemi noti in servizi di Machine Learning

Questo articolo descrive i problemi noti o limitazioni con i componenti di Machine Learning forniti come un'opzione in SQL Server 2016 e SQL Server 2017.

Le informazioni riportate di seguito si applicano a tutte le operazioni seguenti, a meno che non indicato in particolare:

* SQL Server 2016

  - R Services (In-Database)
  - Microsoft R Server (Standalone)

* SQL Server 2017

  - Machine Learning servizi per R (In-Database)
  - Machine Learning Services per Python (In-Database)
  - Machine Learning Server (Standalone)

## <a name="setup-and-configuration-issues"></a>Problemi di installazione e configurazione

Per una descrizione dei processi e domande comuni che riguardano l'installazione iniziale e la configurazione, vedere [domande frequenti sull'installazione e aggiornamento](r/upgrade-and-installation-faq-sql-server-r-services.md). Contiene informazioni sugli aggiornamenti, installazione side-by-side e l'installazione di nuovi componenti di R o Python.

### <a name="unable-to-install-python-components-in-offline-installations-of-sql-server-2017-ctp-20-or-later"></a>Impossibile installare i componenti di Python nelle installazioni non in linea di SQL Server 2017 CTP 2.0 o versione successiva

Se si installa una versione non definitiva di SQL Server 2017 in un computer senza accesso a internet, il programma di installazione potrebbe non riuscire visualizzare la pagina che richiede il percorso dei componenti scaricati Python. In questo caso, è possibile installare la funzionalità di servizi di Machine Learning, ma non i componenti di Python.

Questo problema viene risolto nella versione di rilascio. Se si verifica questo problema, in alternativa, è possibile abilitare temporaneamente l'accesso a internet per la durata dell'installazione. Questa limitazione non è valida per R.

**Si applica a:** 2017 di SQL Server con Python

### <a name="install-the-latest-service-release-to-ensure-compatibility-with-microsoft-r-client"></a>Installare la versione più recente del servizio per garantire la compatibilità con Client di Microsoft R

Se si installa la versione più recente di Microsoft R Client e utilizzarlo per l'esecuzione di R in SQL Server in un contesto di calcolo remoto, è possibile che venga visualizzato un errore simile al seguente:

>*Si esegue 9.x.x versione di Microsoft R Client nel computer, non è compatibile con Microsoft R Server versione 8.x.x. Download and install a compatible version.* (Sul computer è in esecuzione la versione 9.0.0 di Microsoft R, che non è compatibile con Microsoft R Server versione 8.0.3. Scaricare e installare una versione compatibile.)

SQL Server 2016 richiede che le librerie di R nel client corrispondano esattamente le librerie di R nel server. La restrizione è stata rimossa per le versioni successive a R Server 9.0.1. Tuttavia, se si verifica questo errore, verificare la versione delle librerie R che viene utilizzata dal client e server e, se necessario, aggiorna il client in modo che corrisponda alla versione del server.

La versione di R che viene installato con SQL Server R Services viene aggiornata ogni volta che viene installata una versione del servizio SQL Server. Per assicurarsi che siano sempre le versioni aggiornate dei componenti di R, assicurarsi di installare tutti i service pack.

Per garantire la compatibilità con Client di Microsoft R 9.0.0, installare gli aggiornamenti descritti in questo [articolo del supporto tecnico](https://support.microsoft.com/kb/3210262).

Per evitare problemi con i pacchetti R, è inoltre possibile aggiornare la versione delle librerie R che vengono installati sul server, per la modifica ai criteri del ciclo di vita moderna descritto in [nella sezione successiva](#bkmk_sqlbindr). Quando si esegue questa operazione, la versione di R che viene installato con SQL Server viene aggiornata in base alla stessa pianificazione che vengono pubblicati gli aggiornamenti per Microsoft R Server, che garantisce che server e client abbiano sempre le versioni più recenti di Microsoft R.

**Si applica a:** SQL Server 2016 R Services, con R Server versione 9.0.0 o versioni precedenti

### <a name="bkmk_sqlbindr"></a>Avviso di versione non compatibile quando ci si connette a una versione precedente di SQL Server R Services da un client tramite[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]

Quando si esegue codice R in un contesto di calcolo di SQL Server 2016, e una delle due istruzioni seguenti è vera, si potrebbe essere visualizzato un errore simile al seguente:
* R Server (Standalone) è stato installato in un computer client tramite installazione guidata di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].
* Si è installato Microsoft R Server mediante il [separare Windows installer](https://docs.microsoft.com/r-server/install/r-server-install-windows).

>*Si esegue la versione 9.0.0 del Client di Microsoft R nel computer, non è compatibile con la versione 8.0.3 Microsoft R Server. Download and install a compatible version.* (Sul computer è in esecuzione la versione 9.0.0 di Microsoft R, che non è compatibile con Microsoft R Server versione 8.0.3. Scaricare e installare una versione compatibile.)

Lo strumento SqlBindR.exe viene fornito nella Microsoft R Server versione 9.0 per supportare l'aggiornamento delle istanze di SQL Server a una versione compatibile di Analysis Services 9.0. Verrà aggiunto il supporto per l'aggiornamento di istanze di R services 9.0 in SQL Server come parte di una prossima service release. Le versioni di candidati per l'aggiornamento futuro includono SQL Server 2016 RTM CU3 e + SP1 e SQL Server 2017 CTP 1.1.

**Si applica a:** SQL Server 2016 R Services, con R Server versione 9.0.0 o versioni precedenti

### <a name="setup-for-sql-server-2016-service-releases-might-fail-to-install-newer-versions-of-r-components"></a>Durante l'installazione di alcune versioni del servizio SQL Server 2016 è possibile che le versioni più recenti dei componenti R non vengano installate

Quando si installa un aggiornamento cumulativo o installare un service pack per SQL Server 2016 in un computer che non è connesso a internet, l'installazione guidata potrebbe non riuscire a visualizzare il prompt che consente di aggiornare i componenti di R usando il file CAB scaricati. In genere questo errore si verifica quando più componenti sono installati con il motore di database.

In alternativa, è possibile installare la versione del servizio tramite la riga di comando e specificando la */MRCACHEDIRECTORY* argomento, come illustrato in questo esempio, che consente di installare gli aggiornamenti CU1:

`C:\<path to installation media>\SQLServer2016-KB3164674-x64.exe /Action=Patch /IACCEPTROPENLICENSETERMS /MRCACHEDIRECTORY=<path to CU1 CAB files>`

Per ottenere i programmi di installazione più recente, vedere [installare i componenti di machine learning senza accesso a internet](r/installing-ml-components-without-internet-access.md).

**Si applica a:** SQL Server 2016 R Services, con R Server versione 9.0.0 o versioni precedenti

### <a name="launchpad-services-fails-to-start-if-the-version-is-different-from-the-r-version"></a>Servizi di finestra di avvio non viene avviato se la versione è diversa dalla versione di R

Se si installa R services separatamente dal motore di database e le versioni di compilazione sono diverse, si potrebbe vedere il seguente errore nel registro eventi di sistema: 

>_Il servizio Launchpad di SQL Server non è stato possibile avviare a causa del seguente errore: il servizio non ha risposto alla richiesta di avvio o di controllo in modo tempestivo._

Ad esempio, questo errore potrebbe verificarsi se si installa il motore di database utilizzando la versione, applicare una patch per aggiornare il motore di database e quindi aggiungere R services utilizzando la versione di rilascio.

Per evitare questo problema, assicurarsi che tutti i componenti abbiano lo stesso numero di versione. Se si aggiorna un componente, assicurarsi di applicare lo stesso aggiornamento a tutti gli altri componenti installati.

Per visualizzare un elenco dei numeri di versione di R che sono necessari per ogni versione di SQL Server 2016, vedere [componenti installare R senza accesso a internet](r/installing-ml-components-without-internet-access.md).

### <a name="remote-compute-contexts-are-blocked-by-a-firewall-in-sql-server-instances-that-are-running-on-azure-virtual-machines"></a>Contesti di calcolo remoto bloccati da un firewall nelle istanze di SQL Server in esecuzione in macchine virtuali di Azure

Se è stato installato [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] in una macchina virtuale Windows Azure, potrebbe non essere in grado di utilizzare i contesti di calcolo che richiedono l'uso dell'area di lavoro della macchina virtuale. Il motivo è che, per impostazione predefinita, il firewall della macchina virtuale di Azure include una regola che blocca l'accesso alla rete per gli account utente di R locali.

In alternativa, nella macchina virtuale di Azure, aprire **Windows Firewall con sicurezza avanzata**selezionare **regole in uscita**e disabilitare la regola seguente: **bloccare l'accesso di rete per gli account utente locale di R in SQL Server instance MSSQLSERVER**.

### <a name="implied-authentication-in-sqlexpress"></a>Autenticazione implicita in SQLEXPRESS

Quando si eseguono i processi R da una workstation di analisi scientifica dei dati remoti tramite l'autenticazione integrata di Windows, SQL Server utilizza *autenticazione implicita* per generare qualsiasi chiamata ODBC locale che potrebbe essere richiesti dallo script. Questa funzionalità, tuttavia, non funziona nella build RTM di SQL Server Express Edition.

Per risolvere il problema, è consigliabile eseguire l'aggiornamento a una versione più recente del servizio.

In alternativa, è possibile usare un account di accesso SQL per eseguire processi R remoti che potrebbero richiedere chiamate ODBC incorporate.

**Si applica a:** SQL Server 2016 R Services Express Edition

### <a name="performance-limits-when-r-libraries-are-called-from-standalone-r-tools"></a>Limiti sulle prestazioni quando vengono chiamate librerie R da strumenti Standalone R

È possibile chiamare R strumenti e librerie che vengono installate per SQL Server R Services da un'applicazione esterna R, ad esempio RGui. Questa chiamata potrebbe essere utile quando si installano nuovi pacchetti, o quando si eseguono test ad hoc su molto brevi esempi di codice.

Tuttavia, tenere presente che all'esterno di SQL Server, delle prestazioni sarà limitata. Ad esempio, anche se è stata acquistata l'edizione Enterprise di SQL Server, R verrà eseguito in modalità a thread singolo quando si esegue il codice R con strumenti esterni. Le prestazioni sono migliori se si esegue il codice R iniziando una connessione di SQL Server e utilizzando [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), verrà chiamato librerie R per l'utente.

* Evitare di chiamare le librerie di R usati da SQL Server da strumenti esterni di R.
* Se è necessario eseguire codice R esteso nel computer SQL Server con SQL Server, installare un'istanza separata di R, ad esempio, Client di Microsoft R e quindi verificare che gli strumenti di sviluppo R facciano riferimento alla nuova libreria.

Per altre informazioni, vedere [Creare un server R autonomo](r/create-a-standalone-r-server.md).

### <a name="the-r-script-is-throttled-due-to-resource-governance-default-values"></a>Lo script R è limitato a causa di valori predefiniti di governance delle risorse

In Enterprise Edition è possibile usare pool di risorse per gestire processi di script esterni. In alcune build di rilascio anticipato, la memoria massima allocata per i processi di R è il 20%. Pertanto, se il server ha 32 GB di RAM, i file eseguibili di R (RTerm.exe e BxlServer.exe) Impossibile utilizzare un massimo di 6,4 GB in una singola richiesta.

Se si verificano i limiti delle risorse, controllare il valore predefinito. Se il 20% non è sufficiente, vedere la documentazione relativa a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] su come modificare questo valore.

**Si applica a:** R Services SQL Server 2016, Enterprise Edition

## <a name="r-code-execution-and-package-or-function-issues"></a>Esecuzione del codice R e i problemi del pacchetto o una funzione

In questa sezione contiene i problemi noti che sono specifici per l'esecuzione di R in SQL Server, nonché alcuni problemi che sono correlate alle librerie R e strumenti pubblicati da Microsoft, tra cui RevoScaleR.

Per altri problemi noti che potrebbero influire sulle soluzioni R, visitare il [sito Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver-known-issues).

### <a name="limitations-on-processor-affinity-for-r-jobs"></a>Limitazioni relative all'affinità processori per i processi R

Nelle build di rilascio iniziale di SQL Server 2016, è possibile impostare l'affinità del processore solo per le CPU nel primo gruppo k. Ad esempio, se il server è un computer 2 socket con due gruppi k, processori soli del primo gruppo k vengono utilizzati per i processi R. La stessa limitazione si applica quando si configura la governance delle risorse per i processi di script R.

Questo problema è stato risolto in SQL Server 2016 Service Pack 1.

**Si applica a:** versione RTM di SQL Server 2016 R Services

### <a name="changes-to-column-types-cannot-be-performed-when-reading-data-in-a-sql-server-compute-context"></a>Non è possibile apportare modifiche ai tipi di colonna durante la lettura di dati in un contesto di calcolo di SQL Server

Se il contesto di calcolo è impostato sull'istanza di SQL Server, non è possibile usare l'argomento _colClasses_ (o altri argomenti simili) per modificare il tipo di dati delle colonne presenti nel codice R.

L'istruzione seguente, ad esempio, causerebbe un errore se la colonna CRSDepTimeStr non fosse già un numero intero:

~~~~
data <- RxSqlServerData(sqlQuery = "SELECT CRSDepTimeStr, ArrDelay  FROM AirlineDemoSmall",
                                connectionString = connectionString,
                                colClasses = c(CRSDepTimeStr = "integer"))
~~~~

Questo problema verrà risolto in una versione futura.

In alternativa, è possibile riscrivere la query SQL per l'utilizzo di CAST o CONVERTIRE e presentare i dati in R, utilizzando il tipo di dati corretto. In generale, le prestazioni sono migliori quando si lavora con i dati utilizzando SQL invece la modifica dei dati nel codice R.

**Si applica a:** R Services SQL Server 2016

### <a name="avoid-clearing-workspaces-when-you-execute-r-code-in-a-includessnoversionincludesssnoversion-mdmd-compute-context"></a>Non deselezionare le aree di lavoro quando si esegue il codice R in un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contesto di calcolo

Se si utilizza il comando di R per cancellare l'area di lavoro degli oggetti durante l'esecuzione di codice R in un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , contesto di calcolo o se si deseleziona l'area di lavoro come parte di uno script R chiamato utilizzando [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), è possibile che venga visualizzato questo Errore: 

>*oggetto dell'area di lavoro 'revoScriptConnection' non trovato*

`revoScriptConnection` è un oggetto dell'area di lavoro R che contiene informazioni su una sessione R chiamata da [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Se, tuttavia, il codice R include un comando per cancellare i dati dell'area di lavoro, ad esempio `rm(list=ls()))`, anche tutte le informazioni relative alla sessione e altri oggetti presenti nell'area di lavoro R vengono cancellati.

In alternativa, evitare di cancellazione indiscriminata di variabili e altri oggetti durante l'esecuzione R [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Anche se è un'operazione comune nella console R, la cancellazione dei dati dell'area di lavoro può avere conseguenze impreviste.

* Per eliminare variabili specifiche, utilizzare l'oggetto R *rimuovere* funzione: `remove('name1', 'name2', ...)`.
* Se devono essere eliminate più variabili, salvare i nomi delle variabili temporanee in un elenco ed eseguire periodicamente operazioni di Garbage Collection.

### <a name="restrictions-on-data-that-can-be-provided-as-input-to-an-r-script"></a>Limitazioni sui dati che possono essere forniti come input per uno script R

Non è possibile usare in uno script R i tipi seguenti di risultati delle query:

- Dati da una query [!INCLUDE[tsql](../includes/tsql-md.md)] che fa riferimento alle colonne AlwaysEncrypted.
  
- Dati da una query [!INCLUDE[tsql](../includes/tsql-md.md)] che fa riferimento alle colonne mascherate.
  
     Se è necessario usare dati mascherati in uno script R, una possibile soluzione consiste nel creare una copia dei dati in una tabella temporanea e usare invece tali dati.

### <a name="arguments-varstokeep-and-varstodrop-are-not-supported-for-sql-server-data-sources"></a>Argomenti *varsToKeep* e *varsToDrop* non sono supportati per le origini dati di SQL Server

Quando si utilizza la funzione rxDataStep per scrivere i risultati in una tabella, usando il *varsToKeep* e *varsToDrop* è un modo pratico per specificare le colonne da includere o escludere come parte dell'operazione. Questi argomenti non sono attualmente supportati per le origini dati di SQL Server.

### <a name="limited-support-for-sql-data-types-in-spexecuteexternalscript"></a>Supporto limitato per tipi di dati SQL`sp_execute_external_script`

Non tutti i tipi di dati supportati in SQL possono essere usati in R. Come soluzione alternativa, valutare la possibilità di eseguire il cast del tipo di dati non supportato in un tipo di dati supportato prima di passare i dati a sp_execute_external_script.

Per ulteriori informazioni, vedere [tipi di dati e delle librerie R](r/r-libraries-and-data-types.md).

### <a name="possible-string-corruption"></a>Possibile danneggiamento della stringa

Qualsiasi andata e ritorno di dati di tipo stringa [!INCLUDE[tsql](../includes/tsql-md.md)] a R e quindi a [!INCLUDE[tsql](../includes/tsql-md.md)] nuovamente può causare il danneggiamento. Ciò è dovuto alle diverse codifiche usate in R e in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], nonché alle diverse regole di confronto e lingue supportate in R e [!INCLUDE[tsql](../includes/tsql-md.md)]. Qualsiasi stringa in una codifica non ASCII può essere potenzialmente gestita in modo non corretto.

Quando si invia dati di tipo stringa a R, convertirli in una rappresentazione ASCII, se possibile.

### <a name="only-one-value-of-type-raw-can-be-returned-from-spexecuteexternalscript"></a>Un solo valore di tipo `raw` può essere restituito da`sp_execute_external_script`

Quando un tipo di dati binari (il tipo di dati **raw** di R) viene restituito da R, il valore deve essere il valore nel frame dei dati di output.

Il supporto per più output di **raw** verrà aggiunti nelle versioni successive.

Se si desidera utilizzare più set di output, una possibile soluzione alternativa consiste nell'effettuare più chiamate della stored procedure e inviare il risultato set nuovamente a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tramite ODBC.

È possibile restituire i valori dei parametri e i risultati della stored procedure semplicemente aggiungendo la parola chiave OUTPUT. Per ulteriori informazioni, vedere [restituire dati utilizzando i parametri di OUTPUT](https://technet.microsoft.com/library/ms187004.aspx).

### <a name="loss-of-precision"></a>Perdita di precisione

Poiché [!INCLUDE[tsql](../includes/tsql-md.md)] e R supportano diversi tipi di dati, tipi di dati numerici possono subire una perdita di precisione durante la conversione.

Per ulteriori informazioni sulla conversione implicita del tipo di dati, vedere [di lavoro con tipi di dati R](r/r-libraries-and-data-types.md).

### <a name="variable-scoping-error-when-you-use-the-transformfunc-parameter-the-sample-data-set-for-the-analysis-has-no-variables"></a>Variabile di errore dell'ambito quando si usa il parametro transformFunc: *il set di dati di esempio per l'analisi non dispone di variabili*

Per trasformare i dati mentre si modellano, è possibile passare un *transformFunc* argomento in una funzione, ad esempio `rxLinmod` o `rxLogit`. Tuttavia, le chiamate di funzione nidificata possono causare errori di ambito nel contesto di calcolo di SQL Server, anche se le chiamate funzionano correttamente nel contesto di calcolo locale.

Ad esempio, si supponga che siano state definite due funzioni, `f` e `g`, nell'ambiente globale locale, e `g` chiamate `f`. Nelle chiamate remote o distribuite che implicano `g`, la chiamata a `g` potrebbe non riuscire perché non è stato trovato `f` , anche se sono stati passati `f` e `g` alla chiamata remota.

Se si verifica questo problema, è possibile risolverlo incorporando la definizione di `f` all'interno della definizione di `g`, in qualsiasi punto prima che `g` chiamerebbe normalmente `f`.

Esempio:

```  
f <- function(x) { 2*x * 3 }  
g <- function(y) {   
              a <- 10 * y  
               f(a)  
}  
  
```  


Per evitare l'errore, riscrivere la definizione come indicato di seguito:

```  
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

Il parallelismo di `rxExec` tra più processi verrà aggiunto in una versione futura.

### <a name="increase-the-maximum-parameter-size-to-support-rxgetvarinfo"></a>Aumentare le dimensioni massime di parametro per supportare rxGetVarInfo

Se si utilizzano set di dati con un numero molto elevato di variabili (ad esempio, oltre 40.000), impostare il `max-ppsize` flag all'avvio R per utilizzare le funzioni, ad esempio `rxGetVarInfo`. Il flag `max-ppsize` specifica le dimensioni massime dello stack di protezione dell'indicatore di misura.

Se si usa la console di R (ad esempio, in rgui.exe o rterm.exe), è possibile impostare il valore di max-ppsize su 500000 digitando:

```  
R --max-ppsize=500000  
```  
  
Se si utilizza il [!INCLUDE[rsql_developr](../includes/rsql-developr-md.md)] ambiente, è possibile impostare il `max-ppsize` flag effettuando la chiamata seguente al file eseguibile RevoIDE:

```  
RevoIDE.exe /RCommandLine --max-ppsize=500000  
```  

### <a name="issues-with-the-rxdtree-function"></a>Problemi con la funzione rxDTree

La funzione `rxDTree` attualmente non supporta le trasformazioni nella formula. In particolare, l'uso della sintassi `F()` per la creazione di fattori in tempo reale non è supportata. Tuttavia, i dati numerici verranno automaticamente categorizzati.

I fattori ordinati vengono trattati proprio come i fattori in tutte le funzioni di analisi RevoScaleR eccetto `rxDTree`.

## <a name="revolution-r-enterprise-and-microsoft-r-open"></a>Revolution R Enterprise e Microsoft R Open

Questa sezione elenca i problemi specifici di connettività R, sviluppo e gli strumenti di prestazioni forniti da Revolution Analitica. Questi strumenti sono stati forniti nelle versioni definitive precedenti di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. 

In generale, è consigliabile disinstallare le versioni precedenti e installare la versione più recente di SQL Server o Microsoft R Server.

### <a name="running-side-by-side-versions-of-revolution-r-enterprise"></a>Esecuzione side-by-side versioni di Revolution R Enterprise

L'installazione con le versioni di Revolution R Enterprise side-by [!INCLUDE[rsql_productname_md](../includes/rsql-productname-md.md)] non è supportata.

Se si ha una licenza per usare una versione diversa di Revolution R Enterprise, è necessario inserirla in un computer separato sia dall'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sia da qualsiasi workstation che si vuole usare per connettersi all'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .

### <a name="the-use-of-an-r-productivity-environment-is-not-supported"></a>Non è supportato l'utilizzo di un ambiente di produttività di R

Alcune versioni non definitive di [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)] incluso un ambiente di sviluppo R per Windows che è stato creato da Revolution Analitica. Questo strumento non viene più fornito e non è supportata.

Per la compatibilità con [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)], si consiglia di installare Microsoft R Client o Microsoft R Server anziché gli strumenti di Revolution Analitica. [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/) è un altro client consigliato per il supporto di soluzioni Microsoft R.

### <a name="compatibility-issues-with-sqlite-odbc-driver-and-revoscaler"></a>Problemi di compatibilità con il driver ODBC di SQLite e RevoScaleR

Revisione 0.92 del driver ODBC di SQLite è incompatibile con RevoScaleR. Le revisioni 0.88-0.91 e 0.93 e versioni successive sono noti per essere compatibili.

## <a name="see-also"></a>Vedere anche

[Novità di SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)


