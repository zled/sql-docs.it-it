---
title: "Gestisci failover del gruppo di disponibilità, SQL Server in Linux | Documenti Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/01/2018
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
ms.openlocfilehash: 086cf16e243810452a3bace411abdc3689e74ff8
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="always-on-availability-group-failover-on-linux"></a>Failover gruppo di disponibilità AlwaysOn su Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Nel contesto di un gruppo di disponibilità (AG), il ruolo primario e il ruolo secondario delle repliche di disponibilità sono generalmente intercambiabili in un processo noto come failover. Sono disponibili tre tipi di failover: failover automatico (senza perdita di dati), failover manuale pianificato (senza perdita di dati) e failover manuale forzato (con possibile perdita di dati), in genere chiamato *failover forzato*. Failover manuale automatico e pianificato vengono conservati tutti i dati. Un gruppo di disponibilità il failover a livello di replica di disponibilità. Ovvero, un gruppo di disponibilità viene eseguito in una delle relative repliche secondarie (la destinazione del failover corrente). 

Per informazioni generali sul failover, vedere [il Failover e modalità](../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md).

## <a name="failover"></a>failover manuale

Utilizzare gli strumenti di Gestione cluster di failover a un gruppo di disponibilità gestito da un gestore cluster esterno. Ad esempio, se una soluzione Usa Pacemaker per gestire un cluster Linux, usare `pcs` per eseguire il failover manuale su RHEL o Ubuntu. SLES utilizza `crm`. 

> [!IMPORTANT]
> In condizioni normali, non viene eseguito con gli strumenti di gestione di Transact-SQL o SQL Server come SQL Server Management Studio o PowerShell. Quando `CLUSTER_TYPE = EXTERNAL`, l'unico valore accettabile per `FAILOVER_MODE` è `EXTERNAL`. Con queste impostazioni, tutte le azioni di failover manuale o automatica vengono eseguite dal gestore del cluster esterno. Per istruzioni su come forzare il failover con potenziale perdita di dati, vedere [forzare il failover](#forceFailover).

### <a name="a-namemanualfailovermanual-failover-steps"></a><a name="manualFailover">Passaggi del failover manuale

Per eseguire il failover, la replica secondaria che diventerà la replica primaria deve essere sincrona. Se una replica secondaria è asincrona, [modificare la modalità di disponibilità](../database-engine/availability-groups/windows/change-the-availability-mode-of-an-availability-replica-sql-server.md).

Failover manuale in due passaggi.

   Prima di tutto,[ manualmente il failover spostando risorsa gruppo di disponibilità](#manualMove) dal nodo del cluster che sia proprietario delle risorse in un nuovo nodo.

   Il cluster di failover della risorsa del gruppo di disponibilità e aggiunge un vincolo di percorso. Questo vincolo consente di configurare la risorsa per l'esecuzione del nuovo nodo. Per eseguire il failover in futuro, è necessario rimuovere questo vincolo.

   In secondo luogo, [rimuovere il vincolo di percorso](#removeLocConstraint).

#### <a name="a-namemanualmovestep-1-manually-fail-over-by-moving-availability-group-resource"></a><a name="manualMove">Passaggio 1. Eseguire manualmente spostando risorsa gruppo di disponibilità

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
>Dopo aver eseguito manualmente su una risorsa, è necessario rimuovere un vincolo di percorso che viene aggiunto automaticamente.

#### <a name="a-nameremovelocconstraint-step-2-remove-the-location-constraint"></a><a name="removeLocConstraint"> Passaggio 2. Rimuovere il vincolo di posizione

Durante un failover manuale, il `pcs` comando `move` o `crm` comando `migrate` aggiunge un vincolo di percorso per la risorsa da inserire nel nuovo nodo di destinazione. Per visualizzare il nuovo vincolo, eseguire il comando seguente dopo aver spostato manualmente la risorsa:

- **Esempio RHEL/Ubuntu**

   ```bash
   sudo pcs constraint --full
   ```

- **Esempio SLES**

   ```bash
   crm config show
   ```

Rimuovere il vincolo di percorso failover future, incluso il failover automatico, avere esito positivo. 

Per rimuovere il vincolo, eseguire il comando seguente: 

- **Esempio RHEL/Ubuntu**

   In questo esempio `ag_cluster-master` è il nome della risorsa che è stato eseguito il failover. 

   ```bash
   sudo pcs resource clear ag_cluster-master 
   ```

- **Esempio SLES**

   In questo esempio `ag_cluster` è il nome della risorsa che è stato eseguito il failover. 

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
 
## <a name="forceFailover"></a> Forzare il failover 

Un failover forzato è progettato esclusivamente per il ripristino di emergenza. In questo caso, è possibile eseguire il failover con gli strumenti di gestione di cluster perché il data center principale è inattivo. Se si forza il failover in una replica secondaria non sincronizzata, è possibile che vengano persi alcuni dati. Forzare il failover solo se è necessario ripristinare il servizio per il gruppo di disponibilità immediatamente e sono disposti a rischiare la perdita di dati.

Se è possibile utilizzare gli strumenti di gestione di cluster per l'interazione con il cluster, ad esempio, se il cluster è bloccato a causa di un evento di emergenza nel data center principale, è necessario forzare il failover per ignorare la gestione del cluster esterno. Questa procedura non è consigliata per le normali operazioni, perché si rischia di perdita di dati. Utilizzarlo quando gli strumenti di gestione di cluster non riescono a eseguire l'azione di failover. A livello funzionale, questa procedura è simile a [esegue un failover manuale forzato](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) in un gruppo di disponibilità in Windows.
 
Questo processo per il failover forzato è specifico di SQL Server in Linux.

1. Verificare che la risorsa del gruppo di disponibilità non è gestita dal cluster più. 

      - Impostare le risorse in modalità non gestita nel nodo del cluster di destinazione. Questo comando segnala l'agente di risorsa per il monitoraggio delle risorse di arresto e gestione. Esempio: 
      
      ```bash
      sudo pcs resource unmanage <resourceName>
      ```

      - Se il tentativo di impostare la modalità di risorsa in modalità non gestita non riesce, eliminare la risorsa. Esempio:

      ```bash
      sudo pcs resource delete <resourceName>
      ```

      >[!NOTE]
      >Quando si elimina una risorsa, verranno inoltre eliminati tutti i vincoli associati. 

1. Nell'istanza di SQL Server che ospita la replica secondaria, impostare la variabile di contesto di sessione `external_cluster`.

   ```Transact-SQL
   EXEC sp_set_session_context @key = N'external_cluster', @value = N'yes';
   ```

1. Eseguire il failover del gruppo di disponibilità con Transact-SQL. Nell'esempio seguente, sostituire `<MyAg>` con il nome del gruppo di disponibilità. Connettersi all'istanza di SQL Server che ospita la replica secondaria di destinazione ed eseguire il comando seguente:

   ```Transact-SQL
   ALTER AVAILABILITY GROUP <MyAg> FORCE_FAILOVER_ALLOW_DATA_LOSS;
   ```

1.  Dopo un failover forzato, portare il gruppo di disponibilità a uno stato integro prima di riavviare la gestione e monitoraggio delle risorse del cluster o ricreare la risorsa del gruppo di disponibilità. Esaminare il [attività essenziali dopo un Failover forzato](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md#FollowUp).

1.  Riavviare Gestione e monitoraggio delle risorse cluster:

   Per riavviare la gestione e monitoraggio delle risorse cluster, eseguire il comando seguente:

   ```bash
   sudo pcs resource manage <resourceName>
   sudo pcs resource cleanup <resourceName>
   ```

   Se è stata eliminata la risorsa cluster, è necessario ricrearlo. Per ricreare la risorsa cluster, seguire le istruzioni in [Crea risorsa gruppo di disponibilità](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource).

>[!Important]
>Non utilizzare i passaggi precedenti per l'analisi di ripristino di emergenza in quanto è il rischio di perdita di dati. Invece di modificare la replica asincrona sincrono e le istruzioni per [normale failover manuale](#manualFailover).

## <a name="database-level-monitoring-and-failover-trigger"></a>Trigger di monitoraggio e failover di livello database

Per `CLUSTER_TYPE=EXTERNAL`, la semantica di trigger di failover è diversa rispetto a WSFC. Quando il gruppo di disponibilità si trova in un'istanza di SQL Server in un cluster WSFC, la transizione da `ONLINE` stato per il database fa sì che l'integrità del gruppo di disponibilità segnalare un errore. In risposta, la gestione di cluster avvia un'azione di failover. In Linux, l'istanza di SQL Server non può comunicare con il cluster. Il monitoraggio per l'integrità del database avviene *esterno aggiuntivo*. Se utente scelto per il monitoraggio del failover di livello database e il failover (impostando l'opzione `DB_FAILOVER=ON` durante la creazione del gruppo di disponibilità), il cluster viene verificato se lo stato del database `ONLINE` ogni volta che esegue un'azione di monitoraggio. Il cluster esegue query sullo stato in `sys.databases`. Per qualsiasi stato diverso da quello `ONLINE`, attiverà un failover automaticamente (se vengono soddisfatte le condizioni di failover automatico). Il tempo effettivo del failover dipende dalla frequenza dell'azione di monitoraggio, nonché lo stato del database viene aggiornato in sys. Databases.

Failover automatico richiede almeno una replica sincrona.

## <a name="next-steps"></a>Passaggi successivi

[Configurare i Cluster di Red Hat Enterprise Linux per le risorse Cluster il gruppo di disponibilità di SQL Server](sql-server-linux-availability-group-cluster-rhel.md)

[Configurare i Cluster di SUSE Linux Enterprise Server per le risorse Cluster il gruppo di disponibilità di SQL Server](sql-server-linux-availability-group-cluster-sles.md)

[Configurare il Cluster Ubuntu per le risorse Cluster il gruppo di disponibilità di SQL Server](sql-server-linux-availability-group-cluster-ubuntu.md)
