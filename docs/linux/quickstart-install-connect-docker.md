---
title: Introduzione a SQL Server 2017 in Docker | Documenti Microsoft
description: Questa Guida introduttiva viene illustrato come usare Docker per eseguire l'immagine contenitore 2017 di SQL Server. Creare e query in un database con sqlcmd.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/31/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.workload: Active
ms.openlocfilehash: 0fcd5cefc02359d407b1799e4cc31ed5afa3c818
ms.sourcegitcommit: 73043fe1ac5d60b67e33b44053c0a7733b98bc3d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/23/2017
---
# <a name="run-the-sql-server-2017-container-image-with-docker"></a>Eseguire l'immagine di SQL Server 2017 contenitore con Docker

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

In questa Guida rapida, usare Docker pull ed eseguire l'immagine di contenitore di SQL Server 2017, [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/). Connettiti con **sqlcmd** per creare il primo database ed eseguire query.

Questa immagine è costituito da SQL Server in esecuzione in base a 16.04 Ubuntu Linux. E può essere utilizzato con il motore Docker 1.8 + in Linux o in Docker per Mac e Windows.

> [!NOTE]
> Questa Guida introduttiva illustra in modo specifico tramite il servizio mssql-server -**linux** immagine. L'immagine di Windows non è coperto, ma sono disponibili ulteriori informazioni sul [pagina Hub Docker mssql-server-windows-developer](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/).

## <a id="requirements"></a> Prerequisites

- Motore docker 1.8 + su qualsiasi supportata di Linux o Docker per Mac e Windows. Per ulteriori informazioni, vedere [installare Docker](https://docs.docker.com/engine/installation/).
- Almeno 2 GB di spazio su disco
- Almeno 2 GB di RAM
- [Requisiti di sistema per SQL Server in Linux](sql-server-linux-setup.md#system).

## <a name="pull-and-run-the-container-image"></a>Effettuare il pull ed eseguire l'immagine del contenitore

1. Effettuare il pull dell'immagine di SQL Server per Linux 2017 contenitore dall'Hub Docker.

   ```bash
   sudo docker pull microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker pull microsoft/mssql-server-linux:2017-latest
   ```

   Il comando precedente effettua il pull dell'immagine di contenitore 2017 di SQL Server più recente. Se si desidera effettuare il pull di un'immagine specifica, aggiungere i due punti e il nome del tag (ad esempio, `microsoft/mssql-server-linux:2017-GA`). Per visualizzare tutte le immagini disponibili, vedere [pagina dell'hub Docker mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/).

1. Per eseguire l'immagine contenitore con Docker, è possibile utilizzare il comando seguente da una shell bash (Linux/macOS) o un prompt dei comandi di PowerShell con privilegi elevati.

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      -p 1401:1433 --name sql1 \
      -d microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1401:1433 --name sql1 `
      -d microsoft/mssql-server-linux:2017-latest
   ```

   > [!NOTE]
   > Per impostazione predefinita, verrà creato un contenitore con l'edizione Developer di SQL Server 2017. Il processo di esecuzione le edizioni di produzione in contenitori è leggermente diverso. Per ulteriori informazioni, vedere [eseguire produzione immagini contenitore](sql-server-linux-configure-docker.md#production).

   Nella tabella seguente fornisce una descrizione dei parametri nella precedente `docker run` esempio:

   | Parametro | Description |
   |-----|-----|
   | **-e ' ACCEPT_EULA = Y'** |  Impostare il **ACCEPT_EULA** variabile qualsiasi valore per confermare l'accettazione del [il contratto di licenza dell'utente finale](http://go.microsoft.com/fwlink/?LinkId=746388). È necessario impostare per l'immagine di SQL Server. |
   | **-e ' MSSQL_SA_PASSWORD =\<YourStrong! Passw0rd\>'** | Specificare una password complessa è composta da almeno 8 caratteri e soddisfa le [requisiti delle password di SQL Server](../relational-databases/security/password-policy.md). È necessario impostare per l'immagine di SQL Server. |
   | **1401:1433 -p** | Mapping di una porta TCP per l'ambiente host (il primo valore) con una porta TCP nel contenitore (secondo valore). In questo esempio, SQL Server è in ascolto sulla porta TCP 1433 nel contenitore e questa funzionalità è esposta alla porta, 1401, nell'host. |
   | **-nome sql1** | Specificare un nome personalizzato per il contenitore invece uno generato casualmente. Se si esecuzione più di un contenitore, è possibile riutilizzare questo stesso nome. |
   | **mssql/Microsoft-server-linux:2017-più recente** | L'immagine di SQL Server per Linux 2017 contenitore. |

1. Per visualizzare i contenitori di Docker, usare il `docker ps` comando.

   ```bash
   sudo docker ps -a
   ```

   ```PowerShell
   docker ps -a
   ```

   Verrà visualizzato l'output simile al seguente schermata:

   ![Output del comando di docker ps](./media/sql-server-linux-setup-docker/docker-ps-command.png)

1. Se il **stato** colonna viene visualizzato lo stato **backup**, quindi viene eseguito SQL Server nel contenitore e in ascolto sulla porta specificata nella **porte** colonna. Se il **stato** colonna per il contenitore di SQL Server viene illustrata **Exited**, vedere il [sezione della Guida alla configurazione di risoluzione dei problemi](sql-server-linux-configure-docker.md#troubleshooting).

Il `-h` è utile anche il parametro (nome host), ma non viene utilizzato in questa esercitazione per motivi di semplicità. Questa modifica il nome interno del contenitore su un valore personalizzato. Si tratta del nome che verrà restituito nella query Transact-SQL seguente:

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

Impostazione `-h` e `--name` sullo stesso valore è un buon metodo per identificare facilmente il contenitore di destinazione.

## <a name="change-the-sa-password"></a>Modificare la password SA

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="connect-to-sql-server"></a>Connessione a SQL Server

La procedura seguente utilizza lo strumento da riga di comando di SQL Server, **sqlcmd**, all'interno del contenitore per la connessione a SQL Server.

1. Utilizzare il `docker exec -it` comando per avviare una shell bash interattiva all'interno del contenitore in esecuzione. Nell'esempio seguente `sql1` nome specificato da di `--name` parametro al momento della creazione del contenitore.

   ```bash
   sudo docker exec -it sql1 "bash"
   ```

   ```PowerShell
   docker exec -it sql1 "bash"
   ```

1. Una volta all'interno del contenitore, la connessione in locale con sqlcmd. SQLCMD non è il percorso per impostazione predefinita, è necessario specificare il percorso completo.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourNewStrong!Passw0rd>'
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

## <a id="connectexternal"></a>Connettersi dall'esterno del contenitore

È possibile anche connettersi all'istanza di SQL Server nel computer Docker da qualsiasi strumento esterno macOS, Windows o Linux che supporta le connessioni SQL.

Utilizzare i passaggi seguenti **sqlcmd** di fuori del contenitore per la connessione a SQL Server in esecuzione nel contenitore. Questi passaggi si presuppongono di aver già gli strumenti da riga di comando di SQL Server installati di fuori del contenitore. Le stesse entità si applicano quando si utilizzano altri strumenti, ma il processo di connessione è univoco per ogni strumento.

1. Individuare l'indirizzo IP per il computer che ospita il contenitore. In Linux, usare **ifconfig** o **ip addr**. In Windows, utilizzare **ipconfig**.

1. Esecuzione di sqlcmd che specifica l'indirizzo IP e la porta mappata alla porta 1433 nel contenitore. In questo esempio riguarda la porta 1401 nel computer host.

   ```bash
   sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   ```PowerShell
   sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourNewStrong!Passw0rd>"
   ```

1. Eseguire i comandi Transact-SQL. Al termine, digitare `QUIT`.

Altri strumenti comuni per connettersi a SQL Server includono:

- [Codice di Visual Studio](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) in Windows](sql-server-linux-develop-use-ssms.md)
- [SQL Server operazioni Studio (anteprima)](../sql-operations-studio/what-is.md)
- [MSSQL-cli (anteprima)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)

## <a name="remove-your-container"></a>Rimuovere il contenitore

Se si desidera rimuovere il contenitore di SQL Server utilizzato in questa esercitazione, eseguire i comandi seguenti:

```bash
sudo docker stop sql1
sudo docker rm sql1
```

```PowerShell
docker stop sql1
docker rm sql1
```

> [!WARNING]
> L'arresto e rimozione di un contenitore in modo permanente Elimina i dati di SQL Server nel contenitore. Se si desidera conservare i dati, [creare, copiare un file di backup dal contenitore degli](tutorial-restore-backup-in-sql-server-container.md) o utilizzare un [tecnica di persistenza di dati contenitore](sql-server-linux-configure-docker.md#persist).

## <a name="docker-demo"></a>Demo di docker

Dopo che hai tentato utilizzando l'immagine di contenitore di SQL Server per Docker, è utile conoscere come Docker è usato per migliorare lo sviluppo e test. Il video seguente mostra come usare Docker in uno scenario di distribuzione e integrazione continua.

> [!VIDEO https://channel9.msdn.com/Events/Connect/2017/T152/player]

## <a name="next-steps"></a>Passaggi successivi

Per un'esercitazione su come ripristinare i file di backup di database in un contenitore, vedere [ripristinare un database di SQL Server in un contenitore Linux Docker](tutorial-restore-backup-in-sql-server-container.md). Per esplorare altri scenari, ad esempio l'esecuzione di più contenitori, persistenza dei dati e la risoluzione dei problemi, vedere [configurare SQL Server 2017 le immagini contenitore Docker](sql-server-linux-configure-docker.md).

Inoltre, estrarre il [repository GitHub mssql docker](https://github.com/Microsoft/mssql-docker) per le risorse, commenti e suggerimenti e problemi noti.
