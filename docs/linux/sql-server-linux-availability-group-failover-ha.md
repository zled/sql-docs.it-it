---
title: "Utilizzare il gruppo di disponibilità SQL Server in Linux | Documenti Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 07/20/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.workload: Inactive
ms.openlocfilehash: 68e41573c107725ef7af12e8b990678f8991bb02
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2018
---
# <a name="operate-always-on-availability-groups-on-linux"></a>Utilizzare sempre i gruppi di disponibilità su Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

## <a name="failover"></a>Gruppo di disponibilità il failover

Utilizzare gli strumenti di Gestione cluster di failover a un gruppo di disponibilità gestito da un gestore cluster esterno. Ad esempio, se una soluzione Usa Pacemaker per gestire un cluster Linux, usare `pcs` per eseguire il failover manuale su RHEL o Ubuntu. SLES utilizza `crm`. 

> [!IMPORTANT]
> In condizioni normali, non viene eseguito con gli strumenti di gestione di Transact-SQL o SQL Server come SQL Server Management Studio o PowerShell. Quando `CLUSTER_TYPE = EXTERNAL`, l'unico valore accettabile per `FAILOVER_MODE` è `EXTERNAL`. Con queste impostazioni, tutte le azioni di failover manuale o automatica vengono eseguite dal gestore del cluster esterno. 

### <a name="manual-failover-examples"></a>Esempi di failover manuale

Eseguire manualmente il failover del gruppo di disponibilità con gli strumenti di gestione del cluster esterno. In condizioni normali, non avviare il failover con Transact-SQL. Se gli strumenti di gestione del cluster esterno non risponde, è possibile forzare il gruppo di disponibilità per il failover. Per istruzioni per forzare il failover manuale, vedere [manuale spostare quando gli strumenti di cluster non sono reattivi](#forceManual).

Completare il failover manuale in due passaggi. 

1. Spostare la risorsa del gruppo di disponibilità dal nodo del cluster che sia proprietario delle risorse in un nuovo nodo.

   Gestione cluster di sposta la risorsa del gruppo di disponibilità e aggiunge un vincolo di percorso. Questo vincolo consente di configurare la risorsa per l'esecuzione del nuovo nodo. Per spostare che una manualmente o automaticamente il failover in futuro, è necessario rimuovere questo vincolo.

2. Rimuovere il vincolo di percorso.

#### <a name="1-manually-fail-over"></a>1. Il failover manuale

Per eseguire manualmente il failover di una risorsa del gruppo di disponibilità denominata *ag_cluster* al nodo cluster denominato *nodeName2*, eseguire il comando appropriato per la distribuzione:

- **Esempio RHEL/Ubuntu**

   ```bash
   sudo pcs resource move ag_cluster-master nodeName2 --master
   ```

- **Esempio SLES**

   ```bash
   crm resource migrate ag_cluster nodeName2
   ```



>[!IMPORTANT]
>Dopo aver eseguito manualmente su una risorsa, è necessario rimuovere un vincolo di percorso che viene aggiunto automaticamente durante lo spostamento.

#### <a name="2-remove-the-location-constraint"></a>2. Rimuovere il vincolo di posizione

Durante lo spostamento manuale, il `pcs` comando `move` o `crm` comando `migrate` aggiunge un vincolo di percorso per la risorsa da inserire nel nuovo nodo di destinazione. Per visualizzare il nuovo vincolo, eseguire il comando seguente dopo aver spostato manualmente la risorsa:

- **Esempio RHEL/Ubuntu**

   ```bash
   sudo pcs constraint --full
   ```

- **Esempio SLES**

   ```bash
   crm config show
   ```

È necessario rimuovere il vincolo di posizione per consentire la corretta esecuzione degli spostamenti futuri, incluso il failover automatico. 

Per rimuovere il vincolo, eseguire il comando seguente. 

- **Esempio RHEL/Ubuntu**

   In questo esempio `ag_cluster-master` è il nome della risorsa che è stato spostato. 

   ```bash
   sudo pcs resource clear ag_cluster-master 
   ```

- **Esempio SLES**

   In questo esempio `ag_cluster` è il nome della risorsa che è stato spostato. 

   ```bash
   crm resource clear ag_cluster
   ```

In alternativa, è possibile eseguire il comando seguente per rimuovere il vincolo di posizione.  

- **Esempio RHEL/Ubuntu**

   Nel comando seguente `cli-prefer-ag_cluster-master` è l'ID del vincolo che deve essere rimosso. `sudo pcs constraint --full` restituisce questo ID. 

   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```
- **Esempio SLES**

   Il comando seguente `cli-prefer-ms-ag_cluster` è l'ID del vincolo. `crm config show` restituisce questo ID. 
   
   ```bash
   crm configure
   delete cli-prefer-ms-ag_cluster 
   commit
   ```

>[!NOTE]
>Il failover automatico non comporta l'aggiunta di un vincolo di posizione, quindi non è necessaria alcuna operazione di pulizia. 

Per ulteriori informazioni:
- [Red Hat - Managing Cluster Resources](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/ch-manageresource-HAAR.html) (Red Hat - Gestione di risorse cluster)
- [Pacemaker - spostare manualmente le risorse](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-pcs/html/Clusters_from_Scratch/_move_resources_manually.html)
 [Guida all'amministrazione SLES - risorse](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.resource) 
 

### <a name="forceManual"></a> Manuale spostare quando gli strumenti di cluster non risponde 

In casi estremi, se un utente non è possibile utilizzare gli strumenti di gestione di cluster per l'interazione con il cluster (ad esempio il cluster non risponde, gli strumenti di gestione di cluster hanno un comportamento non corretto), l'utente potrebbe essere necessario eseguire il failover manualmente, ignorando la gestione del cluster esterno. Questo non è consigliabile per le normali operazioni e deve essere utilizzato in cluster non riesce a eseguire l'azione di failover utilizzando gli strumenti di Gestione cluster di case.

Se è possibile eseguire il failover del gruppo di disponibilità con gli strumenti di gestione di cluster, attenersi alla seguente procedura per eseguire il failover da strumenti di SQL Server:

1. Verificare che la risorsa del gruppo di disponibilità non è gestita dal cluster più. 

      - Tentativo di impostare la risorsa in modalità non gestita. Segnala l'agente di risorsa per arrestare il monitoraggio delle risorse e la gestione. Esempio: 
      
      ```bash
      sudo pcs resource unmanage <**resourceName**>
      ```

      - Se il tentativo di impostare la modalità di risorsa in modalità non gestita non riesce, eliminare la risorsa. Esempio:

      ```bash
      sudo pcs resource delete <**resourceName**>
      ```

      >[!NOTE]
      >Quando si elimina una risorsa verranno inoltre eliminati tutti i vincoli associati. 

1. Impostare manualmente la variabile di contesto di sessione `external_cluster`.

   ```Transact-SQL
   EXEC sp_set_session_context @key = N'external_cluster', @value = N'yes';
   ```

1. Failover del gruppo di disponibilità con Transact-SQL. Nell'esempio seguente, sostituire `<**MyAg**>` con il nome del gruppo di disponibilità. Connettersi all'istanza di SQL Server che ospita la replica secondaria di destinazione ed eseguire il comando seguente:

   ```Transact-SQL
   ALTER AVAILABILITY GROUP <**MyAg**> FAILOVER;
   ```

1. Riavviare Gestione e monitoraggio delle risorse cluster. Eseguire il comando seguente:

   ```bash
   sudo pcs resource manage <**resourceName**>
   sudo pcs resource cleanup <**resourceName**>
   ```

## <a name="database-level-monitoring-and-failover-trigger"></a>Trigger di monitoraggio e failover di livello database

Per `CLUSTER_TYPE=EXTERNAL`, la semantica di trigger di failover è diversa rispetto a WSFC. Quando il gruppo di disponibilità in un'istanza di SQL Server in un cluster WSFC, la transizione da `ONLINE` stato per il database fa sì che l'integrità del gruppo di disponibilità segnalare un errore. Questo segnalerà la gestione di cluster per attivare un'azione di failover. In Linux, l'istanza di SQL Server non può comunicare con il cluster. Monitoraggio per l'integrità del database viene eseguito "esterno in". Se utente scelto per il monitoraggio del failover di livello database e il failover (impostando l'opzione `DB_FAILOVER=ON` quando si crea il gruppo di disponibilità), il cluster viene verificato se lo stato del database `ONLINE` ogni volta che al momento dell'esecuzione di un'azione di monitoraggio. Il cluster esegue query sullo stato in `sys.databases`. Per qualsiasi stato diverso da quello `ONLINE`, attiverà un failover automaticamente (se vengono soddisfatte le condizioni di failover automatico). Il tempo effettivo del failover dipende dalla frequenza dell'azione di monitoraggio, nonché lo stato del database viene aggiornato in sys. Databases.

## <a name="upgrade-availability-group"></a>Aggiornare il gruppo di disponibilità

Prima di aggiornare un gruppo di disponibilità, esaminare le procedure consigliate in [l'aggiornamento di istanze di replica di disponibilità gruppo](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).

Le sezioni seguenti illustrano come eseguire un aggiornamento in sequenza con istanze di SQL Server in Linux con gruppi di disponibilità. 

### <a name="upgrade-steps-on-linux"></a>Passaggi di aggiornamento su Linux

Quando repliche del gruppo di disponibilità si trovano in istanze di SQL Server in Linux, il tipo di cluster del gruppo di disponibilità è `EXTERNAL` o `NONE`. Un gruppo di disponibilità che è gestito da Gestione cluster di diversi da Windows Server Failover Cluster (WSFC) `EXTERNAL`. Pacemaker con Corosync è riportato un esempio di Gestione cluster esterno. Dispone di un gruppo di disponibilità con alcuna Gestione cluster di tipo cluster `NONE` i passaggi di aggiornamento descritti di seguito sono specifici per i gruppi di disponibilità di tipo cluster `EXTERNAL` o `NONE`.

1. Prima di iniziare, eseguire il backup di ogni database.
2. Aggiornare le istanze di SQL Server di ospitare le repliche secondarie.

    A. Prima di tutto aggiornare repliche secondarie asincrone.

    B. Aggiornare le repliche secondarie sincrone.

   >[!NOTE]
   >Se un gruppo di disponibilità dispone solo di asincrona repliche - per evitare eventuali perdite di dati modificare una replica sincrona e attendere fino a quando viene sincronizzata. Quindi aggiornare la replica.
   
   b.1. Interrompere la risorsa nel nodo che ospita la replica secondaria di destinazione per l'aggiornamento
   
   Prima di eseguire il comando di aggiornamento, è possibile interrompere la risorsa in modo che il cluster non verrà monitorarlo e negativo inutilmente. Nell'esempio seguente aggiunge un vincolo di percorso sul nodo che si tradurrà sulla risorsa da arrestare. Aggiornamento `ag_cluster-master` con il nome della risorsa e `nodeName1` con il nodo che ospita la replica di destinazione per l'aggiornamento.

   ```bash
   pcs constraint location ag_cluster-master avoids nodeName1
   ```
   b.2. Aggiornamento di SQL Server nella replica secondaria

   Nell'esempio seguente viene aggiornata `mssql-server` e `mssql-server-ha` pacchetti.

   ```bash
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
   b.3. Rimuovere il vincolo di posizione

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

1. Dopo il failover, è possibile aggiornare SQL Server nella replica primaria precedente ripetendo la stessa procedura descritta nei passaggi da b. 1-b. 3.

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

1. Riprendere lo spostamento dei dati per la replica secondaria appena aggiornata - la replica primaria precedente. Ciò è necessario quando un'istanza di versione superiore di SQL Server è il trasferimento di blocchi di log in un'istanza di versione inferiore in un gruppo di disponibilità. Eseguire il comando seguente nella nuova replica secondaria (la replica primaria precedente).

   ```transact-sql
   ALTER DATABASE database_name SET HADR RESUME;
   ```

Dopo l'aggiornamento di tutti i server, è possibile eseguire il failback - failover back alla replica primaria originale, se necessario. 

## <a name="drop-an-availability-group"></a>Eliminare un gruppo di disponibilità

Per eliminare un gruppo di disponibilità, eseguire [DROP AVAILABILITY GROUP](../t-sql/statements/drop-availability-group-transact-sql.md). Se il tipo di cluster è `EXTERNAL` o `NONE` eseguire il comando in ogni istanza di SQL Server che ospita una replica. Ad esempio, per eliminare un gruppo di disponibilità denominato `group_name` eseguire il comando seguente:

   ```transact-sql
   DROP AVAILABILITY GROUP group_name
   ```
 

## <a name="next-steps"></a>Passaggi successivi

[Configurare i Cluster di Red Hat Enterprise Linux per le risorse Cluster il gruppo di disponibilità di SQL Server](sql-server-linux-availability-group-cluster-rhel.md)

[Configurare i Cluster di SUSE Linux Enterprise Server per le risorse Cluster il gruppo di disponibilità di SQL Server](sql-server-linux-availability-group-cluster-sles.md)

[Configurare il Cluster Ubuntu per le risorse Cluster il gruppo di disponibilità di SQL Server](sql-server-linux-availability-group-cluster-ubuntu.md)
