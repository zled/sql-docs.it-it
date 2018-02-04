---
title: "Configurare un gruppo di disponibilità di SQL Server per la scala di lettura in Linux | Documenti Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
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
ms.workload: Inactive
ms.openlocfilehash: e2ce8a7cd87e188fce0f1b0f62bde148324373a5
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="configure-a-sql-server-availability-group-for-read-scale-on-linux"></a>Configurare un gruppo di disponibilità di SQL Server per la scala di lettura su Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

È possibile configurare un SQL Server sempre nel gruppo di disponibilità (AG) per i carichi di lavoro di lettura scala in Linux. Esistono due tipi di architetture per estensivi. Un'architettura per la disponibilità elevata utilizza una Gestione cluster per assicurare la continuità aziendale migliorata. Questa architettura può includere anche repliche in scala di lettura. Per creare l'architettura a disponibilità elevata, vedere [configurare SQL Server gruppo di disponibilità AlwaysOn per la disponibilità elevata in Linux](sql-server-linux-availability-group-configure-ha.md). L'architettura di altri supporta solo i carichi di lavoro in scala di lettura. In questo articolo viene illustrato come creare un gruppo di disponibilità senza una Gestione cluster per i carichi di lavoro di lettura della scala. Questa architettura fornisce solo lettura scala. Non fornisce la disponibilità elevata.

>[!NOTE]
>Un gruppo di disponibilità con `CLUSTER_TYPE = NONE` può includere le repliche ospitate in piattaforme diverse del sistema operativo. Disponibilità elevata non supportato. 

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-ag"></a>Creare il gruppo di disponibilità

Creare il gruppo di disponibilità. Set `CLUSTER_TYPE = NONE`. Inoltre, impostare ogni replica con `FAILOVER_MODE = NONE`. Le applicazioni client in esecuzione analitica o reporting carichi di lavoro possono direttamente la connessione ai database secondari. È anche possibile creare un elenco di routing di sola lettura. Le connessioni alla replica primaria in avanti leggere le richieste di connessione a ognuna delle repliche secondarie della lista di distribuzione in uno schema round-robin.

Lo script di Transact-SQL seguente crea un gruppo di disponibilità denominato `ag1`. Lo script consente di configurare le repliche del gruppo di disponibilità con `SEEDING_MODE = AUTOMATIC`. Questa impostazione, SQL Server creare automaticamente il database in ciascun server secondario dopo averlo aggiunto al gruppo di disponibilità. Aggiornare lo script seguente per l'ambiente. Sostituire il `**<node1>**` e `**<node2>**` valori con i nomi delle istanze di SQL Server che ospitano le repliche. Sostituire il `**<5022>**` valore con la porta è impostata per l'endpoint. Nella replica primaria di SQL Server, eseguire lo script di Transact-SQL seguente:

```SQL
CREATE AVAILABILITY GROUP [ag1]
    WITH (CLUSTER_TYPE = NONE)
    FOR REPLICA ON
        N'**<node1>**' WITH (
            ENDPOINT_URL = N'tcp://**<node1>:**<5022>**',
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
                    SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
        N'**<node2>**' WITH ( 
            ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**', 
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
            SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            );
        
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

### <a name="join-secondary-sql-servers-to-the-ag"></a>Aggiungere server SQL secondario per il gruppo di disponibilità

Lo script Transact-SQL seguente aggiunge un server a un gruppo di disponibilità denominato `ag1`. Aggiornare lo script per l'ambiente. In ogni replica secondaria di SQL Server, eseguire lo script Transact-SQL seguente per creare un join del gruppo di disponibilità:

```SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create post](../includes/ss-linux-cluster-availability-group-create-post.md)]

Questo gruppo di disponibilità non è una configurazione a disponibilità elevata. Se è necessaria la disponibilità elevata, seguire le istruzioni in [configura un gruppo di disponibilità AlwaysOn per SQL Server in Linux](sql-server-linux-availability-group-configure-ha.md). In particolare, creare il gruppo di disponibilità con `CLUSTER_TYPE=WSFC` (in Windows) o `CLUSTER_TYPE=EXTERNAL` (in Linux). Quindi integrare con un gestore cluster utilizzando uno Windows Server failover clustering in Windows o Pacemaker in Linux.

## <a name="connect-to-read-only-secondary-replicas"></a>Connettersi a repliche secondarie di sola lettura

Esistono due modi per connettersi a repliche secondarie di sola lettura. Le applicazioni possono connettersi direttamente all'istanza di SQL Server che ospita la replica secondaria ed eseguire query sui database. È inoltre possibile utilizzare routing di sola lettura, che richiede un listener.

* [Repliche secondarie leggibili](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)
* [Routing di sola lettura](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-the-primary-replica-on-a-read-scale-availability-group"></a>Eseguire il failover la replica primaria in un gruppo di disponibilità a livello di lettura

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

## <a name="next-steps"></a>Passaggi successivi

* [Configurare un gruppo di disponibilità distribuito](..\database-engine\availability-groups\windows\distributed-availability-groups-always-on-availability-groups.md)
* [Altre informazioni sui gruppi di disponibilità](..\database-engine\availability-groups\windows\overview-of-always-on-availability-groups-sql-server.md)
* [Eseguire un failover manuale forzato](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)

