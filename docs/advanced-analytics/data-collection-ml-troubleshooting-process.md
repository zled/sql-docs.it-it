---
title: Risoluzione dei problemi di raccolta dati per l'apprendimento automatico, SQL Server
ms.custom: ''
ms.date: 06/16/2017
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- R
caps.latest.revision: ''
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 95b70a2992b5c43ebaefb8faa729ec16ac3c84f7
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="troubleshoot-data-collection-for-machine-learning"></a>Risoluzione dei problemi di raccolta dati per l'apprendimento automatico
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo descrive il tipo di dati da raccogliere quando si tenta di risolvere i problemi con il programma di installazione, configurazione o le prestazioni di machine learning in SQL Server. Tali dati includono registri, i messaggi di errore e le informazioni di sistema.

L'articolo vengono descritte le origini di informazioni che sono particolarmente utili quando si esegue la diagnostica in una base di risolvere autonomamente il problema. Raccolta di queste informazioni è utile anche quando si richiede il supporto tecnico per i problemi relativi alle funzionalità di SQL Server machine learning.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services (R e Python)

## <a name="sql-server-and-r-versions"></a>Versioni di SQL Server e R

Nota Se la versione è una nuova installazione o l'aggiornamento. Se è un aggiornamento, determinare la modalità con cui è stata eseguita:

- La versione è stata l'aggiornamento da? 
- Sono stati rimossi i componenti obsoleti, oppure ha l'aggiornamento sul posto?
- Apportare funzionalità ha modifiche durante l'aggiornamento? 

### <a name="which-edition-of-sql-server-is-installed-and-which-version"></a>Edizione di SQL Server installata e quale versione? 

SQL Server R Services è stato introdotto in SQL Server 2016. Le versioni precedenti non supportano l'apprendimento. Inoltre, i service pack successivi per la versione di 2016 inclusi numerosi miglioramenti e correzioni di bug. Come primo passaggio, è consigliabile installare Service Pack 1 o versione successivo.

In SQL Server 2017, supporto viene esteso per il linguaggio Python. Nelle versioni precedenti non è stato fornito il supporto per Python.

Assistenza per determinare quale edizione e la versione, vedere l'articolo, in cui sono elencati i numeri di build per ogni il [versioni di SQL Server](https://social.technet.microsoft.com/wiki/contents/articles/783.sql-server-versions.aspx#Service_Pack_editions).

A seconda dell'edizione di SQL Server in uso, alcune funzionalità di apprendimento automatico potrebbe essere non disponibile o limitate.

Vedere gli articoli seguenti per un elenco delle funzionalità di machine learning nelle edizioni Enterprise, Developer, Standard ed Express.

* [Edizioni e le funzionalità supportate di SQL Server](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)
* [Differenze nelle funzionalità di R tra le edizioni di SQL Server](https://docs.microsoft.com/sql/advanced-analytics/r/differences-in-r-features-between-editions-of-sql-server)

### <a name="which-version-of-microsoft-r-is-installed"></a>La versione di Microsoft R è installato.

In generale, la versione di Microsoft R che viene installato quando si seleziona la funzionalità di R Services o la funzionalità di servizi di Machine Learning è determinata dal numero della build di SQL Server. Se si aggiorna o patch di SQL Server, è necessario aggiornare o patch componenti R.

Per un elenco delle versioni e i collegamenti ai download di componenti di R, vedere [installare i componenti di machine learning senza accesso a internet](https://docs.microsoft.com/sql/advanced-analytics/r/installing-ml-components-without-internet-access). Nei computer con accesso a internet, la versione richiesta di R è identificata e installata automaticamente.

È possibile aggiornare i componenti di R Server separatamente dal motore di database di SQL Server, in un processo noto come associazione. Pertanto, la versione di R in uso quando si esegue codice R in SQL Server potrebbe variare a seconda la versione installata di SQL Server e se la migrazione il server alla versione più recente di R.

#### <a name="determine-the-r-version"></a>Determinare la versione di R

Il modo più semplice per determinare la versione di R è per ottenere le proprietà di runtime tramite l'esecuzione di un'istruzione simile alla seguente:

```SQL
exec sp_execute_external_script
       @language = N'R'
       , @script = N'
# Transform R version properties to data.frame
OutputDataSet <- data.frame(
  property_name = c("R.version", "Revo.version"), 
  property_value = c(R.Version()$version.string, Revo.version$version.string),
  stringsAsFactors = FALSE)
# Retrieve properties like R.home, libPath & default packages
OutputDataSet <- rbind(OutputDataSet, data.frame(
  property_name = c("R.home", "libPaths", "defaultPackages"),
  property_value = c(R.home(), .libPaths(), paste(getOption("defaultPackages"), collapse=", ")),
  stringsAsFactors = FALSE)
)
'
WITH RESULT SETS ((PropertyName nvarchar(100), PropertyValue nvarchar(4000)));

```

> [!TIP] 
> Se R Services non funziona, provare a eseguire solo la parte di script R da RGui.

Come ultima risorsa, è possibile aprire i file sul server per determinare la versione installata. A tale scopo, individuare il file rlauncher.config per ottenere la posizione del runtime di R e la directory di lavoro corrente. Si consiglia di verificare e aprire una copia del file in modo da non modificare accidentalmente alcuna proprietà.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name\MSSQL\Binn\rlauncher.config`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Binn\rlauncher.config`

Per ottenere la versione di R e RevoScaleR, aprire un prompt dei comandi di R, o aprire RGui associata con l'istanza.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64\RGui.exe`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES\bin\x64\RGui.exe`


Nella console di R vengono visualizzate le informazioni sulla versione all'avvio. Ad esempio, la seguente versione rappresenta la configurazione predefinita di SQL Server 2017 CTP 2.0:

    *Microsoft R Open 3.3.3*
    
    *The enhanced R distribution from Microsoft*
    
    *Microsoft packages Copyright (C) 2017 Microsoft*
    
    *Loading Microsoft R Server packages, version 9.1.0.*


### <a name="what-version-of-python-is-installed"></a>La versione di Python è installata?

Supporto per Python è disponibile solo in SQL Server 2017 Community Technology Preview (CTP) 2.0 e versioni successive.

Esistono diversi modi per ottenere la versione di Python. Il modo più semplice è eseguire questa istruzione da Management Studio o qualsiasi altro strumento di query SQL:

```SQL
-- Get Python runtime properties:
exec sp_execute_external_script
       @language = N'Python'
       , @script = N'
import sys
import pkg_resources
OutputDataSet = pandas.DataFrame(
                    {"property_name": ["Python.home", "Python.version", "Revo.version", "libpaths"],
                    "property_value": [sys.executable[:-10], sys.version, pkg_resources.get_distribution("revoscalepy").version, str(sys.path)]}
)
'
with WITH RESULT SETS (SQL keywords) ((PropertyName nvarchar(100), PropertyValue nvarchar(4000)));
```

Se non è in esecuzione servizi di Machine Learning, è possibile determinare la versione installata di Python esaminando il file pythonlauncher.config. Si consiglia di verificare e aprire una copia del file in modo da non modificare accidentalmente alcuna proprietà.

1. Solo per SQL Server 2017: `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog\pythonlauncher.config `
2. Ottenere il valore di **PYTHONHOME**.
3. Ottenere il valore della directory di lavoro corrente.


> [!NOTE]
> Se è stato installato sia Python e R in SQL Server 2017, la directory di lavoro e il pool di account di lavoro vengono condivisi per le lingue di R e Python.

### <a name="are-multiple-instances-of-r-or-python-installed"></a>Più istanze di R o Python installato.

Verificare se più di una copia delle librerie R è installata nel computer. Questa duplicazione può verificarsi se:

* Durante l'installazione si seleziona sia R Services (In-Database) e R Server (Standalone). 
* Installare Microsoft R Client oltre a SQL Server.
* Un set diverso di librerie R è stato installato utilizzando gli strumenti R per Visual Studio, R Studio, Microsoft R Client o altri IDE R.
* Il computer ospita più istanze di SQL Server e più di un'istanza Usa il machine learning.

Le stesse condizioni si applicano per Python.

Se si ritiene che siano installati più librerie o Runtime, assicurarsi di ottenere solo gli errori associati i runtime di Python o R che vengono utilizzati dall'istanza di SQL Server.

## <a name="errors-and-messages"></a>Errori e messaggi

Gli errori che viene visualizzato quando si tenta di eseguire il codice R possono provenire da una qualsiasi delle seguenti origini:

- Motore di database di SQL Server, inclusi il sp_execute_external_script stored procedure
- Launchpad attendibile di SQL Server 
- Altri componenti di extensibility framework, inclusi avvio R e Python e i processi satellite
- Provider, ad esempio Microsoft Open Database Connectivity (ODBC)
- Linguaggio R

Quando si lavora con il servizio per la prima volta, può essere difficile stabilire quali messaggi provengono da cui i servizi. Si consiglia di acquisire non solo il testo del messaggio esatta, ma il contesto in cui è stato illustrato il messaggio. Si noti il software client che sta utilizzando per eseguire il codice di machine learning:

- Si sta utilizzando Management Studio? Un'applicazione esterna?
- Si esegue codice R in un client remoto o direttamente in una stored procedure?

### <a name="what-errors-has-sql-server-logged"></a>Gli errori registrati con SQL Server

Ottenere il più recente di SQL Server di log degli errori. Il set completo di log degli errori include i file dalla directory log predefinita seguente:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.SQL2016\MSSQL\Log\ExtensibilityLog`

> [!NOTE] 
> Il nome esatto della cartella varia a seconda il nome dell'istanza.


### <a name="what-errors-were-returned-by-the-spexecuteexternalscript-command"></a>Gli errori restituiti dal comando sp_execute_external_script?

Ottenere il testo completo degli errori che vengono restituiti, se presente, quando si esegue il comando sp_execute_external_script. 

Per evitare problemi di R o Python preso in considerazione, è possibile eseguire questo script, che avvia il runtime di R o Python e passa i dati e viceversa.

**Per R**

```sql
exec sp_execute_external_script @language =N'R',  
@script=N'OutputDataSet<-InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

**Per Python**

```sql
exec sp_execute_external_script @language =N'Python',  
@script=N'OutputDataSet= InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

### <a name="what-errors-are-generated-by-the-extensibility-framework"></a>Gli errori vengono generati dal framework di estendibilità?

SQL Server genera un file di log distinti per i runtime del linguaggio dello script esterno. Questi errori non vengono generati dal linguaggio Python o R. Sono generati dai componenti di estendibilità in SQL Server, tra cui avvio specifici della lingua e i processi satellite.

È possibile ottenere questi log nei percorsi predefiniti seguenti:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog `

> [!NOTE] 
> Il nome esatto della cartella varia in base al nome di istanza. A seconda della configurazione, la cartella potrebbe essere in un'unità diversa.

Ad esempio, i messaggi di log seguenti riguardano il framework di estendibilità:

* *LogonUser non riuscito per l'utente MSSQLSERVER01*
  
  Ciò potrebbe indicare che gli account di lavoro che eseguono script esterno non è possibile accedere all'istanza.

* *InitializePhysicalUsersPool non riuscita* 
  
  Questo messaggio potrebbe indicare che le impostazioni di protezione impediscano l'installazione dalla creazione del pool di account di lavoro che sono necessari per l'esecuzione di script esterni.

* *Inizializzazione di gestore del contesto di sicurezza non riuscita* 

* *Inizializzazione di gestione di sessioni satellite non è riuscita*

### <a name="are-there-any-related-system-events"></a>Sono presenti tutti gli eventi di sistema correlate?

1. Aprire il Visualizzatore eventi di Windows e di ricerca di **evento di sistema** log per i messaggi che includono la stringa *Launchpad*. 
2. Aprire il file ExtLaunchErrorlog e cercare la stringa *ErrorCode*. Esaminare il messaggio associato a un codice di errore.

Ad esempio, i messaggi seguenti sono comuni errori di sistema che riguardano il framework di estendibilità di SQL Server: 

* *Il servizio SQL Server Launchpad (MSSQLSERVER) non è stato possibile avviare a causa dell'errore seguente:  <text>*

* *Il servizio non ha risposto alla richiesta di avvio o di controllo in modo tempestivo.* 

* *(In 120000 millisecondi) è stato raggiunto un timeout durante l'attesa per il servizio SQL Server Launchpad (MSSQLSERVER) per la connessione.* 

### <a name="did-any-components-start-and-then-crash"></a>Tutti i componenti start e quindi di arresto anomalo?

Se ha familiarità con il debug, è possibile utilizzare i file di dump per analizzare un errore nella finestra di avvio.

1. Individuare la cartella che contiene i registri di installazione bootstrap per SQL Server. In SQL Server 2016, ad esempio, il percorso predefinito è C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log.
2. Aprire la sottocartella di log bootstrap è specifica di estendibilità.
3. Se è necessario inviare una richiesta di supporto, aggiungere l'intero contenuto di questa cartella un file compresso. Ad esempio C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log\LOG\ExtensibilityLog.
  
La posizione esatta potrebbero essere diversi nel sistema e potrebbe trovarsi in un'unità diversa dall'unità C. Assicurarsi di ottenere i registri per l'istanza in cui è installato l'apprendimento. 


## <a name="related-tools-and-configuration"></a>Configurazione e gli strumenti correlati

In questa sezione elenca i componenti aggiuntivi o i provider che possono essere un'origine degli errori quando si eseguono script R o Python.

### <a name="what-network-protocols-are-available"></a>I protocolli di rete sono disponibili?

Servizi di Machine Learning richiede i seguenti protocolli di rete per le comunicazioni interne tra i componenti di estendibilità e per la comunicazione con client esterni di R o Python.

* Named Pipes
* TCP/IP

Aprire Gestione configurazione di SQL Server per determinare se è installato un protocollo e, se è installato, per determinare se questa è abilitata.

### <a name="security-configuration-and-permissions"></a>Autorizzazioni e la configurazione di sicurezza

Per gli account di lavoro:

1. Nel Pannello di controllo aprire **utenti e gruppi**e individuare il gruppo utilizzato per eseguire processi di script esterni. Per impostazione predefinita, il gruppo è **SQLRUserGroup**.
2. Verificare che il gruppo esista e che contiene almeno un lavoro account.
3. In SQL Server Management Studio, selezionare l'istanza in cui verranno eseguiti i processi R o Python, selezionare **sicurezza**e quindi determinare se è presente un account di accesso per SQLRUserGroup.
4. Rivedere le autorizzazioni per il gruppo di utenti.

Per singoli account utente:

1. Determinare se l'istanza supporta l'autenticazione in modalità mista, solo gli accessi SQL o solo l'autenticazione di Windows. Questa impostazione influisce l'esecuzione o i requisiti del codice Python.
2. Per ogni utente che ha l'esigenza di eseguire il codice R, determinare il livello di autorizzazioni per ogni database in cui gli oggetti verranno scritti da R, sarà possibile accedere ai dati o verranno creati oggetti richiesto.
3. Per abilitare l'esecuzione dello script, creare i ruoli o aggiungere utenti ai ruoli seguenti, in base alle esigenze:

   - Tutti tranne *db_owner*: richiedono EXECUTE ANY EXTERNAL SCRIPT.
   - *db_datawriter*: per scrivere i risultati da R o Python. 
   - *db_ddladmin*: per creare nuovi oggetti. 
   - *db_datareader*: leggere i dati utilizzati da codice Python o R. 
4. Nota Se è stato modificato qualsiasi account di avvio predefiniti durante l'installazione di SQL Server 2016.
5. Se un utente deve installare i nuovi pacchetti R o utilizzare i pacchetti R che sono stati installati da altri utenti, è necessario abilitare la gestione dei pacchetti nell'istanza e quindi assegnare le autorizzazioni aggiuntive. Per ulteriori informazioni, vedere [abilitare o disabilitare la gestione dei pacchetti R](r\r-package-how-to-enable-or-disable.md).

### <a name="what-folders-are-subject-to-locking-by-antivirus-software"></a>Le cartelle che sono soggetti a blocco dal software antivirus?

Il software antivirus è possibile bloccare cartelle, che impedisce di entrambe le impostazioni di machine learning funzionalità e l'esecuzione corretta dello script. Determinare se le cartelle nella struttura ad albero di SQL Server sono soggetti a ricerca di virus.

Tuttavia, quando in un'istanza vengono installate più servizi o funzionalità, può essere difficile da enumerare tutte le possibili cartelle utilizzate dall'istanza. Ad esempio, quando vengono aggiunte nuove funzionalità, le nuove cartelle devono essere identificate ed esclusi.

Inoltre, alcune funzionalità di creare dinamicamente nuove cartelle in fase di esecuzione. Tabelle OLTP in memoria, le stored procedure e funzioni, ad esempio, creare nuove directory in fase di esecuzione. Questi nomi di cartella spesso contengono GUID e non possono essere previsto. Il Launchpad attendibile di SQL Server crea nuova directory di lavoro per R, Python generare script dei processi.

Poiché potrebbe non essere possibile escludere tutte le cartelle che sono necessari per il processo di SQL Server e delle relative funzionalità, è consigliabile escludere l'intero albero di directory istanza di SQL Server.

### <a name="is-the-firewall-open-for-sql-server-does-the-instance-support-remote-connections"></a>Viene aperto il firewall per SQL Server? L'istanza supporta le connessioni remote?

1. Per determinare se SQL Server supporta le connessioni remote, vedere [configurare connessioni remote](../database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md).

2. Determinare se è stata creata una regola del firewall per SQL Server. Per motivi di sicurezza in un'installazione predefinita, potrebbe non essere possibile per il client R o Python remoto per connettersi all'istanza. Per ulteriori informazioni, vedere [risoluzione dei problemi di connessione a SQL Server](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md).

### <a name="can-you-run-r-script-outside-t-sql"></a>È possibile eseguire lo script R all'esterno di T-SQL?

È possibile provare a eseguire il runtime di R è associato all'istanza di SQL Server utilizzando altri strumenti di R. In questo modo, è possibile determinare se sono installate le librerie necessarie.

Un'installazione di R di base include più strumenti che è possibile utilizzare per eseguire uno script R da riga di comando, nonché RGui per l'esecuzione interattiva di script.

Se il runtime di R è funzionante, ma lo script restituisce errori, è consigliabile provare il debug di script in un ambiente di sviluppo R dedicato, ad esempio strumenti R per Visual Studio.

È inoltre consigliabile esaminare e leggermente riscrivere lo script per risolvere eventuali problemi con i tipi di dati che potrebbero verificarsi quando si spostano dati tra R e il motore di database. Per altre informazioni, vedere [tipi di dati e delle librerie R](r/r-libraries-and-data-types.md).

Inoltre, è possibile utilizzare il pacchetto sqlrutils per raggruppare script R in un formato più facilmente utilizzabile come una stored procedure. Per altre informazioni, vedere:
* [Generare una stored procedure per il codice R tramite il pacchetto sqlrutils](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
* [Creare una stored procedure utilizzando sqlrutils](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## <a name="see-also"></a>Vedere anche

[Risolvere i problemi di apprendimento automatico in SQL Server](machine-learning-troubleshooting-faq.md)
