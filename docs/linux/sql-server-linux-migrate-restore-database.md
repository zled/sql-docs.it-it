---
title: Eseguire la migrazione di un database di SQL Server da Windows per Linux | Documenti Microsoft
description: In questa esercitazione viene illustrato come eseguire un database di SQL Server backup in Windows e ripristinarlo in un computer Linux in esecuzione SQL Server 2017.
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 08/16/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 9ac64d1a-9fe5-446e-93c3-d17b8f55a28f
ms.workload: On Demand
ms.openlocfilehash: 6d54a849630bece0fba6456a516cbd68aecf2eb5
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restore"></a>Eseguire la migrazione di un database di SQL Server da Windows per Linux tramite backup e ripristino

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

SQL Server di backup e ripristino è il modo consigliato per la migrazione di un database da SQL Server in Windows a 2017 di SQL Server in Linux. In questa esercitazione verrà illustrata i passaggi necessari per spostare un database in Linux con backup e ripristino tecniche.

> [!div class="checklist"]
> * Creare un file di backup in Windows con SQL Server Management Studio
> * Installare una shell Bash in Windows
> * Spostare il file di backup per Linux da della shell Bash
> * Ripristinare il file di backup in Linux con Transact-SQL
> * Eseguire una query per verificare la migrazione

## <a name="prerequisites"></a>Prerequisiti

Per completare questa esercitazione, sono necessari i seguenti prerequisiti:

* Computer Windows con le operazioni seguenti:
  * [SQL Server](https://www.microsoft.com/sql-server/sql-server-2016-editions) installato.
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) installato.
  * Database di destinazione per eseguire la migrazione.

* Computer Linux con installati i componenti seguenti:
  * SQL Server 2017 ([RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), o [Ubuntu](quickstart-install-connect-ubuntu.md)) con gli strumenti da riga di comando.

## <a name="create-a-backup-on-windows"></a>Creare un backup in Windows

Esistono diversi modi per creare un file di backup di un database in Windows. La procedura seguente utilizza SQL Server Management Studio (SSMS).

1. Avviare **SQL Server Management Studio** sul proprio computer Windows.

1. Nella finestra di dialogo connessione immettere **localhost**.

1. In Esplora oggetti espandere **database**.

1. Il pulsante destro del database di destinazione, selezionare **attività**, quindi fare clic su **eseguire il backup...** .

   ![Utilizzare SQL Server Management Studio per creare un file di backup](./media/sql-server-linux-migrate-restore-database/ssms-create-backup.png)

1. Nel **Backup dei Database** finestra di dialogo, verificare che **tipo Backup** è **completo** e **backup su** è **disco**. Annotare nome e percorso del file. Ad esempio, un database denominato **YourDB** in SQL Server 2016 è un percorso di backup predefinito di `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak`.

1. Fare clic su **OK** per eseguire il backup del database.

> [!NOTE]
> Un'altra opzione consiste nell'eseguire una query Transact-SQL per creare il file di backup. Il comando Transact-SQL seguente esegue le stesse azioni i passaggi precedenti per un database denominato **YourDB**:
>
> ```sql
> BACKUP DATABASE [YourDB] TO  DISK =
> N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak'
> WITH NOFORMAT, NOINIT, NAME = N'YourDB-Full Database Backup',
> SKIP, NOREWIND, NOUNLOAD, STATS = 10
> GO
> ```

## <a name="install-a-bash-shell-on-windows"></a>Installare una shell Bash in Windows

Per ripristinare il database, è necessario trasferire il file di backup da computer Windows per computer Linux di destinazione. In questa esercitazione è spostare il file di Linux da una shell Bash (finestra terminale) in esecuzione su Windows.

1. Installare una shell Bash nel computer Windows che supporta il **scp** (protetto copia) e **ssh** comandi (account di accesso remoto). Due esempi:

   * Il [sottosistema Windows per Linux](https://msdn.microsoft.com/commandline/wsl/about) (Windows 10)
   * La Shell Git Bash ([https://git-scm.com/downloads](https://git-scm.com/downloads))

1. Aprire una sessione Bash in Windows.

## <a id="scp"></a>Copiare il file di backup in Linux

1. Nella sessione Bash, passare alla directory contenente il file di backup. Esempio:

   ```bash
   cd 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\'
   ```

1. Utilizzare il **scp** comando per trasferire il file in computer Linux di destinazione. I trasferimenti di esempio seguenti **YourDB.bak** della home directory di *user1* sul server Linux con un indirizzo IP di *192.0.2.9*:

   ```bash
   scp YourDB.bak user1@192.0.2.9:./
   ```
   ![comando SCP](./media/sql-server-linux-migrate-restore-database/scp-command.png)

> [!TIP]
> Sono disponibili alternative all'utilizzo di scp per il trasferimento di file. Uno consiste nell'utilizzare [Samba](https://help.ubuntu.com/community/Samba) per configurare una condivisione di rete SMB tra Windows e Linux. Per una procedura dettagliata in Ubuntu, vedere [come creare una condivisione di rete tramite Samba](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!). Una volta stabilita, è possibile accedere come un file di rete condivisione da Windows, ad esempio  **\\ \\machinenameorip\\condividere**.

## <a name="move-the-backup-file-before-restoring"></a>Spostare il file di backup prima del ripristino

A questo punto, il file di backup è nel server Linux nella home directory dell'utente. Prima di ripristinare il database a SQL Server, è necessario inserire il backup in una sottodirectory di **/var/opt/mssql**.

1. Nella stessa sessione di Windows Bash, connettersi in remoto al computer Linux di destinazione con **ssh**. Nell'esempio seguente si connette al computer Linux **192.0.2.9** come utente **user1**.

   ```bash
   ssh user1@192.0.2.9
   ```

   Si stanno eseguendo i comandi nel server remoto di Linux.

1. Passare alla modalità utente con privilegi avanzati.

   ```bash
   sudo su
   ```

1. Creare una nuova directory di backup. Il parametro -p non esegue alcuna operazione se la directory esiste già.

   ```bash
   mkdir -p /var/opt/mssql/backup
   ```

1. Spostare il file di backup in tale directory. Nell'esempio seguente, il file di backup si trova nella home directory di *user1*. Modificare il comando in modo che corrisponda il percorso e il nome del file di backup.

   ```bash
   mv /home/user1/YourDB.bak /var/opt/mssql/backup/
   ```

1. Uscire dalla modalità utente con privilegi avanzati.

   ```bash
   exit
   ```

## <a name="restore-your-database-on-linux"></a>Ripristinare il database su Linux

Per ripristinare il backup del database, è possibile utilizzare il **RESTORE DATABASE** comando Transact-SQL (TQL).

> [!NOTE]
> I seguenti passaggi viene utilizzata la **sqlcmd** strumento. Se non è ancora stato installare gli strumenti di SQL Server, vedere [strumenti da riga di comando di installazione di SQL Server in Linux](sql-server-linux-setup-tools.md).

1. In terminal stesso, avviare **sqlcmd**. Nell'esempio seguente si connette all'istanza locale di SQL Server con il **SA** utente. Immettere la password quando richiesto, oppure specificare la password tramite l'aggiunta di **-P** parametro.

   ```bash
   sqlcmd -S localhost -U SA
   ```

1. Nel `>1` richiesto, immettere quanto segue **RESTORE DATABASE** comando, premere INVIO dopo ogni riga (è possibile copiare e incollare l'intero comando su più righe in una sola volta). Sostituire tutte le occorrenze di `YourDB` con il nome del database.

   ```sql
   RESTORE DATABASE YourDB
   FROM DISK = '/var/opt/mssql/backup/YourDB.bak'
   WITH MOVE 'YourDB' TO '/var/opt/mssql/data/YourDB.mdf',
   MOVE 'YourDB_Log' TO '/var/opt/mssql/data/YourDB_Log.ldf'
   GO
   ```

   È necessario ottenere un messaggio che è stato ripristinato il database.

1. Verificare il ripristino, elencando tutti i database nel server. Il database ripristinato deve essere elencato.

   ```sql
   SELECT Name FROM sys.Databases
   GO
   ```

1. Eseguire altre query sul database migrato. Il comando seguente cambia il contesto per il **YourDB** seleziona le righe da una delle relative tabelle e database.

   ```sql
   USE YourDB
   SELECT * FROM YourTable
   GO
   ```

1. Al termine usando **sqlcmd**, tipo `exit`.

1. Al termine lavorare in remoto **ssh** sessione, digitare `exit` nuovamente.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato descritto come eseguire il backup di un database in Windows e spostarlo in un server Linux in esecuzione SQL Server 2017. Si è appreso per:
> [!div class="checklist"]
> * Utilizzare SQL Server Management Studio e Transact-SQL per creare un file di backup in Windows
> * Installare una shell Bash in Windows
> * Utilizzare **scp** per spostare i file di backup da Windows per Linux
> * Utilizzare **ssh** connettersi in remoto ai computer Linux
> * Spostare il file di backup di preparazione del ripristino
> * Utilizzare **sqlcmd** per eseguire i comandi Transact-SQL
> * Ripristinare il backup di database con il **RESTORE DATABASE** comando 

Successivamente, è possibile esplorare altri scenari di migrazione per SQL Server in Linux. 

> [!div class="nextstepaction"]
>[La migrazione dei database di SQL Server in Linux](sql-server-linux-migrate-overview.md)
