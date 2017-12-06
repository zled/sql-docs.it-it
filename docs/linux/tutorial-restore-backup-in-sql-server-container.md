---
title: Ripristinare un database di SQL Server in Docker | Documenti Microsoft
description: Questa esercitazione illustra come Ripristina un backup del database di SQL Server in un nuovo contenitore Linux Docker.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: 35a8e5ef7b08530b54d751636c122c6455971faf
ms.sourcegitcommit: 29265ad41fbe3326c21c6908ec4275a3a38f1c09
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2017
---
# <a name="restore-a-sql-server-database-in-a-linux-docker-container"></a>Ripristinare un database di SQL Server in un contenitore Linux Docker

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

In questa esercitazione viene illustrato come spostare e il ripristino di un file di backup di SQL Server in un'immagine di SQL Server per Linux 2017 contenitore in esecuzione in Docker.

> [!div class="checklist"]
> * Effettuare il pull ed eseguire l'immagine di contenitore più recente di SQL Server per Linux 2017.
> * Copiare il file di database di World Wide Importers nel contenitore.
> * Ripristinare il database nel contenitore.
> * Eseguire istruzioni Transact-SQL per visualizzare e modificare il database.
> * Backup del database modificato.

## <a name="prerequisites"></a>Prerequisiti

* Motore docker 1.8 + su qualsiasi supportata di Linux o Docker per Mac e Windows. Per ulteriori informazioni, vedere [installare Docker](https://docs.docker.com/engine/installation/).
* Almeno 2 GB di spazio su disco
* Almeno 2 GB di RAM
* [Requisiti di sistema per SQL Server in Linux](sql-server-linux-setup.md#system).

## <a name="pull-and-run-the-container-image"></a>Effettuare il pull ed eseguire l'immagine del contenitore

1. Aprire una sessione di PowerShell con privilegi elevata in Windows o di un terminale bash su Linux/Mac.

1. Effettuare il pull dell'immagine di SQL Server per Linux 2017 contenitore dall'Hub Docker.

    ```bash
    sudo docker pull microsoft/mssql-server-linux:2017-latest
    ```

    ```PowerShell
    docker pull microsoft/mssql-server-linux:2017-latest
    ```

    > [!TIP]
    > In questa esercitazione vengono forniti esempi di comando di docker per la shell bash (Linux o Mac) e PowerShell (Windows).

1. Per eseguire l'immagine contenitore con Docker, è possibile utilizzare il comando seguente:

    ```bash
    sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
       --name 'sql1' -p 1401:1433 \
       -v sql1data:/var/opt/mssql \
       -d microsoft/mssql-server-linux:2017-latest
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
       --name "sql1" -p 1401:1433 `
       -v sql1data:/var/opt/mssql `
       -d microsoft/mssql-server-linux:2017-latest
    ```

    Questo comando crea un contenitore 2017 di SQL Server con l'edizione Developer edition (impostazione predefinita). Porta di SQL Server **1433** viene esposto nell'host come porta **1401**. Facoltativo `-v sql1data:/var/opt/mssql` parametro crea un contenitore di volumi di dati denominato **sql1ddata**. Viene utilizzato per rendere persistenti i dati creati da SQL Server.

   > [!NOTE]
   > Il processo di esecuzione le edizioni di SQL Server di produzione in contenitori è leggermente diverso. Per ulteriori informazioni, vedere [eseguire produzione immagini contenitore](sql-server-linux-configure-docker.md#production). Se si utilizza lo stesso nome di contenitore e le stesse porte, il resto di questa procedura dettagliata funziona comunque con i contenitori di produzione.

1. Per visualizzare i contenitori di Docker, usare il `docker ps` comando.

    ```bash
    sudo docker ps -a
    ```

    ```PowerShell
    docker ps -a
    ```
 
1. Se il **stato** colonna viene visualizzato lo stato **backup**, quindi viene eseguito SQL Server nel contenitore e in ascolto sulla porta specificata nella **porte** colonna. Se il **stato** colonna per il contenitore di SQL Server viene illustrata **Exited**, vedere il [sezione della Guida alla configurazione di risoluzione dei problemi](sql-server-linux-configure-docker.md#troubleshooting).

   ```
   $ sudo docker ps -a

   CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
   941e1bdf8e1d        microsoft/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour    0.0.0.0:1401->1433/tcp   sql1
   ```

## <a name="change-the-sa-password"></a>Modificare la password SA

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="copy-a-backup-file-into-the-container"></a>Copiare un file di backup nel contenitore

Questa esercitazione viene utilizzato il [database di esempio Wide World Importers](../sample/world-wide-importers/wide-world-importers-documentation.md). Utilizzare la procedura seguente per scaricare e copiare il file di backup di database di Wide World Importers nel contenitore di SQL Server.

1. Innanzitutto, utilizzare **exec docker** per creare una cartella di backup. Il comando seguente crea un **var/rifiutaremssql/** directory all'interno del contenitore di SQL Server.

   ```bash
   sudo docker exec -it sql1 mkdir /var/opt/mssql/backup
   ```

   ```PowerShell
   docker exec -it sql1 mkdir /var/opt/mssql/backup
   ```

1. Successivamente, scaricare il [Wideworldimporters-full.bak](https://github.com/Microsoft/sql-server-samples/releases/tag/wide-world-importers-v1.0) file nel computer host. I seguenti comandi passare alla directory home/utente e scarica il file di backup come **wwi.bak**.

   ```bash
   cd ~
   curl -L -o wwi.bak 'https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak'
   ```

   ```PowerShell
   curl -OutFile "wwi.bak" "https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak"
   ```

1. Utilizzare **docker cp** per copiare il file di backup nel contenitore nel **/var/opt/mssql/backup** directory.

   ```bash
   sudo docker cp wwi.bak sql1:/var/opt/mssql/backup
   ```

   ```PowerShell
   docker cp wwi.bak sql1:/var/opt/mssql/backup
   ```

## <a name="restore-the-database"></a>Ripristinare il database

Il file di backup è ora disponibile all'interno del contenitore. Prima di ripristinare il backup, è importante conoscere i nomi di file logico e i tipi di file all'interno del backup. I comandi Transact-SQL seguenti ispezionare il backup ed eseguire il ripristino utilizzando **sqlcmd** nel contenitore.

> [!TIP]
> Questa esercitazione viene utilizzato **sqlcmd** all'interno del contenitore, in quanto il contenitore viene fornito con questo strumento di pre-installato. Tuttavia, è possibile inoltre eseguire istruzioni Transact-SQL con altri client di strumenti di fuori del contenitore, ad esempio [codice di Visual Studio](sql-server-linux-develop-use-vscode.md) o [SQL Server Management Studio](sql-server-linux-develop-use-ssms.md). Per connettersi, utilizzare la porta dell'host che è stato eseguito il mapping alla porta 1433 nel contenitore. In questo esempio, che è **localhost, 1401** nel computer host e **Host_IP_Address, 1401** in modalità remota.

1. Eseguire **sqlcmd** all'interno del contenitore all'elenco di nomi di file logico e i percorsi all'interno del backup. Questa operazione viene eseguita con il **RESTORE FILELISTONLY** istruzione Transact-SQL.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd -S localhost \
      -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'RESTORE FILELISTONLY FROM DISK = "/var/opt/mssql/backup/wwi.bak"' \
      | tr -s ' ' | cut -d ' ' -f 1-2
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd -S localhost `
      -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "RESTORE FILELISTONLY FROM DISK = '/var/opt/mssql/backup/wwi.bak'"
   ```

   È necessario visualizzare l'output simile al seguente:

   ```
   LogicalName   PhysicalName
   ------------------------------------------
   WWI_Primary   D:\Data\WideWorldImporters.mdf
   WWI_UserData   D:\Data\WideWorldImporters_UserData.ndf
   WWI_Log   E:\Log\WideWorldImporters.ldf
   WWI_InMemory_Data_1   D:\Data\WideWorldImporters_InMemory_Data_1
   ```

1. Chiamare il **RESTORE DATABASE** comando per ripristinare il database all'interno del contenitore. Specificare nuovi percorsi per ognuno dei file nel passaggio precedente.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'RESTORE DATABASE WideWorldImporters FROM DISK = "/var/opt/mssql/backup/wwi.bak" WITH MOVE "WWI_Primary" TO "/var/opt/mssql/data/WideWorldImporters.mdf", MOVE "WWI_UserData" TO "/var/opt/mssql/data/WideWorldImporters_userdata.ndf", MOVE "WWI_Log" TO "/var/opt/mssql/data/WideWorldImporters.ldf", MOVE "WWI_InMemory_Data_1" TO "/var/opt/mssql/data/WideWorldImporters_InMemory_Data_1"'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "RESTORE DATABASE WideWorldImporters FROM DISK = '/var/opt/mssql/backup/wwi.bak' WITH MOVE 'WWI_Primary' TO '/var/opt/mssql/data/WideWorldImporters.mdf', MOVE 'WWI_UserData' TO '/var/opt/mssql/data/WideWorldImporters_userdata.ndf', MOVE 'WWI_Log' TO '/var/opt/mssql/data/WideWorldImporters.ldf', MOVE 'WWI_InMemory_Data_1' TO '/var/opt/mssql/data/WideWorldImporters_InMemory_Data_1'"
   ```

   È necessario visualizzare l'output simile al seguente:

   ```
   Processed 1464 pages for database 'WideWorldImporters', file 'WWI_Primary' on file 1.
   Processed 53096 pages for database 'WideWorldImporters', file 'WWI_UserData' on file 1.
   Processed 33 pages for database 'WideWorldImporters', file 'WWI_Log' on file 1.
   Processed 3862 pages for database 'WideWorldImporters', file 'WWI_InMemory_Data_1' on file 1.
   Converting database 'WideWorldImporters' from version 852 to the current version 869.
   Database 'WideWorldImporters' running the upgrade step from version 852 to version 853.
   Database 'WideWorldImporters' running the upgrade step from version 853 to version 854.
   Database 'WideWorldImporters' running the upgrade step from version 854 to version 855.
   Database 'WideWorldImporters' running the upgrade step from version 855 to version 856.
   Database 'WideWorldImporters' running the upgrade step from version 856 to version 857.
   Database 'WideWorldImporters' running the upgrade step from version 857 to version 858.
   Database 'WideWorldImporters' running the upgrade step from version 858 to version 859.
   Database 'WideWorldImporters' running the upgrade step from version 859 to version 860.
   Database 'WideWorldImporters' running the upgrade step from version 860 to version 861.
   Database 'WideWorldImporters' running the upgrade step from version 861 to version 862.
   Database 'WideWorldImporters' running the upgrade step from version 862 to version 863.
   Database 'WideWorldImporters' running the upgrade step from version 863 to version 864.
   Database 'WideWorldImporters' running the upgrade step from version 864 to version 865.
   Database 'WideWorldImporters' running the upgrade step from version 865 to version 866.
   Database 'WideWorldImporters' running the upgrade step from version 866 to version 867.
   Database 'WideWorldImporters' running the upgrade step from version 867 to version 868.
   Database 'WideWorldImporters' running the upgrade step from version 868 to version 869.
   RESTORE DATABASE successfully processed 58455 pages in 18.069 seconds (25.273 MB/sec).
   ```

## <a name="verify-the-restored-database"></a>Verificare che il database ripristinato

Eseguire la query seguente per visualizzare un elenco di nomi di database nel contenitore:

```bash
sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
   -Q 'SELECT Name FROM sys.Databases'
```

```PowerShell
docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
   -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
   -Q "SELECT Name FROM sys.Databases"
```

Dovrebbe essere **WideWorldImporters** nell'elenco dei database.

## <a name="make-a-change"></a>Apportare una modifica

I passaggi seguenti apportare una modifica nel database.

1. Eseguire una query per visualizzare gli elementi dei primi 10 nel **Warehouse.StockItems** tabella.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'SELECT TOP 10 StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems ORDER BY StockItemID'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "SELECT TOP 10 StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems ORDER BY StockItemID"
   ```

   Si dovrebbe vedere un elenco di nomi e gli identificatori elemento:

   ```
   StockItemID StockItemName
   ----------- -----------------
             1 USB missile launcher (Green)
             2 USB rocket launcher (Gray)
             3 Office cube periscope (Black)
             4 USB food flash drive - sushi roll
             5 USB food flash drive - hamburger
             6 USB food flash drive - hot dog
             7 USB food flash drive - pizza slice
             8 USB food flash drive - dim sum 10 drive variety pack
             9 USB food flash drive - banana
            10 USB food flash drive - chocolate bar
   ```

1. Aggiornare la descrizione del primo elemento con il codice seguente **aggiornamento** istruzione:

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'UPDATE WideWorldImporters.Warehouse.StockItems SET StockItemName="USB missile launcher (Dark Green)" WHERE StockItemID=1; SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "UPDATE WideWorldImporters.Warehouse.StockItems SET StockItemName='USB missile launcher (Dark Green)' WHERE StockItemID=1; SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1"
   ```

   È necessario visualizzare l'output simile al seguente:

   ```
   (1 rows affected)
   StockItemID StockItemName
   ----------- ------------------------------------
             1 USB missile launcher (Dark Green)
   ```

## <a name="create-a-new-backup"></a>Creare un nuovo backup

Dopo aver ripristinato il database in un contenitore, è inoltre possibile creare regolarmente i backup di database all'interno del contenitore in esecuzione. I passaggi seguono un modello simile per i passaggi precedenti, ma in ordine inverso.

1. Utilizzare il **BACKUP DATABASE** comando Transact-SQL per creare un backup del database nel contenitore. Questa esercitazione consente di creare un nuovo file di backup, **wwi_2.bak**, creato in precedenza **/var/opt/mssql/backup** directory.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q "BACKUP DATABASE [WideWorldImporters] TO DISK = N'/var/opt/mssql/backup/wwi_2.bak' WITH NOFORMAT, NOINIT, NAME = 'WideWorldImporters-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "BACKUP DATABASE [WideWorldImporters] TO DISK = N'/var/opt/mssql/backup/wwi_2.bak' WITH NOFORMAT, NOINIT, NAME = 'WideWorldImporters-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
   ```

   È necessario visualizzare l'output simile al seguente:

   ```
   10 percent processed.
   20 percent processed.
   30 percent processed.
   40 percent processed.
   50 percent processed.
   60 percent processed.
   70 percent processed.
   Processed 1200 pages for database 'WideWorldImporters', file 'WWI_Primary' on file 1.
   Processed 53096 pages for database 'WideWorldImporters', file 'WWI_UserData' on file 1.
   80 percent processed.
   Processed 3865 pages for database 'WideWorldImporters', file 'WWI_InMemory_Data_1' on file 1.
   Processed 938 pages for database 'WideWorldImporters', file 'WWI_Log' on file 1.
   100 percent processed.
   BACKUP DATABASE successfully processed 59099 pages in 25.056 seconds (18.427 MB/sec).
   ```

1. Successivamente, copiare il file di backup fuori del contenitore e nel computer host.

   ```bash
   cd ~
   sudo docker cp sql1:/var/opt/mssql/backup/wwi_2.bak wwi_2.bak
   ls -l wwi*
   ```

   ```PowerShell
   cd ~
   docker cp sql1:/var/opt/mssql/backup/wwi_2.bak wwi_2.bak
   ls -l wwi*
   ```

## <a name="use-the-persisted-data"></a>Utilizzare i dati persistenti

Oltre al backup del database per la protezione dei dati, è inoltre possibile utilizzare i contenitori di volumi di dati. L'inizio di questa esercitazione creata il **sql1** contenitore con il `-v sql1data:/var/opt/mssql` parametro. Il **sql1data** contenitore del volume di dati mantiene il **/var/opt/mssql** anche dopo che viene rimosso il contenitore di dati. La procedura seguente consente di rimuovere completamente il **sql1** contenitore e quindi creare un nuovo contenitore, **sql2**, con i dati persistenti.

1. Arrestare il **sql1** contenitore.

   ```bash
   sudo docker stop sql1
   ```

   ```PowerShell
   docker stop sql1
   ```

1. Rimuovere il contenitore. Questa operazione non elimina creato in precedenza **sql1data** contenitore del volume di dati e i dati persistenti in essa contenuti.

   ```bash
   sudo docker rm sql1
   ```

   ```PowerShell
   docker rm sql1
   ```

1. Creare un nuovo contenitore, **sql2**e riutilizzare il **sql1data** contenitore del volume di dati.

    ```bash
    sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
       --name 'sql2' -e 'MSSQL_PID=Developer' -p 1401:1433 \
       -v sql1data:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
       --name "sql2" -e "MSSQL_PID=Developer" -p 1401:1433 `
       -v sql1data:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
    ```

1. Il database di Wide World Importers è il nuovo contenitore. Eseguire una query per verificare le modifiche precedenti apportate.

   ```bash
   sudo docker exec -it sql2 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1'
   ```

   ```PowerShell
   docker exec -it sql2 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1"
   ```

   > [!NOTE]
   > La password dell'amministratore di sistema non è la password specificata per il **sql2** contenitore, `MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>`. Tutti i dati di SQL Server è stato ripristinato da **sql1**, inclusa la password modificata dalla precedenza nell'esercitazione. In effetti, alcune opzioni simile al seguente vengono ignorati a causa di ripristino dei dati in /var/opt/mssql. Per questo motivo, la password è `<YourNewStrong!Passw0rd>` come illustrato di seguito.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato descritto come eseguire il backup di un database in Windows e spostarlo in un server Linux in esecuzione SQL Server 2017 RC2. Si è appreso per:
> [!div class="checklist"]
> * Creazione di immagini contenitore di SQL Server per Linux 2017.
> * Copiare i backup del database SQL Server in un contenitore.
> * Eseguire istruzioni Transact-SQL all'interno del contenitore con **sqlcmd**.
> * Creare ed estrarre i file di backup da un contenitore.
> * Utilizzare i contenitori di volumi di dati in Docker per rendere persistenti i dati di SQL Server.

Successivamente, esaminare altre configurazioni di Docker e gli scenari di risoluzione dei problemi:

> [!div class="nextstepaction"]
>[Guida alla configurazione di SQL Server 2017 in Docker](sql-server-linux-configure-docker.md)
