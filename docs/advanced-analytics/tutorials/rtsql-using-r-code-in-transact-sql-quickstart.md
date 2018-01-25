---
title: Utilizzo di codice R in Transact-SQL (R nella Guida rapida SQL) | Documenti Microsoft
ms.custom: SQL2016_New_Updated
ms.date: 08/20/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 4e6fe30d-a105-4d5b-bc05-5e5204753847
caps.latest.revision: "36"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 9c0896ca67df3d8000fae8f3cd3d336b047ee481
ms.sourcegitcommit: d7dcbcebbf416298f838a39dd5de6a46ca9f77aa
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="using-r-code-in-transact-sql-r-in-sql-quickstart"></a>Utilizzo di codice R in Transact-SQL (R nella Guida rapida SQL)

Questa esercitazione descrive il meccanismo di base per la chiamata di uno script R da una stored procedure T-SQL.

**Si apprenderà**

+ Come incorporare R in una funzione T-SQL
+ Alcuni suggerimenti per l'utilizzo di SQL e R dati e i tipi di oggetti dati
+ Come creare un modello semplice e salvarlo in SQL Server
+ Come creare stime e un tracciato di R usando il modello

**Tempo stimato**

30 minuti, configurazione esclusa

## <a name="prerequisites"></a>Prerequisiti

Con uno dei seguenti già installato, è necessario avere accesso a un'istanza di SQL Server:

+ Servizi SQL Server 2017 Machine Learning, con il linguaggio R installato
+ SQL Server 2016 R Services

Istanza di SQL Server può essere in una macchina virtuale di Azure o in locale. Solo tenere presente che la funzionalità di scripting esterna è disabilitata per impostazione predefinita, pertanto potrebbe essere necessario eseguire alcuni passaggi aggiuntivi per ottenere lo stesso risultato.

Per eseguire query SQL che includono script R, è possibile utilizzare qualsiasi altra applicazione in grado di connettersi a un database e di eseguire il codice T-SQL. I professionisti SQL è possono utilizzare SQL Server Management Studio (SSMS) o Visual Studio.

Per questa esercitazione, per mostrare come sia facile eseguire R all'interno di SQL Server, abbiamo utilizzato il nuovo **mssql estensione per il codice di Visual Studio**. Visual Studio Code è un ambiente di sviluppo gratuito che è possibile eseguire in Windows, Linux o Mac OS. Il **mssql** estensione è un'estensione semplice per l'esecuzione di query T-SQL. Per installarla, vedere questo articolo: [Use the mssql extension for Visual Studio Code](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode) (Usare l'estensione mssql per Visual Studio Code).

## <a name="connect-to-a-database-and-run-a-hello-world-test-script"></a>Connettersi a un database ed eseguire uno script di test Hello World

1. In Visual Studio Code creare un nuovo file di testo con il nome BasicRSQL.sql.
2. Con il file aperto, premere CTRL+MAIUSC+P (Comando+P su macOS), digitare **sql** per elencare i comandi SQL e selezionare **CONNECT**. Codice di Visual Studio viene richiesto di creare un profilo da utilizzare quando ci si connette a un database specifico. È facoltativo, ma rende più semplice passare tra i database e account di accesso.
    + Scegliere un server o un'istanza in cui è installato R in SQL Server.
    + Usare un account dotato delle autorizzazioni necessarie per creare un nuovo database, eseguire istruzioni SELECT e visualizzare definizioni di tabella.
2. Se la connessione avviene correttamente, dovrebbe essere possibile visualizzare il nome del server e del database sulla barra di stato, insieme alle credenziali correnti. Se la connessione non è riuscita, verificare che il nome del computer e del server siano corretti.
3. Incollare questa istruzione ed eseguirla.

    ```sql
    EXEC sp_execute_external_script
      @language =N'R',
      @script=N'OutputDataSet<-InputDataSet',
      @input_data_1 =N'SELECT 1 AS hello'
      WITH RESULT SETS (([hello] int not null));
    GO
    ```

    In Visual Studio Code è possibile evidenziare il codice che si vuole eseguire e quindi premere CTRL+MAIUSC+E. Se questo passaggio è troppo difficile da ricordare, è possibile modificarlo. Vedere [Customize the shortcut key bindings](https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts) (Personalizzare le associazioni dei tasti di scelta rapida).

    ![rsql-basictut_hello1code](media/rsql-basictut-hello1code.PNG)

**Risultati**

![rsql_basictut_hello1](media/rsql-basictut-hello1.PNG)

## <a name="troubleshooting"></a>Risoluzione dei problemi

+ Se si verificano errori di questa query, l'installazione potrebbe essere incompleta. Dopo aver aggiunto la funzionalità usando l'Installazione guidata di SQL Server, è necessario eseguire alcuni passaggi aggiuntivi per abilitare l'uso di librerie di codice esterne.  Vedere [Configurare SQL Server R Services](../r/set-up-sql-server-r-services-in-database.md).

+ Assicurarsi che il servizio Launchpad sia in esecuzione. A seconda dell'ambiente, potrebbe essere necessario abilitare gli account di lavoro R per la connessione a SQL Server, installare librerie di rete aggiuntive, abilitare l'esecuzione remota del codice o riavviare l'istanza dopo aver completato la configurazione. Vedere [R Services Installation and Upgrade FAQ](../r/upgrade-and-installation-faq-sql-server-r-services.md) (Domande frequenti sull'installazione e l'aggiornamento di R Services)

+ Per ottenere Visual Studio Code, vedere [Download and install Visual Studio Code](https://code.visualstudio.com/Download) (Scaricare e installare Visual Studio Code).

## <a name="next-lesson"></a>Lezione successiva

Ora che l'istanza è pronto per funzionare con R, è possibile iniziare subito.

Lezione 1: [utilizzo di input e output](rtsql-working-with-inputs-and-outputs.md)

Lezione 2: [R e SQL dati e i tipi di oggetti dati](rtsql-r-and-sql-data-types-and-data-objects.md)

Lezione 3: [R di uso delle funzioni con i dati di SQL Server](rtsql-using-r-functions-with-sql-server-data.md)

Lezione 4: [creare un modello predittivo](rtsql-create-a-predictive-model-r.md)

Lezione 5: [Predict ed eseguire il tracciato da modello](rtsql-predict-and-plot-from-model.md)
