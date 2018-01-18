---
title: Backup e ripristino di database di SQL Server in Linux | Documenti Microsoft
description: Informazioni su come eseguire il backup e ripristino dei database di SQL Server in Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 11/14/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: d30090fb-889f-466e-b793-5f284fccc4e6
ms.workload: On Demand
ms.openlocfilehash: 0b12200da9b4e0967c8057d807d19919fb07f331
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="backup-and-restore-sql-server-databases-on-linux"></a>Backup e ripristino di database di SQL Server in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

È possibile eseguire i backup dei database SQL Server 2017 in Linux con gli stessi strumenti come altre piattaforme. In un server Linux, è possibile utilizzare **sqlcmd** per connettersi a SQL Server ed eseguire il backup. Da Windows, è possibile connettersi a SQL Server in Linux ed eseguire i backup con l'interfaccia utente. La funzionalità di backup è lo stesso tra le piattaforme. Ad esempio, è possibile eseguire il backup database in locale, in unità remote o a [servizio di archiviazione Blob di Microsoft Azure](../relational-databases/backup-restore/sql-server-backup-to-url.md).

## <a name="backup-a-database"></a>Backup di un database

Nell'esempio seguente **sqlcmd** si connette all'istanza locale di SQL Server e richiede una procedura completa di backup di un database utente denominato `demodb`.

```bash
sqlcmd -S localhost -U SA -Q "BACKUP DATABASE [demodb] TO DISK = N'/var/opt/mssql/data/demodb.bak' WITH NOFORMAT, NOINIT, NAME = 'demodb-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
```

Quando si esegue il comando, verrà richiesta una password SQL Server. Dopo avere immesso la password, la shell verrà restituiti i risultati dello stato di avanzamento di backup. Esempio:

```
Password:
10 percent processed.
21 percent processed.
32 percent processed.
40 percent processed.
51 percent processed.
61 percent processed.
72 percent processed.
80 percent processed.
91 percent processed.
Processed 296 pages for database 'demodb', file 'demodb' on file 1.
100 percent processed.
Processed 2 pages for database 'demodb', file 'demodb_log' on file 1.
BACKUP DATABASE successfully processed 298 pages in 0.064 seconds (36.376 MB/sec).
```

### <a name="backup-the-transaction-log"></a>Eseguire il backup del log delle transazioni

Se il database nel modello di recupero con registrazione completa, è anche possibile rendere i backup del log delle transazioni per le opzioni di ripristino più granulari. Nell'esempio seguente, **sqlcmd** si connette all'istanza locale di SQL Server ed esegue il backup un log delle transazioni.

```bash
sqlcmd -S localhost -U SA -Q "BACKUP LOG [demodb] TO DISK = N'/var/opt/mssql/data/demodb_LogBackup.bak' WITH NOFORMAT, NOINIT, NAME = N'demodb_LogBackup', NOSKIP, NOREWIND, NOUNLOAD, STATS = 5"
```

## <a name="restore-a-database"></a>Ripristinare un database

Nell'esempio seguente **sqlcmd** si connette all'istanza locale di SQL Server e ripristina il database demodb. Si noti che il `NORECOVERY` opzione viene utilizzata per consentire ulteriori ripristini di file di backup del log. Se non si intende ripristinare i file di log aggiuntivi, rimuovere il `NORECOVERY` opzione.

```bash
sqlcmd -S localhost -U SA -Q "RESTORE DATABASE [demodb] FROM DISK = N'/var/opt/mssql/data/demodb.bak' WITH FILE = 1, NOUNLOAD, REPLACE, NORECOVERY, STATS = 5"
```

> [!TIP]
> Se accidentalmente, utilizzare l'opzione NORECOVERY ma non dispone di backup di file di log aggiuntivi, eseguire il comando `RESTORE DATABASE demodb` senza parametri aggiuntivi. Questo termine del ripristino e lascia il database operativo.

### <a name="restore-the-transaction-log"></a>Ripristino del log delle transazioni

Il comando seguente ripristina il backup del log delle transazioni precedenti.

```bash
sqlcmd -S localhost -U SA -Q "RESTORE LOG demodb FROM DISK = N'/var/opt/mssql/data/demodb_LogBackup.bak'"
```

## <a name="backup-and-restore-with-sql-server-management-studio-ssms"></a>Backup e ripristino con SQL Server Management Studio (SSMS)

È possibile utilizzare SSMS da un computer Windows per connettersi a un database di Linux e creare un backup tramite l'interfaccia utente.

>[!NOTE] 
> Utilizzare la versione più recente di SSMS per connettersi a SQL Server. Per scaricare e installare la versione più recente, vedere [scaricare SSMS](../ssms/download-sql-server-management-studio-ssms.md). Per ulteriori informazioni sull'utilizzo di SQL Server Management Studio, vedere [utilizzare SSMS per gestire SQL Server in Linux](sql-server-linux-manage-ssms.md).

I passaggi seguenti eseguendo un backup con SQL Server Management Studio. 

1. Avviare SQL Server Management Studio e connettersi al server in SQL Server 2017 in Linux.

1. In Esplora oggetti fare clic sul database, fare clic su **attività**, quindi fare clic su **eseguire il backup...** .

1. Nel **Backup dei Database** finestra di dialogo, verificare i parametri e le opzioni e fare clic su **OK**.
 
SQL Server consente di completare il backup del database.

### <a name="restore-with-sql-server-management-studio-ssms"></a>Ripristino con SQL Server Management Studio (SSMS) 

I passaggi seguenti consentono di eseguire il ripristino di un database con SQL Server Management Studio.

1. In SQL Server Management Studio fare clic sul **database** e fare clic su **ripristino di database...** . 

1. In **origine** fare clic su **dispositivo:** e quindi fare clic sui puntini di sospensione (...).

1. Individuare il file di backup del database e fare clic su **OK**. 

1. In **piano di ripristino**, verificare le impostazioni e i file di backup. Scegliere **OK**. 

1. SQL Server Ripristina il database. 

## <a name="see-also"></a>Vedere anche

* [Creare un Backup completo del Database (SQL Server)](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)
* [Eseguire il backup di un Log delle transazioni (SQL Server)](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)
* [BACKUP (Transact-SQL)](../t-sql/statements/backup-transact-sql.md)
* [Backup di SQL Server nell'URL](../relational-databases/backup-restore/sql-server-backup-to-url.md)
