---
title: Utilizzare l'estensione di Visual Studio Code mssql per SQL Server | Documenti Microsoft
description: In questa esercitazione viene illustrato come utilizzare l'estensione mssql per il codice di Visual Studio. Questa estensione consente di modificare ed eseguire script Transact-SQL nel codice di Visual Studio.
author: erickangMSFT
ms.author: erickang
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9766ee75-32d3-4045-82a6-4c7968bdbaa6
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a4b2f82ac904d58604b0c27d46624995878e8a35
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts-for-sql-server"></a>Usare codice di Visual Studio per creare ed eseguire script Transact-SQL per SQL Server

In questo argomento viene illustrato come utilizzare il **mssql** estensione per Visual Studio Code (codice di Visual Studio) per lo sviluppo di database di SQL Server.

Codice di Visual Studio è un editor di codice con interfaccia grafica per Linux, macOS e Windows che supporta le estensioni. Il [**mssql** estensione per il codice di Visual Studio]  consente di connettersi a SQL Server, query Transact-SQL (T-SQL) e visualizzare i risultati.

## <a name="install-vs-code"></a>Installare Visual Studio Code
1. Se non è già installato Visual Studio Code, [scaricare e installare Visual Studio Code] nel computer.

2. Avviare Visual Studio Code.

## <a name="install-the-mssql-extension"></a>Installare l'estensione mssql
I passaggi seguenti illustrano come installare l'estensione mssql. 

1. Premere **CTRL + MAIUSC + P** (o **F1**) per aprire il riquadro comandi in Visual Studio Code. 

2. Selezionare **installare estensione** e tipo **mssql**.
   > [!TIP] 
   > Per macOS, il **CMD** chiave è equivalente a **CTRL** su Linux e Windows.

2. Fare clic su Installa **mssql**. 
   
   <img src="./media/sql-server-linux-develop-use-vscode/vscode-extension.png" alt="Install the extension" style="width: 600px;"/>

3. Il **mssql** estensione accetta fino a un minuto. Attendere che il prompt dei comandi indicante che è stato installato correttamente.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-install-success-notification.png" alt="Installation success notification" style="width: 600px;"/>

   > [!NOTE]
   > Per macOS, è necessario installare OpenSSL. Questo è un prerequisito per .net Core usati dall'estensione mssql. Seguire il **installare prerequisiti** passaggi il [.Net Core istruzioni]. In alternativa, è possibile eseguire i comandi seguenti nel macOS Terminal.
   >
   >   ```bash
   >   brew update
   >   brew install openssl
   >   ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
   >   ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
   >   ```
   
   > [!NOTE]
   > Per Windows 8.1, Windows Server 2012 o versioni precedenti, è necessario scaricare e installare il [Windows 10 Universal C Runtime]. Scaricare e aprire il file zip. Quindi eseguire il programma di installazione (file. msu) per la configurazione del sistema operativo corrente.

## <a name="create-or-open-a-sql-file"></a>Creare o aprire un file SQL

Il **mssql** estensione consente mssql comandi e T-SQL IntelliSense nell'editor quando la modalità di lingua è impostata su **SQL**.

1. Premere **CTRL + N**. Codice di Visual Studio apre un nuovo file "Testo normale" per impostazione predefinita. 

2. Premere **CTRL + K, M** e cambiare la modalità di linguaggio per **SQL**. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-language-mode.png" alt="SQL language mode" style="width: 500px;" />

3. In alternativa, aprire un file esistente con estensione di file con estensione SQL. La modalità di linguaggio è automaticamente **SQL** per i file con estensione SQL.  

## <a name="connect-to-sql-server"></a>Connessione a SQL Server

La procedura seguente viene illustrato come connettersi a SQL Server con Visual Studio Code.

1. Nel codice di Visual Studio, premere **CTRL + MAIUSC + P** (o **F1**) per aprire il riquadro comandi.

2. Tipo **sql** per visualizzare i comandi mssql.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-commands.png" alt="mssql commands" style="width: 500px;" />
   

3. Selezionare il **MS SQL: connettersi** comando. È possibile digitare semplicemente **sqlcon** e premere **invio**.

4. Selezionare **Crea profilo di connessione**. Verrà creato un profilo di connessione per l'istanza di SQL Server.

5. Seguire le istruzioni per specificare le proprietà di connessione per il nuovo profilo di connessione. Dopo aver specificato ogni valore, premere **invio** per continuare. 

   Nella tabella seguente vengono descritte le proprietà di profilo di connessione.

   | Impostazione | Description |
   |-----|-----|
   | **Nome server** | Il nome dell'istanza SQL Server. Per questa esercitazione, usare **localhost** per connettersi all'istanza di SQL Server locale nel computer. Se la connessione a un Server SQL remoto, immettere il nome del computer SQL Server di destinazione o il relativo indirizzo IP. |
   | **[Facoltativo] Nome del database** | Il database che si desidera utilizzare. Ai fini di questa esercitazione, non specificare un database e premere **invio** per continuare. |
   | **Nome utente** | Immettere il nome di un utente con accesso a un database nel server. Per questa esercitazione, usare il valore predefinito **SA** account creato durante l'installazione di SQL Server. |
   | **Password (account di accesso SQL)** | Immettere la password per l'utente specificato. | 
   | **Salva Password?** | Tipo **Sì** per salvare la password. In caso contrario, digitare **n** chiesto di immettere la password ogni volta che viene utilizzato il profilo di connessione. |
   | **[Facoltativo] Immettere un nome per questo profilo** | Il nome del profilo di connessione. Ad esempio, è possibile specificare il nome del profilo **profilo localhost**. 

   > [!Tip] 
   > È possibile creare e modificare i profili di connessione nel file di impostazioni utente (Settings). Aprire il file di impostazioni selezionando **preferenza** e quindi **impostazioni utente** nel menu di Visual Studio Code. Per ulteriori informazioni, vedere [gestire i profili di connessione].

6. Premere il **ESC** tasto per chiudere il messaggio informativo che informa che il profilo viene creato e collegato.

   > [!TIP]
   > Se si verifica un errore di connessione, tenta di diagnosticare il problema dal messaggio di errore nel **Output** pannello in Visual Studio Code (selezionare **Output** sul **vista** menu). Esaminare il [connessione indicazioni risoluzione].

7. Verificare la connessione nella barra di stato.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-connection-status.png" alt="Connection status" style="width: 500px;" />

## <a name="create-a-database"></a>Creazione di un database

1. Nell'editor, digitare **sql** per visualizzare un elenco di frammenti di codice modificabile. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-sql-snippets.png" alt="SQL snippets" style="width: 500px;" />

2. Selezionare **sqlCreateDatabase**.

3. Nel frammento di tipo **TutorialDB** per il nome del database.

   ```sql
   USE master
   GO
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
   CREATE DATABASE [TutorialDB]
   GO
   ```
   
4. Premere **CTRL + MAIUSC + E** per eseguire i comandi Transact-SQL. Visualizzare i risultati nella finestra query.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-create-database-messages.png" alt="create database messages" style="width: 500px;" />

   > [!TIP]
   > È possibile personalizzare i tasti di scelta rapida per i comandi di estensione mssql. Vedere [personalizzare i tasti di scelta rapida].

## <a name="create-a-table"></a>Creare una tabella

1. Rimuovere il contenuto della finestra dell'editor.

2. Premere **F1** per visualizzare il riquadro comandi.

3. Tipo **sql** nella tavolozza di comando per visualizzare comandi SQL o tipo **sqluse** per **MS SQL: Use Database** comando.

4. Fare clic su **MS SQL: Use Database**e selezionare il **TutorialDB** database. Questa modifica il contesto per il nuovo database creato nella sezione precedente.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-use-database.png" alt="use database" style="width: 500px;" />

3. Nell'editor, digitare **sql** per visualizzare i frammenti di codice e quindi selezionare **sqlCreateTable** e premere **immettere**.

4. Nel frammento di tipo **dipendenti** per il nome della tabella.

5. Premere **scheda**, quindi digitare **dbo** per il nome dello schema.

   > [!NOTE]
   > Dopo aver aggiunto il frammento di codice, è necessario digitare i nome dello schema e di tabella senza modificare lo stato attivo dall'editor di Visual Studio Code.

6. Modificare il nome di colonna per **Column1** a **nome** e **Column2** a **percorso**.

   ```sql
   -- Create a new table called 'Employees' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Employees', 'U') IS NOT NULL
   DROP TABLE dbo.Employees
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Employees
   (
      EmployeesId        INT    NOT NULL   PRIMARY KEY, -- primary key column
      Name      [NVARCHAR](50)  NOT NULL,
      Location   [NVARCHAR](50)  NOT NULL
   );
   GO
   ```

7. Premere **CTRL + MAIUSC + E** per creare la tabella.

## <a name="insert-and-query"></a>Query e inserimento

1. Aggiungere le istruzioni seguenti per inserire quattro righe nella **dipendenti** tabella. Selezionare quindi tutte le righe.

   ```sql
   -- Insert rows into table 'Employees'
   INSERT INTO Employees
      ([EmployeesId],[Name],[Location])
   VALUES
      ( 1, N'Jared', N'Australia'),
      ( 2, N'Nikita', N'India'),
      ( 3, N'Tom', N'Germany'),
      ( 4, N'Jake', N'United States')   
   GO   
   -- Query the total count of employees
   SELECT COUNT(*) as EmployeeCount FROM dbo.Employees;
   -- Query all employee information
   SELECT e.EmployeesId, e.Name, e.Location 
   FROM dbo.Employees as e
   GO
   ```

   > [!TIP]
   > Durante la digitazione, utilizzare l'assistenza di T-SQL IntelliSense.
   >   <img src="./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png" alt="TSQL IntelliSense" style="width: 500px;" />

2. Premere **CTRL + MAIUSC + E** per eseguire i comandi. I due comportare la visualizzazione di set nel **risultati** finestra. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png" alt="Results" style="width: 300px;" />

## <a name="view-and-save-the-result"></a>Consente di visualizzare e salvare il risultato

1. Nel **vista** dal menu **attiva/disattiva Editor gruppo Layout** per passare al layout di divisione verticale o orizzontale.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-split.png" alt="Vertical split" style="width: 500px;" />

2. Fare clic su di **risultati** e **messaggi** intestazione pannello per comprimere ed espandere il pannello.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png" alt="Toggle Messages" style="width: 500px;" />

   > [!TIP]
   > È possibile personalizzare il comportamento predefinito dell'estensione mssql. Vedere [personalizzare le opzioni di estensione].

2. Fare clic sull'icona griglia ingrandimento della griglia di risultati secondo per eseguire lo zoom avanti.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-maximize-grid.png" alt="Maximize grid" style="width: 500px;" />

   > [!NOTE]
   > Quando lo script T-SQL dispone di due o più griglie dei risultati, viene visualizzata l'icona di ingrandimento.

3. Aprire il menu di scelta rapida della griglia con il pulsante destro del mouse su una griglia. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-grid-context-menu.png" alt="Context menu" style="width: 500px;" />

4. Selezionare **Seleziona tutto**.

5. Aprire il menu di scelta rapida della griglia e selezionare **salvare come JSON** per salvare il risultato in un file con estensione JSON.

6. Specificare un nome di file per il file JSON. Per questa esercitazione, digitare **employees.json**.

7. Verificare che il file JSON viene salvato e aperto in Visual Studio Code.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-save-as-json.png" alt="Save as Json" style="width: 500px;" />

## <a name="next-steps"></a>Passaggi successivi

In uno scenario reale, è possibile creare uno script che è necessario salvare ed eseguire versioni successive (per l'amministrazione o come parte di un progetto di sviluppo più grande). In questo caso, è possibile salvare lo script con un **SQL** estensione.

Se si ha familiarità con T-SQL, vedere [esercitazione: scrittura di istruzioni Transact-SQL] e [riferimento a Transact-SQL (motore di Database)].

Per ulteriori informazioni su utilizzando o che hanno contribuito all'estensione mssql, vedere [wiki di progetto di estensione mssql].

Per ulteriori informazioni sull'utilizzo di codice di Visual Studio, vedere il [documentazione di Visual Studio Code](https://code.visualstudio.com/docs).

[**mssql** estensione per il codice di Visual Studio]:https://aka.ms/mssql-marketplace
[scaricare e installare Visual Studio Code]:https://code.visualstudio.com/Download
[.Net Core istruzioni]:https://www.microsoft.com/net/core
[gestire i profili di connessione]:https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles
[connessione indicazioni risoluzione]:./sql-server-linux-troubleshooting-guide.md#connection
[personalizzare i tasti di scelta rapida]:https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts
[esercitazione: scrittura di istruzioni Transact-SQL]:https://msdn.microsoft.com/library/ms365303.aspx
[riferimento a Transact-SQL (motore di Database)]:https://msdn.microsoft.com/library/bb510741.aspx
[Visual Studio Code documentation]:https://code.visualstudio.com/docs
[Windows 10 Universal C Runtime]:https://github.com/Microsoft/vscode-mssql/wiki/windows10-universal-c-runtime-requirement
[personalizzare le opzioni di estensione]: https://github.com/Microsoft/vscode-mssql/wiki/customize-options
[wiki di progetto di estensione mssql]: https://github.com/Microsoft/vscode-mssql/wiki

