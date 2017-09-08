---
title: Problemi noti per i servizi di Machine Learning | Documenti Microsoft
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
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b7b9d53a87490e83f888b47b1cff87191b9693a8
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="known-issues-for-machine-learning-services"></a>Problemi noti relativi a servizi di Machine Learning

In questo argomento descrive problemi noti o limitazioni con i componenti che vengono forniti come un'opzione in SQL Server 2016 e SQL Server 2017 di apprendimento automatico.

A meno che non indicato in particolare, si applica a tutti gli elementi seguenti:

+ SQL Server 2016

  - R Services (In-Database)
  - Microsoft R Server (Standalone)

+ SQL Server 2017

  - Machine Learning servizi per R (In-Database)
  - Machine Learning Services per Python (In-Database)
  - Machine Learning Server (Standalone)

## <a name="setup-and-configuration-issues"></a>Il programma di installazione e problemi di configurazione

Una descrizione di domande comuni e trasformate correlate all'installazione iniziale e di configurazione sono elencati di seguito: [domande frequenti sull'installazione e aggiornamento](r/upgrade-and-installation-faq-sql-server-r-services.md).

Vedere anche in questo articolo per informazioni sugli aggiornamenti, installazione side-by-side e l'installazione di nuovi componenti di R o Python.

### <a name="unable-to-install-python-components-in-in-offline-installs-of-sql-server-2017"></a>Impossibile installare i componenti di Python in installazioni non in linea di SQL Server 2017

Se si installa SQL Server 2017 in un computer senza accesso a Internet, il programma di installazione potrebbe non riuscire visualizzare la pagina che richiede il percorso dei componenti scaricati Python; Pertanto, sarà in grado di installare la funzionalità di servizi di Machine Learning, ma non i componenti di Python.

Questo problema verrà risolto in una versione futura. In alternativa, è possibile abilitare temporaneamente l'accesso a Internet per la durata del programma di installazione. Questa limitazione non è valida per R.

**Si applica a:** 2017 di SQL Server con Python

### <a name="install-latest-service-release-to-ensure-compatibility-with-microsoft-r-client"></a>Installare la versione più recente del servizio per garantire la compatibilità con Microsoft R Client

Se si installa la versione più recente di Microsoft R Client e utilizzarlo per eseguire R contesto di calcolo di SQL Server usando un remoto, è possibile che venga visualizzato un errore simile al seguente:

*Si esegue 9.x.x versione del client di Microsoft R nel computer, non è compatibile con il 8.x.x versione di Microsoft R Server. Download and install a compatible version.* (Sul computer è in esecuzione la versione 9.0.0 di Microsoft R, che non è compatibile con Microsoft R Server versione 8.0.3. Scaricare e installare una versione compatibile.)

SQL Server 2016 è necessario che le librerie di R nel client corrispondano esattamente le librerie di R nel server. Che restrizione è stata rimossa in seguito R Server 9.0.1 per le versioni. Tuttavia, se si verifica questo errore, verificare la versione delle librerie R utilizzato dal client e server, nad se necessario, aggiornare il client in modo che corrisponda alla versione del server.

La versione di R che viene installato con SQL Server R Services viene aggiornata ogni volta che viene installata una versione del servizio SQL Server. Pertanto, per assicurarsi che siano sempre le versioni aggiornate dei componenti di R, è necessario installare tutti i service pack.

Per garantire la compatibilità con Microsoft R Client 9.0.0, è necessario installare gli aggiornamenti descritti in questo [articolo del supporto tecnico](https://support.microsoft.com/kb/3210262).

Per evitare problemi con i pacchetti R, è inoltre possibile aggiornare la versione delle librerie R installati sul server, modificando i criteri del ciclo di vita moderne, come descritto in [in questa sezione](#bkmk_sqlbindr). Quando si esegue questa operazione, la versione di R installato con SQL Server viene aggiornata in base alla stessa pianificazione che vengono pubblicati gli aggiornamenti per Microsoft R Server, verificare che server e client possono avere sempre le versioni più recenti di Microsoft R.

**Si applica a:** SQL Server 2016 R Services, con R Server versione 9.0.0 o versioni precedenti

### <a name="bkmk_sqlbindr"></a>Avviso di una versione incompatibile durante la connessione a una versione precedente di SQL Server R Services da un client usando[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]

Se Microsoft R Server è stato installato in un computer client usando la procedura guidata di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] o il nuovo programma di installazione autonomo di [Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)e si esegue codice R in un contesto di calcolo che usa una versione precedente di SQL Server R Services, è possibile che venga visualizzato un errore simile al seguente:

*Si esegue la versione 9.0.0 del Client di Microsoft R nel computer, non è compatibile con la versione 8.0.3 Microsoft R Server. Download and install a compatible version.* (Sul computer è in esecuzione la versione 9.0.0 di Microsoft R, che non è compatibile con Microsoft R Server versione 8.0.3. Scaricare e installare una versione compatibile.)

In Microsoft R Server 9.0 è incluso lo strumento **SqlBindR.exe**, che consente di aggiornare le istanze di SQL Server a una versione compatibile. Il supporto per l'aggiornamento delle istanze di R Services alla versione 9.0 verrà aggiunto in SQL Server nell'ambito di una versione futura del servizio. Le versioni di candidati per l'aggiornamento futuro includono SQL Server 2016 RTM CU3 + e + SP1 e SQL Server 2017 CTP 1.1.

**Si applica a:** SQL Server 2016 R Services, con R Server versione 9.0.0 o versioni precedenti

### <a name="setup-for-sql-server-2016-service-releases-might-fail-to-install-newer-versions-of-r-components"></a>Durante l'installazione di alcune versioni del servizio SQL Server 2016 è possibile che le versioni più recenti dei componenti R non vengano installate

Quando si installa un aggiornamento cumulativo o un Service Pack per SQL Server 2016 in un computer che non è connesso a Internet, è possibile che durante l'Installazione guidata non venga visualizzato il prompt che consente di aggiornare i componenti R usando i file con estensione cab scaricati. Questo problema si verifica in genere quando vengono installati più componenti insieme al motore di database.

In alternativa, è possibile installare la versione del servizio tramite la riga di comando e specificando la */MRCACHEDIRECTORY* argomento, come illustrato in questo esempio, che consente di installare gli aggiornamenti CU1:

`C:\<path to installation media>\SQLServer2016-KB3164674-x64.exe /Action=Patch /IACCEPTROPENLICENSETERMS /MRCACHEDIRECTORY=<path to CU1 CAB files>`

Per ottenere i programmi di installazione più recente, vedere [installazione dei componenti di apprendimento computer senza accesso a Internet](r/installing-ml-components-without-internet-access.md).

**Si applica a:** SQL Server 2016 R Services, con R Server versione 9.0.0 o versioni precedenti

### <a name="launchpad-services-fails-to-start-if-version-is-different-than-r-version"></a>Il servizio Launchpad non viene avviato se la versione è diversa rispetto a quella di R

Se si installa R Services separatamente dal motore di database e le versioni di compilazione sono diverse, si potrebbe essere visualizzato questo errore nel registro eventi di sistema: _Launchpad di SQL Server il servizio non è stato avviato a causa del seguente errore: il servizio non rispondere alla richiesta di avvio o di controllo in modo tempestivo._

Questo errore può verificarsi se, ad esempio, si installa il motore di database usando la versione finale, quindi si applica una patch per aggiornare il motore di database e infine si aggiunge R Services usando la versione finale.

Per evitare questo problema, assicurarsi che tutti i componenti abbiano lo stesso numero di versione. Se si aggiorna un componente, assicurarsi di applicare lo stesso aggiornamento a tutti gli altri componenti installati.

Per visualizzare un elenco dei numeri di versione R necessari per ogni versione di SQL Server 2016, vedere [Installazione dei componenti R senza accesso a Internet](r/installing-ml-components-without-internet-access.md).

### <a name="remote-compute-contexts-blocked-by-firewall-in-sql-server-instances-running-on-azure-virtual-machines"></a>Contesti di calcolo remoto bloccati dal firewall nelle istanze di SQL Server in esecuzione su macchine virtuali di Azure

Se è stato installato [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] in una macchina virtuale di Windows Azure, potrebbe non essere possibile usare contesti di calcolo che richiedono l'uso dell'area di lavoro della macchina virtuale. Il motivo è che, per impostazione predefinita, il firewall della macchina virtuale di Azure include una regola che blocca l'accesso alla rete per gli account utente di R locali.

In alternativa, nella macchina virtuale di Azure aprire **Windows Firewall con sicurezza avanzata**, selezionare **Regole in uscita**e disabilitare la regola seguente: "Block network access for R local user accounts in SQL Server instance MSSQLSERVER".

### <a name="implied-authentication-in-sqlexpress"></a>Autenticazione implicita in SQLEXPRESS

Quando si eseguono processi R da una workstation remota per l'analisi scientifica dei dati tramite l'autenticazione integrata di Windows, SQL Server usa l' *autenticazione implicita* per generare eventuali chiamate ODBC locali richieste dallo script. Questa funzionalità, tuttavia, non funziona nella build RTM di SQL Server Express Edition.

Per risolvere il problema, è consigliabile eseguire l'aggiornamento a una versione più recente del servizio.

In alternativa, è possibile usare un account di accesso SQL per eseguire processi R remoti che potrebbero richiedere chiamate ODBC incorporate.

**Si applica a:** SQL Server 2016 R Services Express Edition

### <a name="performance-limits-when-r-libraries-are-called-from-standalone-r-tools"></a>Prestazioni limitano quando vengono chiamate librerie R dagli strumenti di R autonomo

È possibile chiamare R strumenti e librerie che vengono installate per SQL Server R Services da un'applicazione esterna R, ad esempio RGui. Questo potrebbe essere utile quando si nuovi pacchetti di installazione o esecuzione di test ad hoc su molto brevi esempi di codice.

Tuttavia, tenere presente che all'esterno di SQL Server, delle prestazioni sarà limitata. Ad esempio, anche se è stata acquistata l'edizione Enterprise di SQL Server, R verrà eseguito in modalità a thread singolo quando si esegue codice R con strumenti esterni. Le prestazioni sono migliori se si esegue il codice R iniziando una connessione di SQL Server e utilizzando [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), verrà chiamato librerie R per l'utente.

+ Evitare di chiamare da strumenti R esterni le librerie R usate da SQL Server.
+ Se è necessario eseguire codice R esteso nel computer SQL Server con SQL server, installare un'istanza separata di R, ad esempio Microsoft R Client e quindi verificare che gli strumenti di sviluppo R facciano riferimento alla nuova libreria.

Per altre informazioni, vedere [Creare un server R autonomo](r/create-a-standalone-r-server.md).

### <a name="r-script-throttled-due-to-resource-governance-default-values"></a>Script R limitato a causa di valori predefiniti di governance delle risorse

In Enterprise Edition è possibile usare pool di risorse per gestire processi di script esterni. In alcune build di rilascio anticipato, la memoria massima allocata per i processi di R è 20%. Di conseguenza, se il server ha 32 GB di RAM, i file eseguibili di R (RTerm.exe e BxlServer.exe) non possono usare più di 6,4 GB in un'unica richiesta.

In caso di limitazioni relative alle risorse, controllare il valore predefinito corrente e, se il 20% non è sufficiente, vedere la documentazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] su come modificare questo valore.

**Si applica a:** R Services SQL Server 2016, Enterprise Edition

## <a name="r-code-execution-and-package-or-function-issues"></a>Esecuzione del codice R e pacchetti o problemi (funzione)

In questa sezione contiene i problemi noti che sono specifici per l'esecuzione di R in SQL Server, nonché alcuni problemi relativi alle raccolte di R e strumenti pubblicati da Microsoft, tra cui RevoScaleR.

Per altri problemi noti che potrebbero influire sulle soluzioni R, vedere il sito di Microsoft R Server: [problemi noti con Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver-known-issues)

### <a name="limitations-on-processor-affinity-for-r-jobs"></a>Limitazioni relative all'affinità processori per i processi R

Nelle build di rilascio iniziale di SQL Server 2016, è possibile impostare l'affinità del processore solo per le CPU nel primo gruppo k. Se, ad esempio, il server è costituito da un computer a 2 socket con 2 gruppi K, per i processi R verranno usati solo processori appartenenti al primo gruppo K. La stessa limitazione si applica quando si configura la governance delle risorse per processi di script R.

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

Come soluzione alternativa, è possibile riscrivere la query SQL in modo da usare CAST o CONVERT e presentare i dati in R usando il tipo di dati corretto. In generale, per ottenere prestazioni ottimali è consigliabile eseguire le operazioni sui dati usando SQL anziché modificando i dati nel codice R.

**Si applica a:** R Services SQL Server 2016

### <a name="avoid-clearing-workspaces-when-executing-r-code-in-a-includessnoversionincludesssnoversion-mdmd-compute-context"></a>Non cancellare i dati delle aree di lavoro durante l'esecuzione di codice R in un contesto di calcolo di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]

Se si usa il comando R per rimuovere oggetti dall'area di lavoro durante l'esecuzione di codice R in un contesto di calcolo di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] oppure si cancellano i dati dell'area di lavoro nell'ambito di uno script R chiamato tramite [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), è possibile che venga visualizzato questo errore: *workspace object 'revoScriptConnection' not found*(oggetto 'revoScriptConnection' dell'area di lavoro non trovato).

`revoScriptConnection` è un oggetto dell'area di lavoro R che contiene informazioni su una sessione R chiamata da [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Se, tuttavia, il codice R include un comando per cancellare i dati dell'area di lavoro, ad esempio `rm(list=ls()))`, anche tutte le informazioni relative alla sessione e altri oggetti presenti nell'area di lavoro R vengono cancellati.

Come soluzione alternativa, evitare di cancellare in modo indiscriminato variabili e altri oggetti durante l'esecuzione di R in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Anche se è un'operazione comune nella console R, la cancellazione dei dati dell'area di lavoro può avere conseguenze impreviste.

+ Per eliminare variabili specifiche, usare la funzione *remove* di R: `remove('name1', 'name2', ...)`
+ Se devono essere eliminate più variabili, salvare i nomi delle variabili temporanee in un elenco ed eseguire periodicamente operazioni di Garbage Collection.

### <a name="restrictions-on-data-that-can-be-provided-as-input-to-an-r-script"></a>Limitazioni sui dati che possono essere forniti come input per uno script R

Non è possibile usare in uno script R i tipi seguenti di risultati delle query:

- Dati da una query [!INCLUDE[tsql](../includes/tsql-md.md)] che fa riferimento alle colonne AlwaysEncrypted.
  
- Dati da una query [!INCLUDE[tsql](../includes/tsql-md.md)] che fa riferimento alle colonne mascherate.
  
     Se è necessario usare dati mascherati in uno script R, una possibile soluzione consiste nel creare una copia dei dati in una tabella temporanea e usare invece tali dati.

### <a name="arguments-varstokeep-and-varstodrop-not-supported-for-sql-server-data-sources"></a>Argomenti *varsToKeep* e *varsToDrop* non supportato per le origini dati di SQL Server

Quando si utilizza la funzione rxDataStep per scrivere i risultati in una tabella, usando il *varsToKeep* e *varsToDrop* è un modo pratico per specificare le colonne da includere o escludere come parte dell'operazione. Questi argomenti non sono attualmente supportati per le origini dati di SQL Server.

Questa limitazione verrà rimossa in una versione successiva.

### <a name="limited-support-for-sql-data-types-in-spexecuteexternalscript"></a>Supporto limitato per tipi di dati SQL`sp_execute_external_script`

Non tutti i tipi di dati supportati in SQL possono essere usati in R. Come soluzione alternativa, valutare la possibilità di eseguire il cast del tipo di dati non supportato in un tipo di dati supportato prima di passare i dati a sp_execute_external_script.

Per ulteriori informazioni, vedere [tipi di dati e delle librerie R](r/r-libraries-and-data-types.md).

### <a name="possible-string-corruption"></a>Possibile danneggiamento della stringa

Qualsiasi round trip dei dati di stringa da [!INCLUDE[tsql](../includes/tsql-md.md)] a R e quindi di nuovo a [!INCLUDE[tsql](../includes/tsql-md.md)] può causarne il danneggiamento. Ciò è dovuto alle diverse codifiche usate in R e in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], nonché alle diverse regole di confronto e lingue supportate in R e [!INCLUDE[tsql](../includes/tsql-md.md)]. Qualsiasi stringa in una codifica non ASCII può essere potenzialmente gestita in modo non corretto.

Quando si inviano i dati di stringa a R, convertirli in una rappresentazione ASCII, se possibile.

### <a name="only-one-value-of-type-raw-can-be-returned-from-spexecuteexternalscript"></a>Un solo valore di tipo `raw` può essere restituito da`sp_execute_external_script`

Quando un tipo di dati binari (il tipo di dati **raw** di R) viene restituito da R, il valore deve essere il valore nel frame dei dati di output.

Il supporto per più output di **raw** verrà aggiunti nelle versioni successive.

Una possibile soluzione alternativa se si vogliono più set di output consiste nell'effettuare più chiamate della stored procedure e inviare i set di risultati nuovamente a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] usando ODBC.

Tenere presente che è possibile restituire i valori dei parametri insieme ai risultati della stored procedure semplicemente aggiungendo la parola chiave OUTPUT. Per altre informazioni, vedere [Restituzione di dati utilizzando i parametri OUTPUT](https://technet.microsoft.com/library/ms187004.aspx).

### <a name="loss-of-precision"></a>Perdita di precisione

[!INCLUDE[tsql](../includes/tsql-md.md)] e R supportano diversi tipi di dati. Pertanto, i tipi di dati numerici possono subire una perdita di precisione durante la conversione.

Per ulteriori informazioni sulla conversione implicita dei tipi di dati, vedere [Working with R Data Types](r/r-libraries-and-data-types.md).

### <a name="variable-scoping-error-the-sample-data-set-for-the-analysis-has-no-variables-when-using-the-transformfunc-parameter"></a>Errore dell'ambito di variabile "The sample data set for the analysis has no variables" quando si usa il parametro transformFunc

È possibile passare un argomento *transfomFunc* in una funzione, ad esempio `rxLinmod` o `rxLogit` to transfom the data while modelling. Tuttavia, le chiamate di funzione nidificata possono causare errori di ambito nel contesto di calcolo di SQL Server, anche se le chiamate funzionano correttamente nel contesto di calcolo locale.

Ad esempio, si supponga che siano state definite due funzioni `f` e `g` nell'ambiente globale locale, e che `g` chiami `f`. Nelle chiamate remote o distribuite che implicano `g`, la chiamata a `g` potrebbe non riuscire perché non è stato trovato `f` , anche se sono stati passati `f` e `g` alla chiamata remota.

Se si verifica questo problema, è possibile risolverlo incorporando la definizione di `f` all'interno della definizione di `g`, in qualsiasi punto prima che `g` chiamerebbe normalmente `f`.

Esempio:

```  
f <- function(x) { 2*x + 3 }  
g <- function(y) {   
              a <- 10 * y  
               f(a)  
}  
  
```  


Per evitare l'errore, riscrivere come indicato di seguito:

```  
g <- function(y){  
              f <- function(x) { 2*x +3}  
              a <- 10 * y  
              f(a)  
}  
  
```  

### <a name="data-import-and-manipulation-using-revoscaler"></a>Importazione e modifica dei dati con RevoScaleR

Durante la lettura delle colonne di **varchar** da un database verrà rimosso lo spazio vuoto. Per evitare questo problema, racchiudere le stringhe tra caratteri che non siano spazi vuoti.

Quando si usano funzioni come `rxDataStep` per creare tabelle di database con le colonne di **varchar** , la larghezza della colonna viene stimata in base a un campione di dati. Se la larghezza può variare, potrebbe essere necessario riempire tutte le stringhe a una lunghezza comune.

L'uso di una trasformazione per modificare il tipo di dati di una variabile non è supportato quando si usano chiamate ripetute a `rxImport` o a `rxTextToXdf` per importare e aggiungere righe, combinando più file di input in un singolo file XDF.

### <a name="limited-support-for-rxexec"></a>Supporto limitato per rxExec

In SQL Server 2016, il `rxExec` funzione fornita dal pacchetto RevoScaleR può essere utilizzata solo in modalità a thread singolo.

Il parallelismo di `rxExec` tra più processi verrà aggiunto in una versione futura.

### <a name="increase-maximum-parameter-size-to-support-rxgetvarinfo"></a>Aumentare la dimensione massima dei parametri per supportare rxGetVarInfo

Se si usano set di dati con un numero molto elevato di variabili (ad esempio, oltre 40.000), è necessario impostare il flag `max-ppsize` all'avvio R per poter usare le funzioni, ad esempio `rxGetVarInfo`.  Il flag `max-ppsize` specifica le dimensioni massime dello stack di protezione dell'indicatore di misura.

Se si usa la console di R (ad esempio, in rgui.exe o rterm.exe), è possibile impostare il valore di max-ppsize su 500000 digitando:

```  
R --max-ppsize=500000  
```  
  
Se si usa l'ambiente [!INCLUDE[rsql_developr](../includes/rsql-developr-md.md)] , è possibile impostare il flag `max-ppsize` eseguendo questa chiamata al file eseguibile RevoIDE:

```  
RevoIDE.exe /RCommandLine --max-ppsize=500000  
```  

### <a name="issues-with-the-rxdtree-function"></a>Problemi con la funzione rxDTree

La funzione `rxDTree` attualmente non supporta le trasformazioni nella formula. In particolare, l'uso della sintassi `F()` per la creazione di fattori in tempo reale non è supportata. Tuttavia, i dati numerici verranno automaticamente categorizzati.

I fattori ordinati vengono trattati proprio come i fattori in tutte le funzioni di analisi RevoScaleR eccetto `rxDTree`.

## <a name="revolution-r-enterprise-and-microsoft-r-open"></a>Revolution R Enterprise e Microsoft R Open

Questa sezione elenca i problemi specifici degli strumenti per le prestazioni, lo sviluppo e la connettività di R forniti da Revolution Analytics. Questi strumenti erano inclusi in precedenti versioni non definitive di  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. 

In generale, è consigliabile disinstallare le versioni precedenti e installare la versione più recente di SQL Server o Microsoft R Server.

### <a name="running-side-by-side-versions-of-revolution-r-enterprise"></a>Esecuzione di versioni affiancate di Revolution R Enterprise

L'installazione side-by-side di Revolution R Enterprise con qualsiasi altra versione di [!INCLUDE[rsql_productname_md](../includes/rsql-productname-md.md)] non è supportata.

Se si ha una licenza per usare una versione diversa di Revolution R Enterprise, è necessario inserirla in un computer separato sia dall'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sia da qualsiasi workstation che si vuole usare per connettersi all'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .

### <a name="use-of-r-productivity-environment-not-supported"></a>Uso di R Productivity Environment non supportato

Alcune versioni non definitive di [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)] includono un ambiente di sviluppo R per Windows creato da Revolution Analytics. Questo strumento non viene più fornito e non è supportato.

Per la compatibilità con [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)], si consiglia di installare Microsoft R Client o Microsoft R Server anziché gli strumenti di Revolution Analitica. [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/) è un altro client consigliato per il supporto di soluzioni Microsoft R.

### <a name="compatibility-issues-with-sqlite-odbc-driver-and-revoscaler"></a>Problemi di compatibilità con il driver ODBC di SQLite e RevoScaleR

La revisione 0.92 del driver ODBC di SQLite è incompatibile con RevoScaleR; le revisioni 0.88-0.91 e 0.93 e le versioni successive risultano compatibili.

## <a name="see-also"></a>Vedere anche

[Novità di SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)


