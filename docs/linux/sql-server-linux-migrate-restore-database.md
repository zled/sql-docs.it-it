---
title: Eseguire la migrazione di un database di SQL Server da Windows per Linux | Documenti Microsoft
description: In questo argomento viene illustrato come eseguire un database di SQL Server backup in Windows e ripristinarlo in un computer Linux in esecuzione SQL Server 2017 RC2.
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9ac64d1a-9fe5-446e-93c3-d17b8f55a28f
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 2e23ba46381b1fb80b8ac335f6d7630f02a222bb
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restore"></a>Eseguire la migrazione di un database di SQL Server da Windows per Linux tramite backup e ripristino

SQL Server di backup e ripristino è il modo consigliato per eseguire la migrazione di un database da SQL Server in Windows a SQL Server 2017 RC2 in Linux. In questo argomento vengono fornite istruzioni dettagliate per questa tecnica. Questa esercitazione illustrerà come:

- Scaricare il file di backup di AdventureWorks in un computer Windows
- Trasferimento di backup al computer Linux
- Ripristinare il database utilizzando i comandi Transact-SQL

> [!NOTE] 
> In questa esercitazione si presuppone che sia stato installato [SQL Server 2017 RC2](sql-server-linux-setup.md) e [strumenti di SQL Server](sql-server-linux-setup-tools.md) sul server Linux di destinazione.

## <a name="download-the-adventureworks-database-backup"></a>Scaricare il backup del database AdventureWorks

Sebbene sia possibile utilizzare gli stessi passaggi per ripristinare un database, il database di esempio AdventureWorks fornisce un buon esempio. Si tratta di un file di backup di database esistente.

>[!NOTE] 
> Per ripristinare un database di SQL Server in Linux, è necessario eseguire il backup di origine da SQL Server 2014 o SQL Server 2016. Il backup del numero di build di SQL Server non deve essere maggiore del numero di build di SQL Server di ripristino.  

1. Nei computer Windows, passare a [https://msftdbprodsamples.codeplex.com/downloads/get/880661](https://msftdbprodsamples.codeplex.com/downloads/get/880661) e scaricare il **Adventure Works 2014 Full Database Backup.zip**.

   > [!TIP] 
   > Sebbene questa esercitazione viene illustrato il backup e ripristino tra Windows e Linux, è possibile utilizzare un browser per scaricare direttamente il database di esempio AdventureWorks nel computer Linux in Linux.

2. Aprire il file zip ed estrarre il file AdventureWorks2014.bak in una cartella nel computer.

## <a name="transfer-the-backup-file-to-linux"></a>Trasferire il file di backup in Linux

Per ripristinare il database, è necessario trasferire il file di backup da computer Windows per computer Linux di destinazione.

1. Per Windows, installare una shell Bash. Sono disponibili diverse opzioni, inclusi i seguenti:

   - Scaricare un open-source shell Bash, ad esempio [PuTTY](http://www.putty.org/).
   - In alternativa, in Windows 10, usare il nuovo [shell Bash incorporata (beta)](https://msdn.microsoft.com/en-us/commandline/wsl/about).
   - In alternativa, se si lavora con Git, utilizzare il [shell Git Bash](https://git-scm.com/downloads).

2. Aprire una shell Bash (terminal) e passare alla directory contenente **AdventureWorks2014.bak**.

3. Utilizzare il **scp** comando (copia sicuro) per trasferire il file in computer Linux di destinazione. I trasferimenti di esempio seguenti **AdventureWorks2014.bak** della home directory di *user1* sul server denominato *linuxserver1*.

   ```bash
   sudo scp AdventureWorks2014.bak user1@linuxserver1:./
   ```
   
   Nell'esempio precedente, è invece possibile fornire l'indirizzo IP al posto del nome del server.

Esistono diverse alternative all'utilizzo del scp. Uno consiste nell'utilizzare [Samba](https://help.ubuntu.com/community/Samba) per configurare una condivisione di rete SMB tra Windows e Linux. Per una procedura dettagliata in Ubuntu, vedere [come creare una condivisione di rete tramite Samba](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!). Una volta stabilita, è possibile accedere come un file di rete condivisione da Windows, ad esempio  **\\ \\machinenameorip\\condividere**.

## <a name="move-the-backup-file"></a>Spostare il file di backup

A questo punto, il file di backup è il server Linux. Prima di ripristinare il database a SQL Server, è necessario inserire il backup in una sottodirectory di **/var/opt/mssql**.

1. Aprire un terminale nel computer Linux di destinazione che contiene il backup.

2. Passare alla modalità utente con privilegi avanzati.

   ```bash
   sudo su
   ```

3. Creare una nuova directory di backup. Il parametro -p non esegue alcuna operazione se la directory esiste già.

   ```bash
   mkdir -p /var/opt/mssql/backup
   ```

4. Spostare il file di backup in tale directory. Nell'esempio seguente, il file di backup si trova nella home directory di *user1*. Modificare il comando in base alla posizione di **AdventureWorks2014.bak** nel computer.

   ```bash
   mv /home/user1/AdventureWorks2014.bak /var/opt/mssql/backup/
   ```

5. Uscire dalla modalità utente con privilegi avanzati.

   ```bash
   exit
   ```

## <a name="restore-the-database-backup"></a>Ripristinare il backup del database

Per ripristinare il backup, è possibile utilizzare il comando RESTORE DATABASE Transact-SQL (TQL).

> [!NOTE] 
> La procedura seguente utilizza lo strumento sqlcmd. Se non è ancora stato installare gli strumenti di SQL Server, vedere [installazione di SQL Server in Linux](sql-server-linux-setup.md).

1. In terminal stesso, avviare **sqlcmd**. Nell'esempio seguente si connette all'istanza locale di SQL Server con il *SA* utente. Immettere la password quando richiesto o specificare la password con il parametro -P.

   ```bash
   sqlcmd -S localhost -U SA
   ```

2. Dopo la connessione, immettere quanto segue **ripristinare database** premendo INVIO dopo ogni riga di comando. Nell'esempio seguente ripristina il **AdventureWorks2014.bak** file dal */var/opt/mssql/backup* directory.

   ```sql
   RESTORE DATABASE AdventureWorks
   FROM DISK = '/var/opt/mssql/backup/AdventureWorks2014.bak'
   WITH MOVE 'AdventureWorks2014_Data' TO '/var/opt/mssql/data/AdventureWorks2014_Data.mdf',
   MOVE 'AdventureWorks2014_Log' TO '/var/opt/mssql/data/AdventureWorks2014_Log.ldf'
   GO
   ```

   È necessario ottenere un messaggio che è stato ripristinato il database.

3. Per verificare il ripristino, modifica il contesto per il database AdventureWorks. 

   ```sql
   USE AdventureWorks
   GO
   ```

4. Eseguire la query seguente che elenca i primi 10 prodotti nel **Production** tabella.

   ```sql
   SELECT TOP 10 Name, ProductNumber FROM Production.Product ORDER BY Name
   GO
   ```

![Output dalla query Production](./media/sql-server-linux-migrate-restore-database/sql-server-linux-adventureworks-query.png)

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni su altre tecniche di migrazione di database e dei dati, vedere [la migrazione dei database di SQL Server in Linux](sql-server-linux-migrate-overview.md). 

