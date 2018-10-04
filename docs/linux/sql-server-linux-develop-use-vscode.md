---
title: Usare l'estensione mssql Visual Studio Code per SQL Server | Microsoft Docs
description: Questa esercitazione illustra come usare l'estensione mssql per Visual Studio Code. Questa estensione consente di modificare ed eseguire script Transact-SQL in Visual Studio Code.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 9766ee75-32d3-4045-82a6-4c7968bdbaa6
ms.custom: sql-linux
ms.openlocfilehash: 7775ece865eea62aad52f1c942c522ad21ed1108
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47686619"
---
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts-for-sql-server"></a>Usare Visual Studio Code per creare ed eseguire script Transact-SQL per SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Questo articolo illustra come usare il **mssql** estensione per Visual Studio Code (VS Code) per lo sviluppo di database di SQL Server.

Visual Studio Code è un editor grafico di codice per Linux, macOS e Windows che supporta le estensioni. Il [**mssql** estensione per il codice di Visual Studio] consente di connettersi a SQL Server, query Transact-SQL (T-SQL) e visualizzare i risultati.

## <a name="install-vs-code"></a>Installare Visual Studio Code
1. Se non è già installato Visual Studio Code [scaricare e installare Visual Studio Code] nel computer.

2. Avviare Visual Studio Code.

## <a name="install-the-mssql-extension"></a>Installare l'estensione mssql
I passaggi seguenti illustrano come installare l'estensione mssql. 

1. Premere **CTRL + MAIUSC + P** (o **F1**) per aprire il riquadro comandi in Visual Studio Code. 

2. Selezionare **Installa estensione** e digitare **mssql**.
   > [!TIP] 
   > Per macOS, il **CMD** chiave è equivalente a **CTRL** chiave in Linux e Windows.

2. Fare clic su Installa **mssql**. 
   
   <img src="./media/sql-server-linux-develop-use-vscode/vscode-extension.png" alt="Install the extension" style="width: 600px;"/>

3. Il **mssql** estensione accetta fino a un minuto per l'installazione. Attendere che il messaggio che indica che è stato installato.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-install-success-notification.png" alt="Installation success notification" style="width: 600px;"/>

   > [!NOTE]
   > Per macOS, è necessario installare OpenSSL. Questo è un prerequisito per.NET Core usati dall'estensione mssql. Seguire le **installare prerequisito** passaggi nel [Istruzioni di.NET Core]. In alternativa, è possibile eseguire i comandi seguenti in Terminal di macOS.
   >
   >   ```bash
   >   brew update
   >   brew install openssl
   >   ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
   >   ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
   >   ```
   
   > [!NOTE]
   > Per Windows 8.1, Windows Server 2012 o versioni precedenti, è necessario scaricare e installare il [Windows 10 Universal C Runtime]. Scaricare e aprire il file zip. Eseguire quindi il programma di installazione (file. msu) come destinazione la configurazione attuale del sistema operativo.

## <a name="create-or-open-a-sql-file"></a>Creare o aprire un file SQL

Il **mssql** estensione Abilita i comandi mssql e T-SQL IntelliSense nell'editor quando la modalità di linguaggio è impostata su **SQL**.

1. Premere **CTRL + N**. Visual Studio Code viene aperto un nuovo file di 'Testo' per impostazione predefinita. 

2. Premere **CTRL + K, M** e modificare la modalità di linguaggio **SQL**. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-language-mode.png" alt="SQL language mode" style="width: 500px;" />

3. In alternativa, aprire un file esistente con l'estensione di file con estensione SQL. La modalità di linguaggio viene automaticamente **SQL** per i file con estensione SQL.  

## <a name="connect-to-sql-server"></a>Connessione a SQL Server

I passaggi seguenti illustrano come connettersi a SQL Server con Visual Studio Code.

1. In Visual Studio Code premere **CTRL+MAIUSC+P** (o **F1**) per aprire il riquadro comandi.

2. Tipo di **sql** per visualizzare i comandi mssql.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-commands.png" alt="mssql commands" style="width: 500px;" />
   

3. Selezionare il **MS SQL: connettere** comando. È possibile digitare semplicemente **sqlcon** , quindi premere **invio**.

4. Selezionare **Crea profilo di connessione**. Verrà creato un profilo di connessione per l'istanza di SQL Server.

5. Seguire le istruzioni per specificare le proprietà di connessione per il nuovo profilo di connessione. Dopo aver specificato ogni valore, premere **INVIO** per continuare. 

   Nella tabella seguente vengono descritte le proprietà di profilo di connessione.

   | Impostazione | Description |
   |-----|-----|
   | **Nome server** | Il nome dell'istanza SQL Server. Per questa esercitazione, usare **localhost** per connettersi all'istanza di SQL Server locale nel computer. Se ci si connette a un Server SQL remoto, immettere il nome del computer di SQL Server di destinazione o il relativo indirizzo IP. Se è necessario specificare una porta per l'istanza di SQL Server, usare una virgola per separarle dal nome. Ad esempio per un server locale in esecuzione sulla porta 1401 immesso **localhost, 1401**. |
   | **[Facoltativo] Nome del database** | Il database che si desidera utilizzare. Ai fini di questa esercitazione, non specificare un database e premere **invio** per continuare. |
   | **Nome utente** | Immettere il nome di un utente con accesso a un database nel server. Per questa esercitazione, usare il valore predefinito **SA** account creato durante l'installazione di SQL Server. |
   | **Password (account di accesso SQL)** | Immettere la password per l'utente specificato. | 
   | **Salvare la password?** | Tipo di **Sì** per salvare la password. In caso contrario, digitare **No** venga richiesta la password ogni volta che viene usato il profilo di connessione. |
   | **[Facoltativo] Immettere un nome per questo profilo** | Il nome del profilo di connessione. Ad esempio, è possibile denominare il profilo **localhost profilo**. 

   > [!Tip] 
   > È possibile creare e modificare i profili di connessione nel file di impostazioni utente (Settings. JSON). Aprire il file di impostazioni selezionando **preferenza** e quindi **delle impostazioni utente** nel menu di Visual Studio Code. Per altre informazioni, vedere [gestire i profili di connessione].

6. Premere il tasto **ESC** per chiudere il messaggio che informa che il profilo è stato creato e connesso.

   > [!TIP]
   > Se si verifica un errore di connessione, provare a diagnosticare il problema dal messaggio di errore nel **Output** pannello in Visual Studio Code (selezionare **Output** sul **visualizzazione** menu). Rivedere poi i [consigli per la risoluzione dei problemi di connessione].

7. Verificare la connessione nella barra di stato.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-connection-status.png" alt="Connection status" style="width: 500px;" />

## <a name="create-a-database"></a>Creazione di un database

1. Nell'editor, digitare **sql** per visualizzare un elenco di frammenti di codice modificabile. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-sql-snippets.png" alt="SQL snippets" style="width: 500px;" />

2. Selezionare **sqlCreateDatabase**.

3. Nel frammento di codice, digitare **TutorialDB** per il nome del database.

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
   
4. Premere **CTRL + MAIUSC + E** per eseguire i comandi Transact-SQL. Visualizzare i risultati nella finestra di query.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-create-database-messages.png" alt="create database messages" style="width: 500px;" />

   > [!TIP]
   > È possibile personalizzare i tasti di scelta rapida per i comandi di estensione mssql. Visualizzare [personalizzare i tasti di scelta rapida].

## <a name="create-a-table"></a>Creare una tabella

1. Rimuove il contenuto della finestra dell'editor.

2. Premere **F1** per visualizzare il riquadro comandi.

3. Tipo di **sql** nel riquadro comandi per visualizzare comandi SQL o tipo **sqluse** per **MS SQL: Use Database** comando.

4. Fare clic su **Database SQL: Use MS**e selezionare il **TutorialDB** database. Questa operazione modificherà il contesto per il nuovo database creato nella sezione precedente.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-use-database.png" alt="use database" style="width: 500px;" />

3. Nell'editor, digitare **sql** per visualizzare i frammenti di codice e quindi selezionare **sqlCreateTable** , quindi premere **immettere**.

4. Nel frammento di codice, digitare **dipendenti** per il nome della tabella.

5. Premere **della scheda**, quindi digitare **dbo** per il nome dello schema.

   > [!NOTE]
   > Dopo aver aggiunto il frammento di codice, è necessario digitare i nomi di tabella e dello schema senza modificare lo stato attivo dalla finestra editor di Visual Studio Code.

6. Modificare il nome della colonna **Column1** al **nome** e **Column2** al **percorso**.

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

## <a name="insert-and-query"></a>Inserimento e query

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
   > Durante la digitazione, usare l'assistenza di T-SQL IntelliSense.
   >   <img src="./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png" alt="TSQL IntelliSense" style="width: 500px;" />

2. Premere **CTRL + MAIUSC + E** per eseguire i comandi. I due comportare la visualizzazione di set nel **risultati** finestra. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png" alt="Results" style="width: 300px;" />

## <a name="view-and-save-the-result"></a>Visualizzare e salvare il risultato

1. Nel **vista** dal menu **Editor di attivazione/disattivazione gruppo Layout** per passa a layout verticale o orizzontale split.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-split.png" alt="Vertical split" style="width: 500px;" />

2. Fare clic sui **risultati** e **messaggi** header del pannello per comprimere ed espandere il pannello.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png" alt="Toggle Messages" style="width: 500px;" />

   > [!TIP]
   > È possibile personalizzare il comportamento predefinito dell'estensione mssql. Visualizzare [personalizzare le opzioni dell'estensione].

2. Fare clic sull'icona di griglia di ingrandimento nella griglia del risultato secondo eseguire lo zoom.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-maximize-grid.png" alt="Maximize grid" style="width: 500px;" />

   > [!NOTE]
   > Quando lo script T-SQL ha due o più le griglie dei risultati, viene visualizzata l'icona di ingrandimento.

3. Aprire il menu di scelta rapida della griglia con il pulsante destro del mouse su una griglia. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-grid-context-menu.png" alt="Context menu" style="width: 500px;" />

4. Selezionare **Seleziona tutto**.

5. Aprire il menu di scelta rapida della griglia e selezionare **Salva con nome JSON** per salvare il risultato in un file con estensione JSON.

6. Specificare un nome per il file JSON. Per questa esercitazione, digitare **employees.json**.

7. Verificare che il file JSON viene salvato e aperto in Visual Studio Code.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-save-as-json.png" alt="Save as Json" style="width: 500px;" />

## <a name="next-steps"></a>Passaggi successivi

In uno scenario reale, è possibile creare uno script che è necessario salvare ed eseguire successiva (per l'amministrazione o come parte di un progetto di sviluppo più grande). In questo caso, è possibile salvare lo script con un **con estensione SQL** estensione.

Se si ha familiarità con T-SQL, vedere [esercitazione: scrittura di istruzioni Transact-SQL] e il [Riferimento Transact-SQL (motore di Database)].

Per altre informazioni sull'utilizzo o aggiunta come contributo all'estensione mssql, vedere [nel wiki di progetto di estensione mssql].

Per altre informazioni sull'uso di Visual Studio Code, vedere la [documentazione di Visual Studio Code](https://code.visualstudio.com/docs).

[**mssql** estensione per il codice di Visual Studio]:https://aka.ms/mssql-marketplace
[Scaricare e installare Visual Studio Code]:https://code.visualstudio.com/Download
[Istruzioni di.NET Core]:https://www.microsoft.com/net/core
[gestire i profili di connessione]:https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles
[consigli per la risoluzione dei problemi di connessione]:./sql-server-linux-troubleshooting-guide.md#connection
[personalizzare i tasti di scelta rapida]:https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts
[Esercitazione: Scrittura di istruzioni Transact-SQL]:https://msdn.microsoft.com/library/ms365303.aspx
[Riferimento Transact-SQL (motore di Database)]:https://msdn.microsoft.com/library/bb510741.aspx
[Visual Studio Code documentation]:https://code.visualstudio.com/docs
[Windows 10 Universal C Runtime]:https://github.com/Microsoft/vscode-mssql/wiki/windows10-universal-c-runtime-requirement
[personalizzare le opzioni dell'estensione]: https://github.com/Microsoft/vscode-mssql/wiki/customize-options
[nel wiki di progetto di estensione mssql]: https://github.com/Microsoft/vscode-mssql/wiki
