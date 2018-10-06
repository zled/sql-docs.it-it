---
title: Ripristinare un database in cluster di big data di SQL Server | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 04514fb0184fa28e0ba959f3dd33cb2e1ec945cb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796448"
---
# <a name="restore-a-database-into-the-sql-server-big-data-cluster-master-instance"></a>Ripristinare un database nell'istanza master del cluster dei big data di SQL Server

Per portare un database di SQL Server esistente nell'istanza master, è consigliabile utilizzare un backup, copia e ripristino approccio.  In questo esempio verrà illustrato come ripristinare il database AdventureWorks, ma è possibile usare qualsiasi backup del database che è necessario.  È possibile scaricare il backup di AdventureWorks [qui](https://www.microsoft.com/en-us/download/details.aspx?id=49502).

In primo luogo, il backup del database di SQL Server esistente in SQL Server in Windows o Linux usando uno dei normali metodi di creazione di un backup del database.

Copiare il file di backup nel contenitore di SQL Server nel pod istanza master del cluster Kubernetes.

```bash
kubectl cp <path to .bak file> mssql-data-pool-master-0:/tmp/ -c mssql-data-pool-data -n <name of your cluster>
```

Esempio:

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak mssql-data-pool-master-0:/tmp/ -c mssql-data-pool-data -n clustertest
```

Verificare quindi che il file di backup è stato copiato nel contenitore di pod.

```bash
kubectl exec -it mssql-data-pool-master-0 -n <name of your cluster> -c mssql-data-pool-data -- bin/bash
root@mssql-data-pool-master-0:/# ls /tmp
root@mssql-data-pool-master-0:/# exit
```

Esempio:

```bash
kubectl exec -it mssql-data-pool-master-0 -n clustertest -c mssql-data-pool-data -- bin/bash
root@mssql-data-pool-master-0:/# ls /tmp
```

Successivamente, ripristinare il backup del database per istanza master di SQL Server.  Se si sta ripristinando un backup di database che è stato creato in Windows, è necessario ottenere i nomi dei file.  In Ops Studio connesso all'istanza master, eseguire questo script SQL:

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/<db file name>.bak'
```

Esempio:

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
```

![Elenco di file di backup](media/restore-database/database-restore-file-list.png)

A questo punto, ripristinare il database con uno script simile al seguente, sostituendo i nomi o i percorsi in base alle esigenze a seconda del backup del database.

```sql
RESTORE DATABASE AdventureWorks2016CTP3
FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
WITH MOVE 'AdventureWorks2016CTP3_Data' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Data.mdf',
        MOVE 'AdventureWorks2016CTP3_Log' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Log.ldf',
        MOVE 'AdventureWorks2016CTP3_mod' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_mod'
```

A questo punto, se si desidera che il database di valore elevato essere in grado di accedere ai pool di dati che è necessario configurare il pool di dati le stored procedure aprendo ed eseguendo gli script dal repository GitHub.

Eseguire il **elevata-valore-db-configuration\data_pool_ddl_install. SQL** script.

- Supporto stored procedure di impostazione

Eseguire il **elevata-valore-db-configuration\supportability. SQL** script.
