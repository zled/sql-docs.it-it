---
title: Introduzione a SQL Server 2017 in Docker | Documenti Microsoft
description: In questa esercitazione introduttiva viene illustrato come usare Docker per eseguire l'immagine contenitore 2017 di SQL Server. Creare e query in un database con sqlcmd.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 95c360dad72a9cd075f2a85d2581dc8021adf941
ms.contentlocale: it-it
ms.lasthandoff: 08/28/2017

---
# <a name="run-the-sql-server-2017-container-image-with-docker"></a>Eseguire l'immagine di SQL Server 2017 contenitore con Docker

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

In questa esercitazione introduttiva usare Docker pull ed eseguire l'immagine di contenitore di SQL Server 2017 RC2 [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/). Connettiti con **sqlcmd** per creare il primo database ed eseguire query.

Questa immagine è costituito da SQL Server in esecuzione in base a 16.04 Ubuntu Linux. E può essere utilizzato con il motore Docker 1.8 + in Linux o in Docker per Mac e Windows.

> [!NOTE]
> Questa Guida introduttiva illustra in modo specifico utilizzando l'immagine mssql-server-linux. L'immagine di Windows non è coperto, ma sono disponibili ulteriori informazioni sul [pagina Hub Docker mssql-server-windows](https://hub.docker.com/r/microsoft/mssql-server-windows/).

## <a id="requirements"></a> Prerequisiti

- Motore docker 1.8 + su qualsiasi supportata di Linux o Docker per Mac e Windows.
- Almeno 4 GB di spazio su disco
- Almeno 4 GB di RAM
- [Requisiti di sistema per SQL Server in Linux](sql-server-linux-setup.md#system).

> [!IMPORTANT]
> Il valore predefinito su Docker per Mac e Docker per Windows è 2 GB per la VM Moby, pertanto è necessario modificarla a 4 GB. Se si eseguono in Mac o Windows, utilizzare le procedure seguenti per aumentare la memoria.

### <a name="increase-docker-memory-to-4-gb-mac"></a>Aumentare la memoria di Docker a 4 GB (Mac)

I passaggi seguenti aumentare la memoria per Docker per Mac a 4 GB.

1. Fare clic sul logo di Docker sulla barra di stato superiore.
1. Selezionare **preferenze**.
1. Spostare l'indicatore di memoria per almeno 4 GB.
1. Fare clic su di **riavviare** pulsante il pulsante della schermata.

### <a name="increase-docker-memory-to-4-gb-windows"></a>Aumentare la memoria di Docker a 4 GB (Windows)

I passaggi seguenti aumentare la memoria di Docker per Windows a 4 GB.

1. Fare doppio clic sull'icona di Docker dalla barra delle applicazioni.
1. Fare clic su **impostazioni** in tale menu.
1. Fare clic su di **Advanced** scheda.
1. Spostare l'indicatore di memoria per almeno 4 GB.
1. Fare clic su di **applica** pulsante.

## <a name="pull-and-run-the-container-image"></a>Effettuare il pull ed eseguire l'immagine del contenitore

1. Effettuare il pull dell'immagine contenitore dall'Hub Docker.

    ```bash
    docker pull microsoft/mssql-server-linux
    ```

    > [!TIP]
    > Per Linux, a seconda della configurazione di sistema e utente, è necessario anteporre ogni `docker` con `sudo`.

1. Per eseguire l'immagine contenitore con Docker, è possibile utilizzare il comando seguente da una shell bash (Linux/macOS):

    ```bash
    docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -e 'MSSQL_PID=Developer' --cap-add SYS_PTRACE -p 1401:1433 -d microsoft/mssql-server-linux
    ```

    Se si usa Docker per Windows, utilizzare il comando seguente da un comando-prompt di PowerShell con privilegi elevati:

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d microsoft/mssql-server-linux
    ```

    > [!NOTE]
    > L'unica differenza tra l'esempio bash (Linux/macOS) e l'esempio di PowerShell (Windows) è tra virgolette singole e virgolette doppie le variabili di ambiente. Il comando docker run ha esito negativo se si usa quella sbagliata. Il resto di questo argomento vengono forniti per comodità bash e blocchi di codice di PowerShell. Se è presente solo un esempio, funziona in tutte le piattaforme, tra cui Windows.

    Nella tabella seguente fornisce una descrizione dei parametri nella precedente `docker run` esempio:

    | Parametro | Description |
    |-----|-----|
    | **-e ' ACCEPT_EULA = Y'** |  Impostare il **ACCEPT_EULA** variabile qualsiasi valore per confermare l'accettazione del [il contratto di licenza dell'utente finale](http://go.microsoft.com/fwlink/?LinkId=746388). È necessario impostare per l'immagine di SQL Server. |
    | **-e ' MSSQL_SA_PASSWORD =\<YourStrong! Passw0rd\>'** | Specificare una password complessa è composta da almeno 8 caratteri e soddisfa [requisiti di password del Server SQL](../relational-databases/security/password-policy.md). È necessario impostare per l'immagine di SQL Server. |
    | **-e ' MSSQL_PID = sviluppatore '** | Specifica la chiave edition o prodotto. In questo esempio, l'edizione Developer liberamente con licenza viene utilizzato per il test non di produzione. Per altri valori, vedere [le impostazioni di configurazione SQL Server con le variabili di ambiente in Linux](sql-server-linux-configure-environment-variables.md). |
    | **-aggiunta SYS_PTRACE perno** | Aggiunge la funzionalità di Linux per tracciare un processo. Ciò consente a SQL Server generare dump in un'eccezione. |
    | **1401:1433 -p** | Mapping di una porta TCP per l'ambiente host (il primo valore) con una porta TCP nel contenitore (secondo valore). In questo esempio, SQL Server è in ascolto sulla porta TCP 1433 nel contenitore e questa funzionalità è esposta alla porta, 1401, nell'host. |
    | **Microsoft/mssql-server-per linux** | L'immagine di contenitore di SQL Server per Linux. Se non diversamente specificato, l'impostazione predefinita il **più recente** immagine. |

1. Per visualizzare i contenitori di Docker, usare il `docker ps` comando.

    ```bash
    docker ps -a
    ```

    Verrà visualizzato l'output simile al seguente schermata:

    ![Output del comando di docker ps](./media/sql-server-linux-setup-docker/docker-ps-command.png)

1. Se il **stato** colonna viene visualizzato lo stato **backup**, quindi viene eseguito SQL Server nel contenitore e in ascolto sulla porta specificata nella **porte** colonna. Se il **stato** colonna per il contenitore di SQL Server viene illustrata **Exited**, vedere il [sezione della Guida alla configurazione di risoluzione dei problemi](sql-server-linux-configure-docker.md#troubleshooting).

Esistono due utile `docker run` opzioni non utilizzate nell'esempio precedente, per semplicità. Il `-h` parametro (nome host) cambia il nome interno del contenitore su un valore personalizzato. Si tratta del nome che verrà restituito nella query Transact-SQL seguente:

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

È inoltre possibile trovare il `--name` parametro utile per assegnare un nome di contenitore anziché un nome di contenitore generato. Impostazione `-h` e `--name` sullo stesso valore è un buon metodo per identificare facilmente il contenitore di destinazione.

## <a name="change-the-sa-password"></a>Modificare la password SA

L'account SA è un amministratore di sistema nell'istanza di SQL Server che viene creato durante l'installazione. Dopo aver creato il contenitore di SQL Server, il `MSSQL_SA_PASSWORD` variabile di ambiente specificata sia individuabile eseguendo `echo $MSSQL_SA_PASSWORD` nel contenitore. Per motivi di sicurezza, modificare la password dell'amministratore di sistema.

1. Scegliere una password complessa da utilizzare per l'utente SA.

1. Utilizzare `docker exec` eseguire **sqlcmd** per modificare la password tramite Transact-SQL. Sostituire `<Old Password>` e `<New Password>` con i valori della password.

> ```bash
> docker exec -it <Container ID> /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<Old Password>' -Q 'ALTER LOGIN SA WITH PASSWORD="<New Password>";'
> ```

## <a name="connect-to-sql-server"></a>Connessione a SQL Server

La procedura seguente utilizza lo strumento da riga di comando di SQL Server, **sqlcmd**, all'interno del contenitore per la connessione a SQL Server.

1. Utilizzare il `docker exec -it` comando per avviare una shell bash interattiva all'interno del contenitore in esecuzione. Nell'esempio seguente `e69e056c702d` è l'ID del contenitore.

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > Sempre necessario specificare l'id intero contenitore. È necessario solo specificare un numero di caratteri sufficiente per identificarla in modo univoco. In questo esempio, potrebbe pertanto essere sufficienti per utilizzare `e6` o `e69` anziché l'id completo.

1. Una volta all'interno del contenitore, la connessione in locale con sqlcmd. SQLCMD non è il percorso per impostazione predefinita, è necessario specificare il percorso completo.

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

   > [!TIP]
   > È possibile omettere la password nella riga di comanda perché sia richiesto di essere immessa.

1. Se la connessione viene eseguita correttamente, il prompt dei comandi **sqlcmd** sarà: `1>`.

## <a name="create-and-query-data"></a>Creare i dati e recuperarli tramite query

Nelle sezioni seguenti viene descritto l'uso di **sqlcmd** e Transact-SQL per creare un nuovo database, aggiungere dati ed eseguire una query semplice.

### <a name="create-a-new-database"></a>Creare un nuovo database

La seguente procedura consente di creare un nuovo database denominato `TestDB`.

1. Dal prompt dei comandi **sqlcmd** incollare il comando seguente di Transact-SQL per creare un database di test:

   ```sql
   CREATE DATABASE TestDB
   ```

1. Nella riga successiva scrivere una query perché vengano restituiti i nomi di tutti database nel server:

   ```sql
   SELECT Name from sys.Databases
   ```

1. I due comandi precedenti non sono stati eseguiti immediatamente. È necessario digitare `GO` in una nuova riga per eseguire i comandi precedenti:

   ```sql
   GO
   ```

### <a name="insert-data"></a>Inserire i dati

Creare poi una nuova tabella `Inventory` e inserire due nuove righe.

1. Dal prompt dei comandi **sqlcmd** spostare il contesto nel nuovo database `TestDB`:

   ```sql
   USE TestDB
   ```

1. Creare una nuova tabella denominata `Inventory`:

   ```sql
   CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
   ```

1. Inserire i dati nella nuova tabella:

   ```sql
   INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
   ```

1. Digitare `GO` per eseguire i comandi precedenti:

   ```sql
   GO
   ```

### <a name="select-data"></a>Selezionare i dati

A questo punto, eseguire una query per restituire i dati dalla tabella `Inventory`.

1. Dal prompt dei comandi **sqlcmd** immettere una query che restituisca le righe dalla tabella `Inventory` che ne contiene oltre 152:

   ```sql
   SELECT * FROM Inventory WHERE quantity > 152;
   ```

1. Eseguire il comando:

   ```sql
   GO
   ```

### <a name="exit-the-sqlcmd-command-prompt"></a>Uscire dal prompt dei comandi sqlcmd

1. Per terminare la sessione **sqlcmd**, digitare `QUIT`:

   ```sql
   QUIT
   ```

1. Per uscire dal prompt interattivo nel contenitore, digitare `exit`. Il contenitore continua a essere eseguito dopo la chiusura della shell bash interattivo.

## <a name="connect-from-outside-the-container"></a>Connettersi dall'esterno del contenitore

È possibile anche connettersi all'istanza di SQL Server nel computer Docker da qualsiasi strumento esterno macOS, Windows o Linux che supporta le connessioni SQL.

Utilizzare i passaggi seguenti **sqlcmd** di fuori del contenitore per la connessione a SQL Server in esecuzione nel contenitore. Questi passaggi si presuppongono di aver già gli strumenti da riga di comando di SQL Server installati di fuori del contenitore. Le stesse entità si applicano quando si utilizzano altri strumenti, ma il processo di connessione è univoco per ogni strumento.

1. Individuare l'indirizzo IP per il computer che ospita il contenitore. In Linux, usare **ifconfig** o **ip addr**. In Windows, utilizzare **ipconfig**.

1. Esecuzione di sqlcmd che specifica l'indirizzo IP e la porta mappata alla porta 1433 nel contenitore. In questo esempio riguarda la porta 1401 nel computer host.

   ```bash
   sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
   ```

   ```PowerShell
   sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
   ```

1. Eseguire i comandi Transact-SQL. Al termine, digitare `QUIT`.

Altri strumenti comuni per connettersi a SQL Server includono:

- [Codice di Visual Studio](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) in Windows](sql-server-linux-develop-use-ssms.md)

## <a name="next-steps"></a>Passaggi successivi

Per esplorare altri scenari, ad esempio l'esecuzione di più contenitori, persistenza dei dati e troublehshooting, vedere [configurare SQL Server 2017 le immagini contenitore Docker](sql-server-linux-configure-docker.md).

Inoltre, estrarre il [repository GitHub mssql docker](https://github.com/Microsoft/mssql-docker) per le risorse, commenti e suggerimenti e problemi noti.

