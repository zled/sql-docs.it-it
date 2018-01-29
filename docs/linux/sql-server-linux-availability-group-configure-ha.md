---
title: "Configurare SQL Server gruppo di disponibilità AlwaysOn per la disponibilità elevata in Linux | Documenti Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 01/24/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 
ms.workload: On Demand
ms.openlocfilehash: c510789ccd2c76e2d4e3b7bd8354a46e80e335c2
ms.sourcegitcommit: 0a9c29c7576765f3b5774b2e087852af42ef4c2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="configure-sql-server-always-on-availability-group-for-high-availability-on-linux"></a>Configurare SQL Server gruppo di disponibilità AlwaysOn per la disponibilità elevata in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

In questo articolo viene descritto come creare un SQL Server AlwaysOn in gruppo di disponibilità (AG) per la disponibilità elevata in Linux. Esistono due tipi di configurazione per estensivi. Oggetto *la disponibilità elevata* configurazione utilizza una gestione di cluster per assicurare la continuità aziendale. Questa configurazione può includere anche le repliche di scala di lettura. Questo documento illustra come creare il gruppo di disponibilità per la disponibilità elevata.

È inoltre possibile creare un gruppo di disponibilità senza un cluster di gestione per *lettura scala*. Il gruppo di disponibilità per la lettura scala fornisce solo le repliche di sola lettura per la scalabilità di prestazioni. Non fornisce la disponibilità elevata. Per creare un gruppo di disponibilità per la scala di lettura, vedere [configurare un gruppo di disponibilità di SQL Server per la scala di lettura in Linux](sql-server-linux-availability-group-configure-rs.md).

Le configurazioni che garantire l'elevata disponibilità e protezione dei dati richiedono due o tre sincrono commit repliche. Con tre repliche sincrone, il gruppo di disponibilità può recuperare automaticamente anche se un server non è disponibile. Per ulteriori informazioni, vedere [elevata disponibilità e protezione dei dati per le configurazioni del gruppo di disponibilità](sql-server-linux-availability-group-ha.md). 

Tutti i server devono essere fisico o virtuale e server virtuali devono eseguire la stessa piattaforma di virtualizzazione. Questo requisito è che gli agenti fencing sono specifici della piattaforma. Vedere [criteri per i cluster Guest](https://access.redhat.com/articles/29440#guest_policies).

## <a name="roadmap"></a>Guida di orientamento

I passaggi per creare un gruppo di disponibilità su server Linux per la disponibilità elevata sono diversi da quelle in un cluster di failover di Windows Server. L'elenco seguente descrive i passaggi generali: 

1. [Configurare SQL Server in tre server di cluster](sql-server-linux-setup.md).

   >[!IMPORTANT]
   >Tutti e tre i server del gruppo di disponibilità è necessario essere sulla stessa piattaforma - fisica o virtuale, perché la disponibilità elevata di Linux Usa fencing agenti per isolare le risorse nei server. Gli agenti fencing sono specifici per ogni piattaforma.

2. Creare il gruppo di disponibilità. Questo passaggio è illustrato in questo articolo corrente. 

3. Configurare un gestore di risorse cluster, ad esempio Pacemaker.
   
   Il modo per configurare un gestore di risorse cluster dipende dalla distribuzione Linux specifica. Vedere i collegamenti seguenti per istruzioni specifiche di distribuzione: 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   * [SUSE](sql-server-linux-availability-group-cluster-sles.md)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

   >[!IMPORTANT]
   >Gli ambienti di produzione richiedono un agente di geofencing, ad esempio STONITH per la disponibilità elevata. Dimostrazione di questa documentazione non utilizzano agenti fencing. Dimostrazioni sono per i test e convalida solo. 
   
   >Un cluster Linux Usa fencing per restituire il cluster a uno stato noto. Il modo per configurare fencing varia a seconda della distribuzione e l'ambiente. Fencing non è attualmente disponibile in alcuni ambienti cloud. Per ulteriori informazioni, vedere [criteri di supporto per RHEL cluster disponibilità elevata - piattaforme di virtualizzazione](https://access.redhat.com/articles/29440).
   
   >Per SLES, vedere [estensione disponibilità elevata di SUSE Linux Enterprise](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing).

5. Aggiungere il gruppo di disponibilità come una risorsa del cluster.  

   La modalità per aggiungere il gruppo di disponibilità come una risorsa del cluster dipende dalla distribuzione di Linux. Vedere i collegamenti seguenti per istruzioni specifiche di distribuzione: 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource)
   * [SLES](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource)

[!INCLUDE [Create Prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-ag"></a>Creare il gruppo di disponibilità

Per una configurazione a disponibilità elevata che garantisce il failover automatico, il gruppo di disponibilità richiede almeno tre repliche. Una delle seguenti configurazioni può supportare la disponibilità elevata:

- [Tre repliche sincrone](sql-server-linux-availability-group-ha.md#threeSynch)

- [Una replica di configurazione più di due repliche sincrone](sql-server-linux-availability-group-ha.md#twoSynch)

Per informazioni, vedere [elevata disponibilità e protezione dei dati per le configurazioni del gruppo di disponibilità](sql-server-linux-availability-group-ha.md).

>[!NOTE]
>I gruppi di disponibilità possono includere altre repliche sincrone o asincrone. 

Creare il gruppo di disponibilità per la disponibilità elevata in Linux. Utilizzare il [Crea gruppo di disponibilità](https://docs.microsoft.com/en-us/sql/t-sql/statements/create-availability-group-transact-sql) con `CLUSTER_TYPE = EXTERNAL`. 

* Gruppo di disponibilità - `CLUSTER_TYPE = EXTERNAL` specifica che un'entità esterna cluster gestisce il gruppo di disponibilità. Pacemaker è riportato un esempio di un'entità esterna. Quando il tipo di cluster del gruppo di disponibilità è esterno, 

* Set di repliche primarie e secondarie `FAILOVER_MODE = EXTERNAL`. 
   Specifica che la replica interagisce con una gestione di cluster esterno, ad esempio Pacemaker. 

Gli script Transact-SQL seguenti creano un gruppo di disponibilità per la disponibilità elevata denominata `ag1`. Lo script consente di configurare le repliche del gruppo di disponibilità con `SEEDING_MODE = AUTOMATIC`. Questa impostazione, SQL Server creare automaticamente il database in ciascun server secondario. Aggiornare lo script seguente per l'ambiente. Sostituire il `**<node1>**`, `**<node2>**`, o `**<node3>**` valori con i nomi delle istanze di SQL Server che ospitano le repliche. Sostituire il `**<5022>**` con la porta è impostata per i dati dell'endpoint del mirroring. Per creare il gruppo di disponibilità, eseguire l'istruzione Transact-SQL seguente sull'istanza di SQL Server che ospita la replica primaria.

Eseguire **sola** degli script di seguito: 

- [Creare il gruppo di disponibilità con repliche sincrone tre](#threeSynch).
- [Creare il gruppo di disponibilità con due repliche sincrone e una replica di configurazione](#configOnly)
- [Creare il gruppo di disponibilità con due repliche sincrone](#readScale).

<a name="threeSynch"></a>

- Crea gruppo di disponibilità con tre repliche sincrone

   ```SQL
   CREATE AVAILABILITY GROUP [ag1]
       WITH (DB_FAILOVER = ON, CLUSTER_TYPE = EXTERNAL)
       FOR REPLICA ON
           N'**<node1>**' 
            WITH (
               ENDPOINT_URL = N'tcp://**<node1>:**<5022>**',
               AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
               FAILOVER_MODE = EXTERNAL,
               SEEDING_MODE = AUTOMATIC
               ),
           N'**<node2>**' 
            WITH ( 
               ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**', 
               AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
               FAILOVER_MODE = EXTERNAL,
               SEEDING_MODE = AUTOMATIC
               ),
           N'**<node3>**'
           WITH( 
              ENDPOINT_URL = N'tcp://**<node3>**:**<5022>**', 
              AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
              FAILOVER_MODE = EXTERNAL,
              SEEDING_MODE = AUTOMATIC
              );
        
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```

   >[!IMPORTANT]
   >Dopo aver eseguito lo script precedente per creare un gruppo di disponibilità con tre repliche sincrone, non eseguire lo script seguente:

- Crea gruppo di disponibilità con due repliche sincrone e una replica di configurazione:

   >[!IMPORTANT]
   >Questa architettura consente a qualsiasi edizione di SQL Server per ospitare la replica di terza. Ad esempio, la terza replica può essere ospitata in SQL Server Enterprise Edition. In Enterprise Edition, è il tipo di endpoint valido solo `WITNESS`. 

   ```SQL
   CREATE AVAILABILITY GROUP [ag1] 
      WITH (CLUSTER_TYPE = EXTERNAL) 
      FOR REPLICA ON 
       N'**<node1>**' WITH ( 
          ENDPOINT_URL = N'tcp://**<node1>**:**<5022>**', 
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = EXTERNAL, 
          SEEDING_MODE = AUTOMATIC 
          ), 
       N'**<node2>**' WITH (  
          ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**',  
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = EXTERNAL, 
          SEEDING_MODE = AUTOMATIC 
          ), 
       N'**<node3>**' WITH ( 
          ENDPOINT_URL = N'tcp://**<node3>**:**<5022>**', 
          AVAILABILITY_MODE = CONFIGURATION_ONLY  
          );
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```
<a name="readScale"></a>

- Crea gruppo di disponibilità con due repliche sincrone

   Includere le due repliche con modalità di disponibilità sincrono. Ad esempio, lo script seguente crea un gruppo di disponibilità denominato `ag1`. `node1`e `node2` le repliche in modalità sincrona, con seeding automatico e il failover automatico.

   >[!IMPORTANT]
   >Eseguire solo lo script seguente per creare un gruppo di disponibilità con due repliche sincrone. Impossibile eseguire lo script seguente se è stato eseguito uno script precedente. 

   ```SQL
   CREATE AVAILABILITY GROUP [ag1]
      WITH (CLUSTER_TYPE = EXTERNAL)
      FOR REPLICA ON
      N'node1' WITH (
         ENDPOINT_URL = N'tcp://node1:5022',
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
         FAILOVER_MODE = EXTERNAL,
         SEEDING_MODE = AUTOMATIC
      ),
      N'node2' WITH ( 
         ENDPOINT_URL = N'tcp://node2:5022', 
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
         FAILOVER_MODE = EXTERNAL,
         SEEDING_MODE = AUTOMATIC
      );
        
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```


È inoltre possibile configurare un gruppo di disponibilità con `CLUSTER_TYPE=EXTERNAL` con SQL Server Management Studio o PowerShell. 

### <a name="join-secondary-replicas-to-the-ag"></a>Creare un join delle repliche secondarie per il gruppo di disponibilità

Lo script Transact-SQL seguente aggiunge un'istanza di SQL Server a un gruppo di disponibilità denominato `ag1`. Aggiornare lo script per l'ambiente. In ogni istanza di SQL Server che ospita una replica secondaria, eseguire Transact-SQL seguente per creare un join del gruppo di disponibilità.

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create Post](../includes/ss-linux-cluster-availability-group-create-post.md)]

>[!IMPORTANT]
>Dopo aver creato il gruppo di disponibilità, è necessario configurare l'integrazione con una tecnologia di cluster come Pacemaker per la disponibilità elevata. Per una configurazione di scalabilità di lettura utilizzando estensivi, a partire da [!INCLUDE [SQL Server version](..\includes\sssqlv14-md.md)], configurazione di un cluster non è necessaria.

Se è stata seguita la procedura in questo documento, è necessario un gruppo di disponibilità non è ancora in cluster. Il passaggio successivo consiste nell'aggiungere il cluster. Questa configurazione è valida per scenari di bilanciamento del carico di caricamento/scalabilità-lettura, non è completa per la disponibilità elevata. Per la disponibilità elevata, è necessario aggiungere il gruppo di disponibilità come risorsa cluster. Vedere [passaggi successivi](#next-steps) per le istruzioni. 

## <a name="notes"></a>Note

>[!IMPORTANT]
>Dopo aver configurato il cluster e aggiungere il gruppo di disponibilità come risorsa cluster, è possibile utilizzare Transact-SQL per le risorse del gruppo di disponibilità il failover. Risorse del cluster di SQL Server in Linux non sono collegate come strettamente con il sistema operativo come se fossero in un Windows Server Failover Cluster (WSFC). Servizio SQL Server non riconosce la presenza del cluster. Tutte le orchestrazioni viene eseguita tramite gli strumenti di gestione di cluster. RHEL o Ubuntu utilizzare `pcs`. In SLES utilizzare `crm`. 

>[!IMPORTANT]
>Se il gruppo di disponibilità è una risorsa cluster, si verifica un problema noto nella versione corrente, in cui il failover forzato con perdita di dati a una replica asincrona non funziona. Questo problema verrà risolto nella prossima versione. Failover manuale o automatico in una replica sincrona ha esito positivo. 


## <a name="next-steps"></a>Passaggi successivi

[Configurare i Cluster di Red Hat Enterprise Linux per le risorse Cluster il gruppo di disponibilità di SQL Server](sql-server-linux-availability-group-cluster-rhel.md)

[Configurare i Cluster di SUSE Linux Enterprise Server per le risorse Cluster il gruppo di disponibilità di SQL Server](sql-server-linux-availability-group-cluster-sles.md)

[Configurare il Cluster Ubuntu per le risorse Cluster il gruppo di disponibilità di SQL Server](sql-server-linux-availability-group-cluster-ubuntu.md)
