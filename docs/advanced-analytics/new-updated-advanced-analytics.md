---
title: 'Aggiornato: avanzato Analitica per i documenti del Server SQL | Documenti Microsoft'
description: Visualizzare i frammenti di contenuto aggiornato per modificati di recente nella documentazione, Analitica avanzato per Microsoft SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: advanced-analytics
ms.date: 04/28/2018
ms.openlocfilehash: bbce32579b54647e167c25d2708a80027ae0e678
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Nuovi e aggiornati: Advanced Analitica per SQL Server



Quasi ogni giorno Microsoft aggiorna alcuni articoli esistenti nel relativo sito Web di documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). In questo articolo sono visualizzati estratti degli articoli aggiornati di recente. Potrebbero anche essere elencati collegamenti a nuovi articoli.

Questo articolo viene generato da un programma eseguito periodicamente. In alcuni casi un estratto può apparire con una formattazione imperfetta, o anche come markdown origine dell'articolo. Le immagini non vengono mai visualizzate qui.

Sono indicati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo degli aggiornamenti di date:* &nbsp; **2018-02-03** &nbsp; - a - &nbsp; **2018-04-28**
- *Area di interesse:* &nbsp; **Advanced Analitica per SQL Server**.

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Installare SQL Server 2017 di Machine Learning Services (In-Database) in Windows](install/sql-machine-learning-services-windows-install.md)
2. [Installare SQL Server 2017 apprendimento Server (Standalone) in Windows](install/sql-machine-learning-standalone-windows-install.md)
3. [Installare i componenti di SQL Server machine learning dalla riga di comando](install/sql-ml-component-commandline-install.md)
4. [Installare i componenti senza accesso a internet di apprendimento automatico SQL Server](install/sql-ml-component-install-without-internet-access.md)
5. [Installare SQL Server 2016 R Services (In-Database)](install/sql-r-services-windows-install.md)
6. [Installare SQL Server 2016 R Server (Standalone)](install/sql-r-standalone-windows-install.md)
7. [Configurare gli strumenti client per l'uso con SQL Server Machine Learning Python](python/setup-python-client-tools-sql.md)
8. [Utilizzare il modello di Python in SQL per il training e assegnazione dei punteggi](tutorials/train-score-using-python-in-tsql.md)
9. [Eseguire il wrapping di codice Python in una stored procedure](tutorials/wrap-python-in-tsql-stored-procedure.md)
10. [Che cos'è SQL Machine Learning Services](what-is-sql-server-machine-learning.md)
11. [Eventi estesi per il monitoraggio di istruzioni PREDICT](xe-event-predict-tsql.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui vengono visualizzati separatamente dal relativo contesto di semantica corretto. Inoltre, talvolta un estratto è separato dalla sintassi markdown importante che lo racchiude nell'articolo effettivo. Di conseguenza questi estratti sono solo a scopo generale. Gli estratti consentono solo di sapere se i tuoi interessi garantiscono la necessità di fare clic e visitare l'articolo effettivo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità esatta qualsiasi testo in essi contenuto. Piuttosto, visitare l'articolo effettivo.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Visualizzazione R o pacchetti Python installati in SQL Server](#TitleNum_1)
2. [Installare con training preliminare di machine learning i modelli in SQL Server](#TitleNum_2)
3. [Configurare un client di analisi scientifica dei dati per lo sviluppo di R in SQL Server](#TitleNum_3)
4. [SQL Server di Machine Learning e R Services (In-Database)](#TitleNum_4)
5. [Eseguire Python con T-SQL](#TitleNum_5)
6. [Usare Python con revoscalepy per creare un modello](#TitleNum_6)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-viewing-r-or-python-packages-installed-on-sql-serverrdetermine-which-packages-are-installed-on-sql-servermd"></a>1. &nbsp; [Visualizzazione R o pacchetti Python installati in SQL Server](r/determine-which-packages-are-installed-on-sql-server.md)

*Ultimo aggiornamento: 2018-04-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Avanti](#TitleNum_2))

<!-- Source markdown line 208.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7a1df11f57e7bbf0abc37d3aa240dedd2b88c45f ec6859ac91b27539dc36f21aec82c99937c0187a  (PR=5610  ,  Filename=determine-which-packages-are-installed-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f1f96a990644c0d6cfa5a1d88ccee959cab6c2b2) -->



**Python**


Questo esempio viene restituito l'elenco delle cartelle incluse in Python `sys.path` variabile. L'elenco include la directory corrente e il percorso della libreria standard.

```
EXEC sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

**Risultati**

```
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\python35.zip
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\DLLs
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Sphinx-1.5.4-py3.5.egg
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Pythonwin
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\setuptools-27.2.0-py3.5.egg
```

Per ulteriori informazioni sulla variabile `sys.path` e su come viene utilizzato per impostare il percorso di ricerca dell'interprete per i moduli, vedere il [documentazione Python](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-install-pre-trained-machine-learning-models-on-sql-serverrinstall-pretrained-models-sql-servermd"></a>2. &nbsp; [Installare con training preliminare di machine learning i modelli in SQL Server](r/install-pretrained-models-sql-server.md)

*Ultimo aggiornamento: 2018-04-12* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_1) | [Avanti](#TitleNum_3))

<!-- Source markdown line 140.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 aa03623d819750d4919feb7910b07ec1875bb509 7382228fa68b04b500a5fde73c29995e12aa20ac  (PR=5504  ,  Filename=install-pretrained-models-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f34765240b79a44167ca2af90f97a0fdd47c41d2) -->



1. Avviare il programma basato su Windows separato per uno [R Server](https://docs.microsoft.com/machine-learning-server/rebranding-microsoft-r-server) oppure [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).

2. Selezionare le lingue che si desiderano aggiornare e scegliere il **Pre-trained modelli** opzione.

    > [!TIP]
    > Se in precedenza è stato eseguito il programma di installazione per aggiornare R Server (Standalone), è sufficiente aggiungere i modelli con training preliminare, lasciare tutte le selezioni precedenti **come**, selezionare semplicemente Pre **-Training modelli di** opzione . **Non** deselezionate le opzioni selezionate in precedenza, se in tal modo, il programma di installazione rimuove i componenti.

    Si consiglia di accettare le impostazioni predefinite per i percorsi di modello.

3. Fare clic su **Continua**.

4. Accettare tutte le altre richieste, inclusi i contratti di licenza.

Al termine dell'installazione, è necessario eseguire alcuni passaggi aggiuntivi per registrare i modelli con training preliminare.

1. Aprire un prompt dei comandi di Windows **come amministratore**.

2. Passare alla cartella setup bootstrap per R Server (Standalone), che contiene anche il programma di installazione di Microsoft R.

3. Eseguire `RSetup.exe` e indicare il componente per l'installazione, la versione e la cartella contenente i file di origine del modello, utilizzando questa sintassi:

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "~\R_SERVER\library\MicrosoftML\mxLibs\x64"`

    I valori seguenti sono supportati per il parametro version:



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-set-up-a-data-science-client-for-r-development-on-sql-serverrset-up-a-data-science-clientmd"></a>3. &nbsp; [Configurare un client di analisi scientifica dei dati per lo sviluppo di R in SQL Server](r/set-up-a-data-science-client.md)

*Ultimo aggiornamento: 2018-04-12* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_2) | [Avanti](#TitleNum_4))

<!-- Source markdown line 39.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0583f8febcedc5dc2e14ca1a8073ca204ca37987 3d50ad8f35f2985944741a9b2211a461df2c13e4  (PR=5504  ,  Filename=set-up-a-data-science-client.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f34765240b79a44167ca2af90f97a0fdd47c41d2) -->



**Strumenti di R**


Quando si installa R con SQL Server, si ottengono gli stessi strumenti R che vengono installati con qualsiasi **base** installazione di R, ad esempio RGui, Rterm e così via. Tecnicamente, si disporrebbe tutti gli strumenti che necessari per sviluppare e testare il codice R.

Sono inclusi i seguenti strumenti standard di R in un *installazione di base* di R e pertanto vengono installati per impostazione predefinita.

+ **RTerm**: un terminale della riga di comando per l'esecuzione di script R

+ **RGui.exe**: semplice editor interattivo per R. Gli argomenti della riga di comando sono gli stessi di RGui.exe e RTerm.

+ **RScript**: strumento da riga di comando per l'esecuzione di script R in modalità batch.

Per individuare questi strumenti, determinare la raccolta di R che è stata installata quando si configura SQL Server o della macchina autonoma funzionalità di apprendimento. Ad esempio, in un'installazione predefinita, gli strumenti di R si trovano in queste cartelle:

+ SQL Server 2016 R Services: `~\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64`
+ Microsoft R Server autonomo: `~\Program Files\Microsoft R\R_SERVER\bin\x64`
+ SQL Server 2017 apprendimento servizi: `~\Program Files\Microsoft SQL Server\MSSQL14.<instancename>\R_SERVICES\bin\x64`
+ Machine Learning Server (Standalone): `~\Program Files\Microsoft\ML Server\R_SERVER\bin\x64`

Se assistenza con gli strumenti di R, aprire **RGui**, fare clic su **Guida**e selezionare una delle opzioni

**Microsoft R Client**


Microsoft R è un download gratuito che consente di accedere ai pacchetti RevoScaleR per il processo di sviluppo. Installando il Client R, è possibile creare soluzioni R che possono essere eseguite in tutti i contesti di calcolo supportati, tra cui analitica nel database di SQL Server e R distribuite in Hadoop, Spark o Linux con Server di Machine Learning.

Se è già stato installato un ambiente di sviluppo R diverso, ad esempio RStudio, assicurarsi di riconfigurare l'ambiente per usare le librerie e file eseguibili forniti dal Client di Microsoft R. In questo modo è possibile utilizzare tutte le funzionalità del pacchetto RevoScaleR, anche se le prestazioni sarà limitata.



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-sql-server-machine-learning-and-r-services-in-databasersql-server-r-servicesmd"></a>4. &nbsp; [SQL Server di Machine Learning e R Services (In-Database)](r/sql-server-r-services.md)

*Ultimo aggiornamento: 2018-04-12* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_3) | [Avanti](#TitleNum_5))

<!-- Source markdown line 83.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b1a95a7f6d391a518762eb271e8ea7e0d684d403 7fbfabf62917e03e2bcb99d297e1c9d0f0604440  (PR=5504  ,  Filename=sql-server-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f34765240b79a44167ca2af90f97a0fdd47c41d2) -->



Scegliere il linguaggio più adatto per l'attività. R è ideale per i calcoli statistici difficili da implementare con SQL. Per le operazioni sui dati basata su set, sfruttano la potenza del *{inclusi contenuto-non diminuisce qui}* per ottenere prestazioni ottimali. Utilizzare il motore di database in memoria per i calcoli molto veloci su colonne.

**Passaggio 4: Ottimizzare la soluzione**


Quando il modello è pronto per applicare la scalabilità ai dati aziendali, l'esperto di dati funziona spesso con lo sviluppatore di amministratore di database o SQL per ottimizzare i processi, ad esempio:

+ Progettazione delle funzionalità
+ Inserimento di dati e la trasformazione dei dati
+ Assegnazione dei punteggi

Gli esperti di dati con R sono sempre state problemi di prestazioni e scalabilità, soprattutto quando si utilizzano i dataset di grandi dimensioni. Ciò avviene perché l'implementazione di common runtime è a thread singolo e può gestire solo i set di dati che rientrano nella memoria disponibile nel computer locale. Integrazione con servizi di SQl Server Machine Learning fornisce più funzionalità per ottenere prestazioni migliori, con ulteriori dati:

+ **RevoScaleR**: R questo pacchetto contiene le implementazioni di alcune funzioni R più diffuse, riprogettate per garantire parallelismo e scalabilità. Il pacchetto include inoltre funzioni che incrementano scalabilità e prestazioni trasferendo i calcoli per il *{inclusi contenuto-non diminuisce qui}* computer, che ha in genere più memoria e potenza di calcolo.

+ **revoscalepy**. Questa libreria Python, disponibile in SQL Server 2017, implementa funzioni più diffuse in RevoScaleR, ad esempio contesti di calcolo remoti e numerosi algoritmi che supportano l'elaborazione distribuita.

**Risorse**

+ [Case Study di prestazioni]
+ [R e ottimizzazione dati]

**Passaggio 5: Distribuire e usare**




&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-run-python-using-t-sqltutorialsrun-python-using-t-sqlmd"></a>5. &nbsp; [Eseguire Python con T-SQL](tutorials/run-python-using-t-sql.md)

*Ultimo aggiornamento: 2018-04-11* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_4) | [Avanti](#TitleNum_6))

<!-- Source markdown line 306.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 bde8c6476df259d225847c08224cefd02f3529d5 cad56997abe7928b588ac4a0302384c5edc1ede5  (PR=5497  ,  Filename=run-python-using-t-sql.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=86c4e1879c5914676b9da384ab101b50b4a63bf1) -->



2. Si noti che i valori di indice non sono output, anche se si utilizza l'indice per ottenere i valori specifici dal data.frame.

    **Risultati**

    |ResultValue|
    |------|
    |0,5|
    |2|

**Valori di output in data.frame tramite un indice**


Di seguito viene illustrato il funzionamento di conversione in un data.frame con due serie che contiene i risultati di operazioni matematiche semplici. Il primo ha un indice dei valori sequenziali generati da Python. La seconda Usa un indice arbitrario di valori stringa.

1. In questo esempio Ottiene un valore di serie che utilizza un indice intero.

```
    EXECUTE sp_execute_external_script
    @language = N'Python',
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    df = pd.DataFrame(s, index=[1])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
```

Tenere presente che l'indice generato automaticamente inizia in corrispondenza di 0. Provare a utilizzare un timeout del valore di indice di intervallo e verificare il risultato.

2. Ora consente di ottenere un valore singolo da altri frame di dati che dispone di un indice stringa.

```
    EXECUTE sp_execute_external_script
    @language = N'Python',
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
    print(s)
    df = pd.DataFrame(s, index=["simple math example 1"])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
```

**Risultati**

|ResultValue|
|------|
|0,5|

Se si tenta di utilizzare un indice numerico per ottenere un valore di questa serie, viene visualizzato un errore.



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-use-python-with-revoscalepy-to-create-a-modeltutorialsuse-python-revoscalepy-to-create-modelmd"></a>6. &nbsp; [Usare Python con revoscalepy per creare un modello](tutorials/use-python-revoscalepy-to-create-model.md)

*Ultimo aggiornamento: 2018-04-11* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_5))

<!-- Source markdown line 22.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5b642b391ca571412c30c8470875d3d4d3c57246 bd83387eb8a1076a1396bbd48dca12872843aa2f  (PR=5497  ,  Filename=use-python-revoscalepy-to-create-model.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=86c4e1879c5914676b9da384ab101b50b4a63bf1) -->



Se è installata una versione non definitiva di SQL Server 2017, è necessario aggiornare a almeno la versione RTM. Nelle versioni successive del servizio è sono costantemente espandere e migliorare le funzionalità di Python. Alcune funzionalità di questa esercitazione potrebbero non funzionare nelle prime versioni di pre-release.

+ Questo esempio viene utilizzato un ambiente di Python predefinito, denominato `PYTEST_SQL_SERVER`. L'ambiente è stato configurato per contenere **revoscalepy** e altre librerie necessarie.

    Se non si dispone di un ambiente configurato per l'esecuzione di Python, è necessario farlo separatamente. Informazioni su come creare o modificare gli ambienti Python esula dall'ambito di questa esercitazione. Per ulteriori informazioni su come configurare un client Python che contiene le librerie corrette, vedere [client di installare Python](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) e [Python collegamento agli strumenti](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools).

**Revoscalepy e contesti di calcolo remoto**


In questo esempio viene illustrato il processo di creazione di un modello di Python in remota _contesto di calcolo_, che consente utilizzare un client, ma scegliere un ambiente remoto, ad esempio SQL Server, Spark o Server di Machine Learning, in cui il operazioni vengono effettivamente eseguite. Contesti di calcolo utilizzando rende più semplice scrivere codice una sola volta e distribuirlo in qualsiasi ambiente supportato.

Per eseguire codice Python in SQL Server, è necessario il **revoscalepy** pacchetto. Si tratta di un pacchetto di Python speciale fornito da Microsoft, simile al **RevoScaleR** pacchetto per il linguaggio R. Il **revoscalepy** pacchetto supporta la creazione di contesti di calcolo e fornisce l'infrastruttura per il passaggio di dati e modelli tra una workstation locale e un server remoto. Il **revoscalepy** funzione che supporta l'esecuzione del codice nel database è [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver).







## <a name="similar-articles-about-new-or-updated-articles"></a>Articoli simili su articoli nuovi o aggiornati

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Aree di interesse *con* articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (11 + 6): &nbsp; &nbsp; **Advanced Analitica per SQL** docs](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (18 + 0): &nbsp; &nbsp; **Analysis Services per SQL** docs](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (218 + 14): **Connect to SQL** docs](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (14 + 0): &nbsp; &nbsp; **motore di Database per SQL** docs](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (3 + 2): &nbsp; &nbsp; **servizi di integrazione per SQL** docs](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (3 + 3): &nbsp; &nbsp; **Linux per SQL** docs](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (7 + 10): &nbsp; &nbsp; **database relazionali di SQL** docs](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (0 + 2): &nbsp; &nbsp; **Reporting Services per SQL** docs](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (1 + 3): &nbsp; &nbsp; **operazioni SQL Studio** docs](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (2 + 3): &nbsp; &nbsp; **Microsoft SQL Server** docs](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (1 + 1): &nbsp; &nbsp; **SQL Server Data Tools (SSDT)** docs](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (5 + 2): &nbsp; &nbsp; **SQL Server Management Studio (SSMS)** docs](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0 + 2): &nbsp; &nbsp; **Transact-SQL** docs](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (1 + 1): &nbsp; &nbsp; **Tools per SQL** docs](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Aree di interesse *senza* articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0 + 0): **Analitica Platform System per SQL** docs](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (0 + 0): **Data Quality Services per SQL** documenti](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0 + 0): **estensioni DMX (Data Mining) per SQL** documenti](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0 + 0): **MDX (Multidimensional Expressions) per SQL** documenti](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0 + 0): **ODBC (Open Database Connectivity) per SQL** documenti](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0 + 0): **PowerShell per SQL** documenti](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0 + 0): **esempi per SQL** documenti](../samples/new-updated-samples.md)
- [Nuovo + aggiornato (0 + 0): **SQL Server Migration Assistant (SSMA)** documenti](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0 + 0): **XQuery per SQL** documenti](../xquery/new-updated-xquery.md)

