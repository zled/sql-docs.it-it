---
title: Backup e ripristino - Parallel Data Warehouse | Documenti Microsoft
description: Viene descritto come dati di backup e ripristino eseguito per Parallel Data Warehouse (PDW). Operazioni di backup e ripristino vengono utilizzate per il ripristino di emergenza. Backup e ripristino è consente anche di copiare un database da un dispositivo a un altro dispositivo.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 118b9ced12e01ac6655d85969bb61717f2b31e0b
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="backup-and-restore"></a>Backup e ripristino
Viene descritto come dati di backup e ripristino eseguito per Parallel Data Warehouse (PDW). Operazioni di backup e ripristino vengono utilizzate per il ripristino di emergenza. Backup e ripristino è consente anche di copiare un database da un dispositivo a un altro dispositivo.  
    
## <a name="BackupRestoreBasics"></a>Nozioni di base di backup e ripristino  
Un PDW *backup del database* è una copia di un database dello strumento, archiviato in un formato in modo che può essere utilizzato per ripristinare il database originale in un'applicazione.  
  
Viene creato un backup del database PDW con il [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md) istruzione t-sql e formattato per l'utilizzo con il [RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md) istruzione; è inutilizzabile per altri scopi. Il backup può essere ripristinato solo in un'applicazione con lo stesso numero o un numero maggiore di nodi di calcolo.  
  
<!-- MISSING LINKS

The [master database](master-database.md) is a SMP SQL Server database. It is backed up with the BACKUP DATABASE statement. To restore master, use the [Restore the Master Database](configuration-manager-restore-master-database.md) page of the Configuration Manager tool.  

-->
  
PDW utilizza tecnologia di backup di SQL Server per eseguire il backup e ripristino di database di dispositivo. Opzioni di backup di SQL Server sono preconfigurate per utilizzare la compressione dei backup. Non è possibile impostare opzioni di backup come la compressione, il checksum, la dimensione blocco e il conteggio buffer.  
  
Backup di database vengono archiviati in uno o più server di backup, che esiste nella rete di clienti.  PDW scrive un backup del database utente in parallelo direttamente dai nodi di calcolo in un server di backup e ripristina un backup del database utente in parallelo direttamente dal server di backup per i nodi di calcolo.  
  
Backup vengono archiviati nel server di backup come un set di file nel file system di Windows. Un backup del database PDW può essere ripristinato solo per PDW. Tuttavia, è possibile archiviare i backup di database dal server di backup in un'altra posizione utilizzando standard processi di backup di file di Windows. Per ulteriori informazioni sui server di backup, vedere [acquisizione e configurare un server di backup](acquire-and-configure-backup-server.md).  
  
## <a name="BackupTypes"></a>Tipi di backup di database  
Esistono due tipi di dati che richiedono un backup: database di sistema (ad esempio, il database master) e i database utente. PDW non esegue il backup del log delle transazioni.  
  
Un backup completo del database è un backup di un intero database PDW. Questo è il tipo di backup predefinito. Un backup completo di un database utente include gli utenti del database e i ruoli del database. Un backup del database master include gli account di accesso.  
  
Un backup differenziale contiene tutte le modifiche apportate dopo l'ultimo backup completo. Un backup differenziale richiede in genere meno tempo rispetto a un backup completo e può essere eseguito più di frequente. Quando più copie di backup differenziale si basano su stesso backup completo, ogni backup differenziale include tutte le modifiche nel backup differenziale precedente.  
  
Ad esempio, è possibile creare un backup completo ogni settimana e ogni giorno un backup differenziale. Per ripristinare il database utente, il backup completo più l'ultimo backup differenziale (se presente) deve essere ripristinato.  
  
Un backup differenziale è supportato solo per i database utente. Un backup del database master è sempre un backup completo.  
  
Per eseguire il backup dell'intera accessorio, è necessario eseguire un backup di tutti i database utente e un backup del database master.  
  
## <a name="BackupProc"></a>Processo di backup del database  
Nel diagramma seguente mostra il flusso di dati durante un backup del database.  
  
![Processo di backup PDW](media/backup-process.png "processo di backup di PDW")  
  
Il processo di backup funziona nel modo seguente:  
  
1.  Utente invia un'istruzione tsql BACKUP DATABASE per il nodo di controllo.  
  
    -   Il backup è un backup completo o differenziale.  
  
2.  Per i database utente, il nodo di controllo (motore di MPP) crea un piano di query distribuite per eseguire un backup di database paralleli.  
  
3.  Ogni nodo coinvolta in copie di backup il file di backup al server di backup utilizzando la funzionalità backup di SQL Server.  
  
    -   Ogni nodo coinvolta copia un file di backup per il server di backup.  
  
    -   Il backup del database utente (completo o differenziale) include un backup della parte del database archiviato in ogni nodo di calcolo e un backup di database utenti e ruoli del database.  
  
4.  Il backup vengono eseguiti in parallelo utilizzando la rete InfiniBand.  
  
    -   PDW esegue ogni backup completi e differenziali in parallelo. Tuttavia, più backup del database non vengono eseguiti contemporaneamente. Ogni richiesta di backup deve attendere per i backup inviati in precedenza terminare.  
  
    -   Un backup del database master esegue solo il backup dei dati dal nodo di controllo. Questo tipo di backup viene eseguito in modo seriale.  
  
5.  Un backup del database PDW è un gruppo di file archiviati in una directory che si trova disattivare il dispositivo. Il nome della directory viene specificato come un nome di percorso e la directory di rete. La directory non può essere un percorso locale e non può essere nel dispositivo.  
  
6.  Al termine dell'operazione di backup, è possibile utilizzare il file system di Windows per copiare la directory di backup in un altro percorso, se lo si desidera.  
  
    -   Una copia di backup può essere ripristinato solo a appliance PDW che presenta un numero uguale o maggiore di nodi di calcolo.  
  
    -   Prima di eseguire un ripristino, è possibile modificare il nome del backup. Il nome della directory di backup deve corrispondere al nome del nome originale del backup. Il nome originale del backup si trova nel file backup.xml all'interno della directory di backup. Per ripristinare un database in un nome diverso, è possibile specificare il nuovo nome nel comando restore. Esempio: `RESTORE DATABASE MyDB1 FROM DISK = ꞌ\\10.192.10.10\backups\MyDB2ꞌ`.  
  
## <a name="RestoreModes"></a>Modalità di ripristino di database  
Un ripristino completo del database consente di ricreare il database PDW utilizzando i dati nel backup del database. Il ripristino di database viene effettuato prima di ripristinare un backup completo e quindi, facoltativamente, il ripristino di un backup differenziale. Il ripristino di database include gli utenti di database e i ruoli del database.  
  
Il ripristino solo di intestazione restituisce le informazioni di intestazione per un database. Dati non verranno ripristinati al dispositivo.  
  
Il ripristino di un dispositivo è un ripristino del dispositivo intero. Ciò include il ripristino di tutti i database utente e del database master.  
  
## <a name="RestoreProc"></a>Processo di ripristino  
Nel diagramma seguente mostra il flusso di dati durante il ripristino del database.  
  
![Processo di ripristino](media/restore-process.png "processo di ripristino")  
  
## <a name="restoring-to-an-appliance-with-the-same-number-of-compute-nodes"></a>Ripristino in un'applicazione con lo stesso numero di nodi di calcolo * *  
  
Quando il ripristino dei dati, lo strumento rileva il numero di nodi di calcolo in cui il dispositivo di origine e il dispositivo di destinazione. Se entrambi gli accessori dispongono di un numero uguale di nodi di calcolo, il processo di ripristino funziona nel modo seguente:  
  
1.  Il backup del database da ripristinare è disponibile in una condivisione di file di Windows in un server di backup non strumento. Per prestazioni ottimali, il server è in genere connesso alla rete InfiniBand accessorio.  
  
2.  Utente invia un [RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md) istruzione tsql per il nodo di controllo.  
  
    -   Il ripristino è un ripristino completo o un ripristino di intestazione. Il ripristino completo Ripristina un backup completo e quindi, facoltativamente, consente di ripristinare un backup differenziale.  
  
3.  Il nodo di controllo (motore di MPP) crea un piano di query distribuite per eseguire un ripristino di database paralleli.  
  
    -   ServerPDW SQL esegue il ripristino di un database utente in parallelo. Tuttavia, più i backup del database e i ripristini non vengono eseguiti contemporaneamente. Il motore MPP inserisce ogni istruzione restore in una coda. deve attendere inviata in precedenza backup e ripristinare le richieste di fine.  
  
    -   Un ripristino del database master consente di ripristinare solo i dati sul nodo di controllo. il ripristino viene eseguito in serie.  
  
    -   Un ripristino delle informazioni di intestazione è un'operazione rapida e verranno ripristinati i dati per i nodi di calcolo o di controllo. Al contrario, il nodo controllo restituisce i risultati come output della query.  
  
4.  I file di backup venga copiati in nodi di calcolo corretti in parallelo, in genere nella rete InfiniBand di dispositivo.  
  
5.  Ogni nodo di calcolo consente di ripristinare la parte del database utente. Se uno qualsiasi dei ripristini non completata correttamente, tutti i database rimossi e il ripristino viene completato correttamente.  
  
## <a name="restoring-to-an-appliance-with-a-larger-number-of-compute-nodes"></a>Ripristino in un'applicazione con un numero maggiore di nodi di calcolo  
  
Il ripristino di un backup in un'appliance con un numero maggiore di nodi di calcolo aumenta la dimensione allocata al database proporzionalmente al numero di nodi di calcolo.  
  
Ad esempio, quando si ripristina un database di 60 GB da un dispositivo 2 nodi (30 GB per ogni nodo) in un'applicazione di 6 nodi, SQL Server PDW crea un database di 180 GB (6 nodi con 30 GB per ogni nodo) nel dispositivo 6-nodo. SQL Server PDW inizialmente Ripristina il database a 2 nodi in modo che corrisponda alla configurazione dell'origine e quindi vengono ridistribuiti i dati da tutti i nodi di 6.  
  
Dopo la ridistribuzione, ogni nodo di calcolo contiene meno dati effettivi e più spazio disponibile rispetto a ogni nodo di calcolo nell'appliance di origine di dimensioni inferiori. Usare lo spazio aggiuntivo per l'aggiunta di altri dati al database. Se le dimensioni del database ripristinato sono superiore al necessario, è possibile utilizzare [ALTER DATABASE](../t-sql/statements/alter-database-parallel-data-warehouse.md) per compattare le dimensioni dei file di database.  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Backup e attività di ripristino|Description|  
|---------------------------|---------------|  
|Preparare un server come server di backup.|[Acquisire e configurare un server di backup ](acquire-and-configure-backup-server.md)|  
|Backup di un database.|[DATABASE DI BACKUP](../t-sql/statements/backup-database-parallel-data-warehouse.md)|  
|Ripristinare un database.|[RIPRISTINO DI DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)|    
<!-- MISSING LINKS
|Create a disaster recovery plan.|[Create a Disaster Recovery Plan](create-disaster-recovery-plan.md)|
|Restore the master database.|To restore the master database, use the [Restore the master database](configuration-manager-restore-master-database.md) page in the Configuration Manager tool.| 
|Copy a database from one appliance to another appliance.|[Copy a PDW database to another appliance](copy-pdw-database-to-another-appliance.md).|  
|Monitor backups and restores.|[Monitor backups and restores](monitor-backup-and-restore.md)|  
-->
