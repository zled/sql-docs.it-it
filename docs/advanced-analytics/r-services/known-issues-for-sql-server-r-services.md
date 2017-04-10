---
title: "Problemi noti per SQL Server R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b37a63a-5ff5-478e-bcc2-d13da3ac241c
caps.latest.revision: 52
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 49
---
# Problemi noti per SQL Server R Services
  Questo argomento descrive le limitazioni e i problemi relativi a [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] e ai componenti correlati in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].  
  
> [!NOTE]
> Altri problemi relativi alle attività iniziali di installazione e configurazione sono elencati qui: [Domande frequenti sull'installazione e sull'aggiornamento](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md).  
  
## <a name="r-services-in-database"></a>R Services (In-Database)  
 Questa sezione elenca i problemi specifici della funzionalità del motore di database che supporta l'integrazione di R.  

### <a name="install-latest-service-release-to-ensure-compatibility-with-microsoft-r-client"></a>Installare la versione più recente del servizio per garantire la compatibilità con Microsoft R Client

Se si installa la versione più recente di Microsoft R Client e si usa tale versione per eseguire R su SQL Server tramite un contesto di calcolo remoto, è possibile che venga visualizzato l'errore seguente:

*You are running version 9.0.0 of Microsoft R client on your computer, which is incompatible with the Microsoft R server version 8.0.3. Download and install a compatible version.* (Sul computer è in esecuzione la versione 9.0.0 di Microsoft R, che non è compatibile con Microsoft R Server versione 8.0.3. Scaricare e installare una versione compatibile.)

In genere, la versione di R installata con SQL Server R Services viene aggiornata al momento della pubblicazione di nuove versioni del servizio. Per assicurarsi di avere sempre le versioni più aggiornate dei componenti R, installare tutti i Service Pack. Per garantire la compatibilità con Microsoft R Client 9.0.0, è necessario installare gli aggiornamenti descritti in questo [articolo del supporto tecnico](https://support.microsoft.com/kb/3210262). 
  
### <a name="new-license-agreement-for-r-components-required-for-unattended-installs"></a>Nuovo contratto di licenza per i componenti R necessari per le installazioni automatiche  
 Se si usa la riga di comando per installare un'istanza di SQL Server in cui è installato [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], è necessario modificare la riga di comando in modo da usare il nuovo parametro del contratto di licenza, */IACCEPTROPENLICENSEAGREEMENT*. Il mancato uso dell'argomento corretto può causare un errore di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="warning-of-incompatible-version-when-connecting-to-older-version-of-sql-server--r-services-from-a-client-using-includesssqlv14mdtokensqlv14sssqlv14mdmd"></a>Avviso di versione non compatibile quando ci si connette a una versione precedente di SQL Server R Services da un client che usa [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 

Se Microsoft R Server è stato installato in un computer client usando la procedura guidata di [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] o il nuovo programma di installazione autonomo di [Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver-install-windows) e si esegue codice R in un contesto di calcolo che usa una versione precedente di SQL Server R Services, è possibile che venga visualizzato un errore simile al seguente:

*You are running version 9.0.0 of Microsoft R Client on your computer, which is incompatible with the Microsoft R Server version 8.0.3. Download and install a compatible version.* (Sul computer è in esecuzione la versione 9.0.0 di Microsoft R, che non è compatibile con Microsoft R Server versione 8.0.3. Scaricare e installare una versione compatibile.)

In Microsoft R Server 9.0 è incluso lo strumento **SqlBindR.exe**, che consente di aggiornare le istanze di SQL Server a una versione compatibile. Il supporto per l'aggiornamento delle istanze di R Services alla versione 9.0 verrà aggiunto in SQL Server nell'ambito di una versione futura del servizio. Le versioni in cui probabilmente sarà supportato l'aggiornamento includono SQL Server 2016 RTM CU3+ e SP1+ e SQL Server vNext CTP 1.1. 

### <a name="setup-for-sql-server-2016-service-releases-might-fail-to-install-newer-versions-of-r-components"></a>Durante l'installazione di alcune versioni del servizio SQL Server 2016 è possibile che le versioni più recenti dei componenti R non vengano installate

Quando si installa un aggiornamento cumulativo o un Service Pack per SQL Server 2016 in un computer che non è connesso a Internet, è possibile che durante l'Installazione guidata non venga visualizzato il prompt che consente di aggiornare i componenti R usando i file con estensione cab scaricati. Questo problema si verifica in genere quando vengono installati più componenti insieme al motore di database.
 
Come soluzione alternativa, è possibile installare la versione del servizio usando la riga di comando e specificando l'argomento /MRCACHEDIRECTORY, come illustrato in questo esempio relativo a CU1: 

`C:\<path to installation media>\SQLServer2016-KB3164674-x64.exe /Action=Patch /IACCEPTROPENLICENSETERMS /MRCACHEDIRECTORY=<path to CU1 CAB files>`

Per ottenere i file con estensione cab più recenti, vedere [Installazione dei componenti R senza accesso a Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md).

### <a name="windows-group-created-for-launchpad-must-have-an-account-in-the-sql-server-instance"></a>Il gruppo di Windows creato per LaunchPad deve avere un account nell'istanza di SQL Server
 Durante l'installazione di SQL Server R Services viene creato un gruppo di utenti Windows con il nome predefinito **SQLRUsers**, che viene usato dal servizio Trusted Launchpad per eseguire processi R. Se si devono eseguire processi R da un client remoto usando l'autenticazione integrata di Windows, è necessario concedere a questo gruppo di utenti Windows l'autorizzazione ad accedere all'istanza di SQL Server in cui è abilitato R.

In un ambiente in cui il gruppo **SQLRUsers** non ha questa autorizzazione, è possibile che vengano visualizzati gli errori seguenti:  
  
-   Quando si prova a eseguire gli script R:  
  
     *Non è stato possibile avviare il runtime per lo script 'R'. Verificare la configurazione del runtime di 'R'.*  
  
     *Si è verificato un errore dello script esterno. Non è stato possibile avviare il runtime.*  
  
-   Errori generati dal servizio [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] :  
  
     *Failed to initialize the launcher RLauncher.dll* (Non è stato possibile inizializzare l'utilità di avvio RLauncher.dll)  
  
     *No launcher dlls were registered!* (Non è stata registrata alcuna DLL dell'utilità di avvio.)  
  
-   I registri di sicurezza indicano che non è stato possibile accedere con l'account NT SERVICE\MSSQLLAUNCHPAD.  
 
> [!NOTE]
> Se si eseguono processi R in SQL Server Management Studio usando la memoria condivisa, è possibile che questa limitazione non venga applicata finché il processo R non usa una chiamata ODBC incorporata. 
> 
> Questo espediente non è necessario se si usano account di accesso SQL dalla workstation remota.

### <a name="launchpad-services-fails-to-start-if-version-is-different-than-r-version"></a>Il servizio Launchpad non viene avviato se la versione è diversa rispetto a quella di R
Se si installa R Services separatamente dal motore di database e le versioni sono diverse, è possibile che nel registro eventi di sistema venga visualizzato questo errore: _Il servizio SQL Server Launchpad non è stato avviato per il seguente errore: Il servizio non ha risposto alla richiesta di avvio o controllo nel tempo previsto._

Questo errore può verificarsi se, ad esempio, si installa il motore di database usando la versione finale, quindi si applica una patch per aggiornare il motore di database e infine si aggiunge R Services usando la versione finale.

Per evitare questo problema, assicurarsi che tutti i componenti abbiano lo stesso numero di versione. Se si aggiorna un componente, assicurarsi di applicare lo stesso aggiornamento a tutti gli altri componenti installati.

Per visualizzare un elenco dei numeri di versione R necessari per ogni versione di SQL Server 2016, vedere [Installazione dei componenti R senza accesso a Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md).


### <a name="service-account-for-launchpad-requires-permission-replace-process-level-token"></a>L'account del servizio per LaunchPad richiede l'autorizzazione Sostituzione di token a livello di processo
 Durante l'installazione di SQL Server R Services, il servizio Trusted Launchpad viene avviato con l'account NT Service\MSSQLLaunchpad, che per impostazione predefinita dispone delle autorizzazioni necessarie. Se, tuttavia, si usa un account diverso o si modificano i privilegi associati all'account, è possibile che il servizio Launchpad non venga avviato.
 
 Per assicurarsi che l'account del servizio Launchpad possa eseguire l'accesso, assegnare all'account il privilegio `Replace Process Level Token`. Per altre informazioni, vedere [Replace a process level token](https://technet.microsoft.com/itpro/windows/keep-secure/replace-a-process-level-token) (Sostituzione di token a livello di processo).

### <a name="remote-compute-contexts-blocked-by-firewall-in-sql-server-instances-running-on-azure-virtual-machines"></a>Contesti di calcolo remoto bloccati dal firewall nelle istanze di SQL Server in esecuzione su macchine virtuali di Azure  
 Se è stato installato [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in una macchina virtuale di Windows Azure, potrebbe non essere possibile usare contesti di calcolo che richiedono l'uso dell'area di lavoro della macchina virtuale. Il motivo è che, per impostazione predefinita, il firewall della macchina virtuale di Azure include una regola che blocca l'accesso alla rete per gli account utente di R locali.  
  
 In alternativa, nella macchina virtuale di Azure aprire **Windows Firewall con sicurezza avanzata**, selezionare **Regole in uscita**e disabilitare la regola seguente: "Block network access for R local user accounts in SQL Server instance MSSQLSERVER".  
  
### <a name="implied-authentication-in-sqlexpress"></a>Autenticazione implicita in SQLEXPRESS
Quando si eseguono processi R da una workstation remota per l'analisi scientifica dei dati tramite l'autenticazione integrata di Windows, SQL Server usa l'*autenticazione implicita* per generare eventuali chiamate ODBC locali richieste dallo script. Questa funzionalità, tuttavia, non funziona nella build RTM di SQL Server Express Edition. 

Per risolvere il problema, è consigliabile eseguire l'aggiornamento a una versione più recente del servizio.

In alternativa, è possibile usare un account di accesso SQL per eseguire processi R remoti che potrebbero richiedere chiamate ODBC incorporate. 

### <a name="limitations-on-processor-affinity-for-r-jobs"></a>Limitazioni relative all'affinità processori per i processi R 
 
Nella build RTM di SQL Server 2016 è possibile impostare l'affinità processori solo per le CPU presenti nel primo gruppo K. Se, ad esempio, il server è costituito da un computer a 2 socket con 2 gruppi K, per i processi R verranno usati solo processori appartenenti al primo gruppo K. La stessa limitazione si applica quando si configura la governance delle risorse per processi di script R.

Questo problema è stato risolto in SQL Server 2016 Service Pack 1.

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
  
### <a name="resource-governance-default-values"></a>Valori predefiniti per la governance delle risorse  
In Enterprise Edition è possibile usare pool di risorse per gestire processi di script esterni. In alcune build non è possibile allocare ai processi R più del 20% della memoria complessiva. Di conseguenza, se il server ha 32 GB di RAM, i file eseguibili di R (RTerm.exe e BxlServer.exe) non possono usare più di 6,4 GB in un'unica richiesta. 

In caso di limitazioni relative alle risorse, controllare il valore predefinito corrente e, se il 20% non è sufficiente, vedere la documentazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] su come modificare questo valore.  

### <a name="avoid-clearing-workspaces-when-executing-r-code-in-a-includessnoversiontokenssnoversionmdmd-compute-context"></a>Non cancellare i dati delle aree di lavoro durante l'esecuzione di codice R in un contesto di calcolo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Se si usa il comando R per rimuovere oggetti dall'area di lavoro durante l'esecuzione di codice R in un contesto di calcolo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oppure si cancellano i dati dell'area di lavoro nell'ambito di uno script R chiamato tramite [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), è possibile che venga visualizzato questo errore: *workspace object 'revoScriptConnection' not found* (oggetto 'revoScriptConnection' dell'area di lavoro non trovato).

`revoScriptConnection` è un oggetto dell'area di lavoro R che contiene informazioni su una sessione R chiamata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se, tuttavia, il codice R include un comando per cancellare i dati dell'area di lavoro, ad esempio `rm(list=ls()))`, anche tutte le informazioni relative alla sessione e altri oggetti presenti nell'area di lavoro R vengono cancellati.

Come soluzione alternativa, evitare di cancellare in modo indiscriminato variabili e altri oggetti durante l'esecuzione di R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Anche se è un'operazione comune nella console R, la cancellazione dei dati dell'area di lavoro può avere conseguenze impreviste. 

+ Per eliminare variabili specifiche, usare la funzione *remove* di R: `remove('name1', 'name2', ...)` 
+ Se devono essere eliminate più variabili, salvare i nomi delle variabili temporanee in un elenco ed eseguire periodicamente operazioni di Garbage Collection. 
   
### <a name="restrictions-on-data-that-can-be-provided-as-input-to-an-r-script"></a>Limitazioni sui dati che possono essere forniti come input per uno script R  
 Non è possibile usare in uno script R i tipi seguenti di risultati delle query:  
  
-   Dati da una query [!INCLUDE[tsql](../../includes/tsql-md.md)] che fa riferimento alle colonne AlwaysEncrypted.  
  
-   Dati da una query [!INCLUDE[tsql](../../includes/tsql-md.md)] che fa riferimento alle colonne mascherate.  
  
     Se è necessario usare dati mascherati in uno script R, una possibile soluzione consiste nel creare una copia dei dati in una tabella temporanea e usare invece tali dati.  
   
  
## <a name="microsoft-r-server-standalone"></a>Microsoft R Server (Standalone)  
 Questa sezione elenca i problemi specifici della versione Standalone di Microsoft R Server. 
  
### <a name="multiple-r-libraries-and-executables-are-installed-if-you-install-both-standalone-and-in-database"></a>Se si installano entrambe le versioni Standalone e In-Database, è possibile che vengano installati più file eseguibili e librerie di R  
 Il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] include l'opzione di installazione Microsoft R Server (Standalone). Questa opzione può essere usata in Enterprise Edition per installare un server Windows autonomo in grado di supportare R senza tuttavia richiedere l'interattività con SQL Server.    

> [!TIP] L'opzione Standalone **non** è necessaria per usare R con [!INCLUDE[tsql](../../includes/tsql-md.md)].
> 
> Se è necessario configurare un computer client per l'analisi scientifica dei dati in grado di connettersi a [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] o a Microsoft R Server (Standalone), è consigliabile usare [Microsoft R Client](http://go.microsoft.com/fwlink/?LinkId=799768).  

Se nello stesso computer si installano sia R Services (In-Database) sia Microsoft R Server (Standalone), tenere presente che verrà creata un'istanza di R separata per ogni istanza di SQL Server in cui è abilitato R, oltre a un'istanza separata di R per Microsoft R Server (Standalone).  Se, ad esempio, sono state installate l'istanza predefinita, un'istanza denominata e R Server (Standalone), è possibile che nello stesso computer siano presenti tre istanze di R:  
  
-   **Standalone:** C:\Programmi\Microsoft SQL Server\130\R_SERVER  
  
-   **Istanza predefinita:** C:\Programmi\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES  
  
-   **Istanza denominata:** C:\Programmi\Microsoft SQL Server\MSSQL13.<nome_istanza>\R_SERVICES  
  
> [!NOTE] 
> 
> Usare le librerie e gli strumenti R associati a un'istanza di database solo dal contesto di [!INCLUDE[tsql](../../includes/tsql-md.md)]. Se è necessario eseguire R usando altri strumenti R, assicurarsi di fare riferimento alle librerie R usate da R Server (Standalone), che per impostazione predefinita sono installate in C:\Programmi\Microsoft SQL Server\130\R_SERVER.  

### <a name="performance-limits-when-r-services-libraries-are-called-from-standalone-r-tools"></a>Limiti di prestazioni quando vengono chiamate librerie di R Services da strumenti R autonomi

Le librerie R usate da SQL Server R Services sono installate per impostazione predefinita in C:\Programmi\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES. È *possibile* chiamare librerie e strumenti R installati per SQL Server R Services da un'applicazione R esterna, ad esempio RGui. 

In questo caso, tuttavia, le prestazioni risulteranno limitate. Se si esegue il codice R usando strumenti esterni, R verrà eseguito in modalità a thread singolo anche se, ad esempio, è stato acquistato SQL Server Enterprise Edition. Per aumentare le prestazioni, è possibile eseguire il codice R inizializzando una connessione di SQL Server e usando il comando [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), che chiamerà automaticamente le librerie di R Services.

+ Evitare di chiamare da strumenti R esterni le librerie R usate da SQL Server. 
+ Se devono essere usati strumenti esterni per eseguire R nel computer SQL Server, è necessario installare un'istanza separata di R e quindi verificare che gli strumenti R puntino alla nuova libreria. 
+ Se si usa Enterprise Edition, è consigliabile installare Microsoft R Server (Standalone) nel computer SQL Server e quindi, tramite lo strumento esterno usato per eseguire il codice R, fare riferimento alle librerie di R Server, installate per impostazione predefinita in C:\Programmi\Microsoft SQL Server\<numero versione>\R_SERVER. 

Per altre informazioni, vedere [Creare un server R autonomo](../../advanced-analytics/r-services/create-a-standalone-r-server.md).  
  
  
## <a name="general-r-issues"></a>Problemi generali di R  

 Questa sezione elenca i problemi specifici degli strumenti per le prestazioni e la connettività di R.  
  
### <a name="limited-support-for-sql-data-types-in-spexecuteexternalscript"></a>Supporto limitato per i tipi di dati SQL in sp_execute_external_script  

 Non tutti i tipi di dati supportati in SQL possono essere usati in R. Come soluzione alternativa, valutare la possibilità di eseguire il cast del tipo di dati non supportato in un tipo di dati supportato prima di passare i dati a sp_execute_external_script.  
  
 Per altre informazioni, vedere [Uso dei tipi di dati di R](../../advanced-analytics/r-services/working-with-r-data-types.md).  
  
### <a name="possible-string-corruption"></a>Possibile danneggiamento della stringa  

 Qualsiasi round trip dei dati di stringa da [!INCLUDE[tsql](../../includes/tsql-md.md)] a R e quindi di nuovo a [!INCLUDE[tsql](../../includes/tsql-md.md)] può causarne il danneggiamento. Ciò è dovuto alle diverse codifiche usate in R e in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], nonché alle diverse regole di confronto e lingue supportate in R e [!INCLUDE[tsql](../../includes/tsql-md.md)]. Qualsiasi stringa in una codifica non ASCII può essere potenzialmente gestita in modo non corretto.  
  
 Quando si inviano i dati di stringa a R, convertirli in una rappresentazione ASCII, se possibile.  
  
### <a name="only-one-raw-value-can-be-returned-from-spexecuteexternalscript"></a>Solo un valore non elaborato può essere restituito da sp_execute_external_script  

 Quando un tipo di dati binari (il tipo di dati **raw** di R) viene restituito da R, il valore deve essere il valore nel frame dei dati di output.  
  
 Il supporto per più output di **raw** verrà aggiunti nelle versioni successive.  
  
 Una possibile soluzione alternativa se si vogliono più set di output consiste nell'effettuare più chiamate della stored procedure e inviare i set di risultati nuovamente a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando ODBC.  
  
 Tenere presente che è possibile restituire i valori dei parametri insieme ai risultati della stored procedure semplicemente aggiungendo la parola chiave OUTPUT. Per altre informazioni, vedere [Restituzione di dati utilizzando i parametri OUTPUT](https://technet.microsoft.com/library/ms187004.aspx).
  
### <a name="loss-of-precision"></a>Perdita di precisione  

 [!INCLUDE[tsql](../../includes/tsql-md.md)] e R supportano diversi tipi di dati. Pertanto, i tipi di dati numerici possono subire una perdita di precisione durante la conversione.  
  
 Per ulteriori informazioni sulla conversione implicita dei tipi di dati, vedere [Working with R Data Types](../../advanced-analytics/r-services/working-with-r-data-types.md).  
  
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
  
 Per evitare l'errore, riscrivere come:  
  
```  
g <- function(y){  
              f <- function(x) { 2*x +3}  
              a <- 10 * y  
              f(a)  
}  
  
```  

  
## <a name="revolution-r-enterprise-and-microsoft-r-open"></a>Revolution R Enterprise e Microsoft R Open 
 
 Questa sezione elenca i problemi specifici degli strumenti per le prestazioni, lo sviluppo e la connettività di R forniti da Revolution Analytics. Questi strumenti erano inclusi in precedenti versioni non definitive di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 

In generale, è consigliabile disinstallare queste versioni e installare la versione più recente di SQL Server R Services, Microsoft R Server o Microsoft R Client.
  
### <a name="running-side-by-side-versions-of-revolution-r-enterprise"></a>Esecuzione di versioni affiancate di Revolution R Enterprise  

 L'installazione side-by-side di Revolution R Enterprise con qualsiasi altra versione di [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] non è supportata.  
  
 Se si ha una licenza per usare una versione diversa di Revolution R Enterprise, è necessario inserirla in un computer separato sia dall'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia da qualsiasi workstation che si vuole usare per connettersi all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="limited-support-for-revoscaler-rxexec"></a>Supporto limitato per RevoScaleR rxExec  

 A partire dalla versione RC0, la funzione `rxExec` fornita da [!INCLUDE[rsql_rre-short](../../includes/rsql-rre-short-md.md)] può essere usata solo in modalità a thread singolo.  
  
 Il parallelismo di `rxExec` tra più processi verrà aggiunto in una versione futura.  
  
### <a name="data-import-and-manipulation-using-revoscaler"></a>Importazione e modifica dei dati con RevoScaleR  

 Durante la lettura delle colonne di **varchar** da un database verrà rimosso lo spazio vuoto. Per evitare questo problema, racchiudere le stringhe tra caratteri che non siano spazi vuoti.  
  
 Quando si usano funzioni come `rxDataStep` per creare tabelle di database con le colonne di **varchar** , la larghezza della colonna viene stimata in base a un campione di dati. Se la larghezza può variare, potrebbe essere necessario riempire tutte le stringhe a una lunghezza comune.  
  
 L'uso di una trasformazione per modificare il tipo di dati di una variabile non è supportato quando si usano chiamate ripetute a `rxImport` o a `rxTextToXdf` per importare e aggiungere righe, combinando più file di input in un singolo file XDF.  
  
### <a name="increase-maximum-parameter-size-to-support-rxgetvarinfo"></a>Aumentare la dimensione massima dei parametri per supportare rxGetVarInfo  

 Se si usano set di dati con un numero molto elevato di variabili (ad esempio, oltre 40.000), è necessario impostare il flag `max-ppsize` all'avvio R per poter usare le funzioni, ad esempio `rxGetVarInfo`.  Il flag `max-ppsize` specifica le dimensioni massime dello stack di protezione dell'indicatore di misura.  
  
 Se si usa la console di R (ad esempio, in rgui.exe o rterm.exe), è possibile impostare il valore di max-ppsize su 500000 digitando:  
  
```  
R --max-ppsize=500000  
```  
  
 Se si usa l'ambiente [!INCLUDE[rsql_developr](../../includes/rsql-developr-md.md)] , è possibile impostare il flag `max-ppsize` eseguendo questa chiamata al file eseguibile RevoIDE:  
  
```  
RevoIDE.exe /RCommandLine --max-ppsize=500000  
```  
  
### <a name="issues-with-rxdtree-function"></a>Problemi con la funzione rxDTree  

 La funzione `rxDTree` attualmente non supporta le trasformazioni nella formula. In particolare, l'uso della sintassi `F()` per la creazione di fattori in tempo reale non è supportata. Tuttavia, i dati numerici verranno automaticamente categorizzati.  
  
 I fattori ordinati vengono trattati proprio come i fattori in tutte le funzioni di analisi RevoScaleR eccetto `rxDTree`.  
  
### <a name="using-the-r-productivity-environment"></a>Uso di R Productivity Environment  

Alcune versioni non definitive di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] includono un ambiente di sviluppo R per Windows creato da Revolution Analytics. 

Tuttavia, per garantire la compatibilità con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], è consigliabile installare Microsoft R Client o Microsoft R Server anziché gli strumenti di Revolution Analytics. [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/) è un altro client consigliato per il supporto di soluzioni Microsoft R.
  
### <a name="compatibility-issues-with-sqlite-odbc-driver-and-revoscaler"></a>Problemi di compatibilità con il driver ODBC di SQLite e RevoScaleR  
 La revisione 0.92 del driver ODBC di SQLite è incompatibile con RevoScaleR; le revisioni 0.88-0.91 e 0.93 e le versioni successive risultano compatibili.  
  
## <a name="see-also"></a>Vedere anche  
[Novità di SQL Server 2016](../../sql-server/what-s-new-in-sql-server-2016.md)
  