---
title: 'Aggiornato: avanzato Analitica per i documenti del Server SQL | Documenti Microsoft'
description: Visualizzare i frammenti di contenuto aggiornato per modificati di recente nella documentazione, Analitica avanzato per Microsoft SQL Server.
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: advanced-analytics
ms.date: 02/03/2018
ms.openlocfilehash: fa0c25c193ea2815773ed9d08a50194d825f0a8a
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2018
---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Nuovi e aggiornati: Advanced Analitica per SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Quasi ogni giorno Microsoft aggiorna alcuni articoli esistenti nel relativo [Docs.Microsoft.com](http://docs.microsoft.com/) sito Web di documentazione. In questo articolo consente di visualizzare estratti dagli articoli aggiornati di recente. Potrebbero anche essere elencati collegamenti a nuovi articoli.

In questo articolo viene generato da un programma che viene eseguito di nuovo periodicamente. In alcuni casi un estratto può apparire con formattazione perfetto, o come markdown nell'articolo di origine. Le immagini non vengono mai visualizzate qui.

Aggiornamenti recenti vengono indicati per il seguente intervallo di date e l'oggetto:



- *Intervallo di date degli aggiornamenti:* &nbsp; **03/12/2017** &nbsp; - &nbsp; **03/02/2018**
- *Area di interesse:* &nbsp; **Advanced Analitica per SQL Server**.

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Installare nuovi pacchetti Python in SQL Server](python/install-additional-python-packages-on-sql-server.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui vengono visualizzati separatamente dal relativo contesto semantica corretto Inoltre, talvolta un estratto è separato dalla sintassi markdown importante che la racchiude nell'articolo effettivo. Di conseguenza questi estratti sono solo a scopo generale. Gli estratti consentono solo di sapere se i tuoi interessi garantiscono la necessità di fare clic e visitare l'articolo effettivo.

Per queste e altre ragioni, non copiare da questi estratti di codice e non prendono come verità esatta qualsiasi testo estratto. In alternativa, visitare l'articolo effettivo.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Compact elenco degli articoli aggiornato di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Problemi noti in servizi di Machine Learning](#TitleNum_1)
2. [Conversione del codice R per l'esecuzione nel database](#TitleNum_2)
3. [Determinare quali pacchetti R vengono installati in SQL Server](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-known-issues-in-machine-learning-servicesknown-issues-for-sql-server-machine-learning-servicesmd"></a>1. &nbsp; [Problemi noti in servizi di Machine Learning](known-issues-for-sql-server-machine-learning-services.md)

*Ultimo aggiornamento: 2018-02-02* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Avanti](#TitleNum_2))

<!-- Source markdown line 163.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c6f46adcf795c43f818120b88407a3a89304cb27 c781562605f5cd77f6c43bfe5e89810cb72ceae0  (PR=4789  ,  Filename=known-issues-for-sql-server-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\  ,  MergeCommitSha40=386bfb688843bac7fa4d83dc1cfef94dd19db110) -->



Per altri problemi noti che potrebbero influire sulle soluzioni R, vedere il [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues) sito.

**Accesso negato avviso durante l'esecuzione di script R in SQL Server in un percorso non predefinito**


Se l'istanza di SQL Server è stato installato in un percorso non predefinito, ad esempio di fuori di `Program Files` cartella, l'avviso ACCESS_DENIED viene generato quando si tenta di eseguire gli script che installa un pacchetto. Esempio:

> *NormalizePath(path.expand(path), winslash, mustWork): percorso [2] = "~ExternalLibraries/R/8/1": accesso negato*

Il motivo è che tenta di leggere il percorso di una funzione di R e non riesce se il gruppo users predefinito **SQLRUserGroup**, non dispone dell'accesso in lettura. L'avviso che viene generato non blocca l'esecuzione dello script R corrente, ma può ricorrere più volte il messaggio di avviso ogni volta che l'utente esegue tutti gli altri script R.

Se è stato installato SQL Server nel percorso predefinito, questo errore si verifica, perché le autorizzazioni di lettura in tutti gli utenti di Windows il `Program Files` cartella.

Questo problema verrà risolto in una prossima service release. In alternativa, specificare il gruppo, **SQLRUserGroup**, con accesso in lettura per tutte le cartelle padre di `ExternalLibraries`.

**Errore di serializzazione tra le versioni precedenti e nuove di RevoScaleR**


Quando si passa un modello utilizzando un formato serializzato a un'istanza remota di SQL Server, si potrebbe ricevere l'errore:

> *Errore in memDecompress (dati, tipo = decomprimere) Errore interno -3 nel memDecompress(2).*

Questo errore viene generato se è stato salvato il modello utilizzando una versione aggiornata della funzione di serializzazione, [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel), ma l'istanza di SQL Server in cui si esegue la deserializzazione del modello è una versione precedente di APIs RevoScaleR, da SQL Server 2017 CU2 o versioni precedenti.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-converting-r-code-for-execution-in-databaserconverting-r-code-for-use-in-sql-servermd"></a>2. &nbsp; [Conversione del codice R per l'esecuzione nel database](r/converting-r-code-for-use-in-sql-server.md)

*Ultimo aggiornamento: 2018-01-08* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_1) | [Avanti](#TitleNum_3))

<!-- Source markdown line 136.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a1d156fac1af5813ef75965071686b177e2aede7 fc8beff0aa0d7ea298e493b90984875e81e9143e  (PR=4493  ,  Filename=converting-r-code-for-use-in-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f486d12078a45c87b0fcf52270b904ca7b0c7fc8) -->



**Creare un pacchetto del codice R in una stored procedure**

+ Se il codice è relativamente semplice, è possibile incorporarlo in una funzione definita dall'utente di T-SQL senza alcuna modifica, come descritto in questi esempi:

    + [Creare una funzione di R che viene eseguito in rxExec](r/../tutorials/deepdive-create-a-simple-simulation.md)
    + [Funzionalità di progettazione utilizzando T-SQL e R](r/../tutorials/sqldev-create-data-features-using-t-sql.md)

+ Se il codice è più complesso, utilizzare il pacchetto R **sqlrutils** per convertire il codice. Questo pacchetto è stato progettato per consentire agli utenti di R esperti di scrivere codice buona stored procedure.

    Il primo passaggio è necessario riscrivere il codice R come una singola funzione con definito chiaramente input e output.

    Utilizzare quindi la **sqlrutils** pacchetto per generare l'input e output nel formato corretto. Il **sqlrutils** pacchetto genera il codice della stored procedure completa e può anche registrare la stored procedure nel database.

    Per ulteriori informazioni ed esempi, vedere [SqlRUtils](r/../r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md).

**Integrazione con altri flussi di lavoro**

+ Sfruttare gli strumenti di T-SQL e processi ETL. Eseguire progettazione di funzionalità, estrazione di funzioni e la pulizia dei dati in anticipo come parte di flussi di lavoro dati.

    Quando si lavora in un ambiente di sviluppo R dedicato, ad esempio strumenti R per Visual Studio o RStudio, è possibile effettuare il pull dei dati nel computer, analizzare i dati in modo iterativo e quindi scrivere o visualizzare i risultati.

    Tuttavia, quando il codice R autonomo viene eseguita la migrazione a SQL Server, la maggior parte di questo processo può essere semplificata o delegata ad altri strumenti di SQL Server.

+ Utilizzare le strategie di visualizzazione protetta e asincrona.

    Gli utenti di SQL Server spesso non è possibile accedere a file nel server e gli strumenti SQL client non supportano in genere il dispositivo di grafica R. Se si generano grafici o altre immagini come parte della soluzione, è consigliabile esportare i grafici come dati binari e salvataggio in una tabella o la scrittura.



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-determine-which-r-packages-are-installed-on-sql-serverrdetermine-which-packages-are-installed-on-sql-servermd"></a>3. &nbsp; [Determinare quali pacchetti R vengono installati in SQL Server](r/determine-which-packages-are-installed-on-sql-server.md)

*Ultimo aggiornamento: 2018-01-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_2))

<!-- Source markdown line 78.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9a065066398843a4bed318fa46d4982d712915a9 7a1df11f57e7bbf0abc37d3aa240dedd2b88c45f  (PR=4715  ,  Filename=determine-which-packages-are-installed-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=9e6a029456f4a8daddb396bc45d7874a43a47b45) -->




**Ottenere una versione e il percorso di libreria**


Nell'esempio seguente ottiene la posizione della raccolta di RevoScaleR nel contesto di calcolo locale e la versione del pacchetto.

```
rxFindPackage(RevoScaleR, "local")
packageVersion("RevoScaleR")
```

**Determinare percorso di libreria utilizzata da SQL Server**


Se è stato aggiornato di machine learning componenti mediante l'associazione, il percorso alla libreria R potrebbe cambiare. In questo caso, tasti di scelta rapida precedente degli strumenti di R potrebbe fare riferimento a una versione precedente. Per essere certi della versione del pacchetto e del percorso utilizzata da SQL Server, è possibile eseguire un comando analogo al seguente:

```
EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    sql_r_path <- rxSqlLibPaths("local")
      print(sql_r_path)
    version_info <-packageVersion("RevoScaleR")
      print(version_info)'
```

**Risultati**

```
STDOUT message(s) from external script:
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.2.1'
```







## <a name="similar-articles-about-new-or-updated-articles"></a>Articoli simili su articoli nuovi o aggiornati

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Aree di interesse *con* articoli nuovi o aggiornati di recente


- [Nuovo + aggiornato (1+3):&nbsp; documentazione di **Advanced Analytics per SQL** ](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione della **piattaforma di strumenti analitici per SQL** ](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione della **connessione a SQL Server** ](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione del **motore di database di SQL Server** ](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (12+1): documentazione di **SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (6+2):&nbsp; documentazione di **Linux per SQL Server** ](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (15+0):**documentazione di**PowerShell per SQL Server](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (2+9):&nbsp; documentazione dei **database relazionali per SQL Server** ](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (1+0):&nbsp; documentazione di **SQL Server Reporting Services** ](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (1+1):&nbsp; documentazione di **SQL Operations Studio** ](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (1+1):&nbsp; documentazione di **Microsoft SQL Server** ](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione di **SQL Server Data Tools (SSDT)** ](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (1+2):&nbsp; documentazione di **SQL Server Management Studio (SSMS)** ](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2):&nbsp; documentazione di **Transact-SQL** ](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Aree di interesse *senza* articoli nuovi o aggiornati di recente


- [Nuovo + aggiornato (0 + 0): documentazione di **Data Migration Assistant (DMA) per SQL Server**](../dma/new-updated-dma.md)
- [Nuovo + aggiornato (0 + 0): **oggetti ADO (ActiveX Data) per SQL** documenti](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): documentazione di **Analysis Services per SQL**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (0 + 0): **Data Quality Services per SQL** documenti](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0 + 0): **estensioni DMX (Data Mining) per SQL** documenti](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0 + 0): **MDX (Multidimensional Expressions) per SQL** documenti](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0 + 0): **ODBC (Open Database Connectivity) per SQL** documenti](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0 + 0): **esempi per SQL** documenti](../samples/new-updated-samples.md)
- [Nuovo + aggiornato (0 + 0): **SQL Server Migration Assistant (SSMA)** documenti](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0 + 0): **XQuery per SQL** documenti](../xquery/new-updated-xquery.md)


