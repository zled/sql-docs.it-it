---
title: Utilizzare il gruppo di disponibilità SQL Server in Linux | Documenti Microsoft
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/01/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.openlocfilehash: 3316cb34fb6bd780807cd0f205a88cf418dd22d1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="operate-always-on-availability-groups-on-linux"></a>Utilizzare sempre i gruppi di disponibilità su Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

## <a name="upgrade-availability-group"></a>Aggiornare il gruppo di disponibilità

Prima di aggiornare un gruppo di disponibilità, esaminare i modelli e procedure consigliate in [l'aggiornamento di istanze di replica di disponibilità gruppo](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).

Le sezioni seguenti illustrano come eseguire un aggiornamento in sequenza con istanze di SQL Server in Linux con gruppi di disponibilità. 

### <a name="upgrade-steps-on-linux"></a>Passaggi di aggiornamento su Linux

Quando repliche del gruppo di disponibilità si trovano in istanze di SQL Server in Linux, il tipo di cluster del gruppo di disponibilità è `EXTERNAL` o `NONE`. Un gruppo di disponibilità che è gestito da Gestione cluster di diversi da Windows Server Failover Cluster (WSFC) `EXTERNAL`. Pacemaker con Corosync è riportato un esempio di Gestione cluster esterno. Dispone di un gruppo di disponibilità con alcuna Gestione cluster di tipo cluster `NONE` i passaggi di aggiornamento descritti di seguito sono specifici per i gruppi di disponibilità di tipo cluster `EXTERNAL` o `NONE`.

L'ordine in cui l'aggiornamento di istanze dipende se il ruolo secondario e al fatto le repliche sincrone o asincrone. Aggiornare le istanze di SQL Server che ospitano repliche secondarie asincrone prima. Aggiornare quindi le istanze che ospitano le repliche secondarie sincrone. 

   >[!NOTE]
   >Se un gruppo di disponibilità dispone solo di asincrona repliche, per evitare eventuali perdite di dati modificare una replica sincrona e attendere fino a quando viene sincronizzata. Quindi aggiornare la replica.
   
Prima di iniziare, eseguire il backup di ogni database.

1. Interrompere la risorsa nel nodo che ospita la replica secondaria di destinazione per l'aggiornamento.
   
   Prima di eseguire il comando di aggiornamento, è possibile interrompere la risorsa in modo che il cluster non verrà monitorarlo e negativo inutilmente. Nell'esempio seguente aggiunge un vincolo di percorso sul nodo che si tradurrà sulla risorsa da arrestare. Aggiornamento `ag_cluster-master` con il nome della risorsa e `nodeName1` con il nodo che ospita la replica di destinazione per l'aggiornamento.

   ```bash
   pcs constraint location ag_cluster-master avoids nodeName1
   ```

1. Aggiornare SQL Server nella replica secondaria.

   Nell'esempio seguente viene aggiornata `mssql-server` e `mssql-server-ha` pacchetti.

   ```bash
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
1. Rimuovere il vincolo di percorso.

   Prima di eseguire il comando di aggiornamento, è possibile interrompere la risorsa in modo che il cluster non verrà monitorarlo e negativo inutilmente. Nell'esempio seguente aggiunge un vincolo di percorso sul nodo che si tradurrà sulla risorsa da arrestare. Aggiornamento `ag_cluster-master` con il nome della risorsa e `nodeName1` con il nodo che ospita la replica di destinazione per l'aggiornamento.

   ```bash
   pcs constraint remove location-ag_cluster-master-rhel1--INFINITY
   ```
   Come procedura consigliata, verificare la risorsa sia stata avviata (utilizzando `pcs status` comando) e la replica secondaria è connesso e sincronizzato lo stato dopo l'aggiornamento.

1. Dopo avere aggiornate tutte le repliche secondarie, eseguire manualmente il failover a una delle repliche secondarie sincrone.

   Per i gruppi di disponibilità con `EXTERNAL` tipo di cluster, utilizzare gli strumenti di gestione di cluster per eseguire il failover; gruppi di disponibilità con `NONE` tipo di cluster deve utilizzare Transact-SQL per eseguire il failover. 
   Nell'esempio seguente viene eseguito il failover di un gruppo di disponibilità con gli strumenti di gestione di cluster. Sostituire `<targetReplicaName>` con il nome della replica sincrona secondaria che diventerà principale:

   ```bash
   sudo pcs resource move ag_cluster-master <targetReplicaName> --master  
   ``` 
   
   >[!IMPORTANT]
   >I passaggi seguenti si applicano solo ai gruppi di disponibilità che non dispongono di un gestore cluster.

   Se il tipo di cluster di gruppo di disponibilità è `NONE`manualmente il failover. Completare i passaggi seguenti nell'ordine indicato:

      A. Il comando seguente imposta la replica primaria a secondaria. Sostituire `AG1` con il nome del gruppo di disponibilità. Eseguire il comando Transact-SQL nell'istanza di SQL Server che ospita la replica primaria.

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] SET (ROLE = SECONDARY);
      ```

      B. Il comando seguente imposta una replica secondaria asincrona primario. Il seguente comando Transact-SQL nell'istanza di destinazione di SQL Server - l'istanza che ospita la replica secondaria asincrona.

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] FAILOVER;
      ```

1. Dopo il failover, è possibile aggiornare SQL Server nella replica primaria precedente ripetendo la procedura precedente.

   Nell'esempio seguente viene aggiornata `mssql-server` e `mssql-server-ha` pacchetti.

   ```bash
   # add constraint for the resource to stop on the upgraded node
   # replace 'nodename2' with the name of the cluster node targeted for upgrade
   pcs constraint location ag_cluster-master avoids nodeName2
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
   
   ```bash
   # upgrade mssql-server and mssql-server-ha packages
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```

   ```bash
   # remove the constraint; make sure the resource is started and replica is connected and synchronized
   pcs constraint remove location-ag_cluster-master-rhel1--INFINITY
   ```

1. Per un gruppi di disponibilità con un gestore cluster esterno - tipo di cluster in cui è esterno, eliminare il vincolo di percorso che è stato causato dal failover manuale. 

   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```

1. Riprendere lo spostamento dei dati per la replica secondaria appena aggiornata - la replica primaria precedente. Questo passaggio è obbligatorio quando un'istanza di versione superiore di SQL Server è il trasferimento di blocchi di log in un'istanza di versione inferiore in un gruppo di disponibilità. Eseguire il comando seguente nella nuova replica secondaria (la replica primaria precedente).

   ```transact-sql
   ALTER DATABASE database_name SET HADR RESUME;
   ```

Dopo l'aggiornamento di tutti i server, è possibile eseguire il failback. Eseguire il failover back alla replica primaria originale, se necessario. 

## <a name="drop-an-availability-group"></a>Eliminare un gruppo di disponibilità

Per eliminare un gruppo di disponibilità, eseguire [DROP AVAILABILITY GROUP](../t-sql/statements/drop-availability-group-transact-sql.md). Se il tipo di cluster è `EXTERNAL` o `NONE` eseguire il comando in ogni istanza di SQL Server che ospita una replica. Ad esempio, per eliminare un gruppo di disponibilità denominato `group_name` eseguire il comando seguente:

   ```transact-sql
   DROP AVAILABILITY GROUP group_name
   ```
 

## <a name="next-steps"></a>Passaggi successivi

[Configurare i Cluster di Red Hat Enterprise Linux per le risorse Cluster il gruppo di disponibilità di SQL Server](sql-server-linux-availability-group-cluster-rhel.md)

[Configurare i Cluster di SUSE Linux Enterprise Server per le risorse Cluster il gruppo di disponibilità di SQL Server](sql-server-linux-availability-group-cluster-sles.md)

[Configurare il Cluster Ubuntu per le risorse Cluster il gruppo di disponibilità di SQL Server](sql-server-linux-availability-group-cluster-ubuntu.md)
