---
title: Guida introduttiva per un'esecuzione di codice "Hello World" base R in T-SQL (SQL Server Machine Learning Services) | Microsoft Docs
description: In questa Guida introduttiva per lo script R in SQL Server, informazioni di base di sp_execute_external_script stored procedure di sistema con un esercizio hello-world.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e738289b39f6d390bc4d6196606d242fa4803865
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086884"
---
# <a name="quickstart-hello-world-r-script-in-sql-server"></a>Guida introduttiva: Lo script R "Hello world" in SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server include il supporto di funzionalità del linguaggio R per analitica nel database residenti in dati di SQL Server. È possibile usare le funzioni R open source, i pacchetti di terze parti e pacchetti predefiniti di Microsoft R per analitica predittiva su larga scala.

Questa Guida introduttiva illustra i concetti chiave eseguendo una "Hello World" R script inT-SQL, un'introduzione al **sp_execute_external_script** stored procedure di sistema. Esecuzione di script R è tramite le stored procedure. È possibile usare la [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) stored procedure e pass R creare script come parametro di input come illustrato in questa Guida introduttiva, o eseguire il wrapping dello script R in un [stored procedure di custom](sqldev-in-database-r-for-sql-developers.md). 

## <a name="prerequisites"></a>Prerequisiti

Questo esercizio richiede l'accesso a un'istanza di SQL Server con uno dei già installati i componenti seguenti:

+ [Machine Learning Services di SQL Server 2017](../install/sql-machine-learning-services-windows-install.md), con il linguaggio R installato
+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

  Istanza di SQL Server può essere in una macchina virtuale di Azure o in locale. Tieni presente che la funzionalità di script esterna è disabilitata per impostazione predefinita, pertanto potrebbe essere necessario [abilita la creazione di script esterni](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) e verificare che **Launchpad di SQL Server service** è in esecuzione prima di iniziare.

+ Uno strumento per l'esecuzione di query SQL. È possibile usare qualsiasi applicazione che può connettersi a un database di SQL Server ed eseguire il codice T-SQL. I professionisti SQL è possono usare SQL Server Management Studio (SSMS) o Visual Studio.

Per questa esercitazione, per mostrare come è facile eseguire R all'interno di SQL Server, abbiamo usato la nuova **estensione mssql per Visual Studio Code**. Visual Studio Code è un ambiente di sviluppo gratuito che è possibile eseguire su Linux, macOS o Windows. Il **mssql** estensione è un'estensione leggera per l'esecuzione di query T-SQL. Per ottenere Visual Studio Code, vedere [Download and install Visual Studio Code](https://code.visualstudio.com/Download) (Scaricare e installare Visual Studio Code). Per aggiungere il **mssql** estensione, vedere questo articolo: [Usa l'estensione mssql per Visual Studio Code](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode).

## <a name="connect-to-a-database-and-run-a-hello-world-test-script"></a>Connettersi a un database ed eseguire uno script di test Hello World

1. In Visual Studio Code creare un nuovo file di testo con il nome BasicRSQL.sql.

2. Con il file aperto, premere CTRL+MAIUSC+P (Comando+P su macOS), digitare **sql** per elencare i comandi SQL e selezionare **CONNECT**. Visual Studio Code chiederà di creare un profilo da utilizzare quando ci si connette a un database specifico. Questo è facoltativo, ma rende più semplice per spostarsi tra i database e account di accesso.
    + Scegliere un server o un'istanza in cui è installato R in SQL Server.
    + Usare un account dotato delle autorizzazioni necessarie per creare un nuovo database, eseguire istruzioni SELECT e visualizzare definizioni di tabella.

2. Se la connessione avviene correttamente, dovrebbe essere possibile visualizzare il nome del server e del database sulla barra di stato, insieme alle credenziali correnti. Se la connessione non è riuscita, verificare che il nome del computer e del server siano corretti.

3. Incollare questa istruzione ed eseguirla.

    ```sql
    EXEC sp_execute_external_script
      @language =N'R',
      @script=N'OutputDataSet<-InputDataSet',
      @input_data_1 =N'SELECT 1 AS hello'
      WITH RESULT SETS (([Hello World] int));
    GO
    ```

Gli input per questa stored procedure includono:

+ *@language* parametro definisce l'estensione del linguaggio da chiamare, in questo caso R.
+ *@script* parametro definisce i comandi passati al runtime di R. L'intero script R deve essere incluso in questo argomento come testo Unicode. È anche possibile aggiungere il testo a una variabile di tipo **nvarchar** e quindi chiamare la variabile.
+ *@input_data_1* i dati vengono restituiti dalla query, passata al runtime di R, che restituisce i dati in SQL Server come un frame di dati.
+ SET di risultati di clausola definisce lo schema della tabella dati restituita per SQL Server, aggiunta di "Hello World" come nome della colonna **int** per il tipo di dati.

**Risultati**

![rsql_basictut_hello1](media/rsql-basictut-hello1.PNG)

Se si verificano eventuali errori da questa query, la regola gli eventuali problemi di installazione. Configurazione dopo l'installazione è necessaria per abilitare l'uso delle librerie di codice esterno. Visualizzare [installare SQL Server 2017 servizi di Machine Learning](../install/sql-machine-learning-services-windows-install.md) oppure [installare SQL Server 2016 R Services](../install/sql-r-services-windows-install.md). Analogamente, assicurarsi che il servizio Launchpad sia in esecuzione. 

A seconda dell'ambiente, potrebbe essere necessario abilitare gli account di lavoro R per la connessione a SQL Server, installare librerie di rete aggiuntive, abilitare l'esecuzione remota del codice o riavviare l'istanza dopo aver completato la configurazione. Per altre informazioni, vedere [domande frequenti di eseguire l'aggiornamento e installazione di R Services](../r/upgrade-and-installation-faq-sql-server-r-services.md)

> [!TIP]
> In Visual Studio Code è possibile evidenziare il codice che si vuole eseguire e quindi premere CTRL+MAIUSC+E. Se questo passaggio è troppo difficile da ricordare, è possibile modificarlo. Vedere [Customize the shortcut key bindings](https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts) (Personalizzare le associazioni dei tasti di scelta rapida).
> 
> ![rsql-basictut_hello1code](media/rsql-basictut-hello1code.PNG)
> 

## <a name="next-steps"></a>Passaggi successivi

Ora che si è verificato l'istanza è pronta funzionare con R, esaminiamo più da vicino strutturazione di input e output.

> [!div class="nextstepaction"]
> [Guida rapida: Gestire gli input e output](rtsql-working-with-inputs-and-outputs.md)
