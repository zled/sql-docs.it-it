---
title: Configurare un gruppo di disponibilità SQL Server per scalabilità in lettura in Linux | Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 02/14/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: bbacb8630acf10b5c9d20c50ad40cfba3f036a7c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47677460"
---
# <a name="configure-a-sql-server-availability-group-for-read-scale-on-linux"></a>Configurare un gruppo di disponibilità SQL Server per scalabilità in lettura in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

È possibile configurare un SQL Server Always nel gruppo di disponibilità (AG) per i carichi di lavoro di scalabilità in lettura in Linux. Esistono due tipi di architetture per i gruppi di disponibilità. Un'architettura per la disponibilità elevata utilizza una gestione di cluster per assicurare la continuità aziendale migliorata. Questa architettura può includere anche le repliche con scalabilità in lettura. Per creare l'architettura a disponibilità elevata, vedere [configurare SQL Server gruppo di disponibilità AlwaysOn per la disponibilità elevata in Linux](sql-server-linux-availability-group-configure-ha.md). L'altra architettura supporta solo i carichi di lavoro di scalabilità in lettura. Questo articolo illustra come creare un gruppo di disponibilità senza una Gestione cluster per i carichi di lavoro di scalabilità in lettura. Questa architettura fornisce solo la scalabilità in lettura. Non fornisce la disponibilità elevata.

>[!NOTE]
>Un gruppo di disponibilità con `CLUSTER_TYPE = NONE` può includere repliche ospitate in diverse piattaforme del sistema operativo. Non può tuttavia supportare la disponibilità elevata. 

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-ag"></a>Creare il gruppo di disponibilità

Creare il gruppo di disponibilità. Impostare `CLUSTER_TYPE = NONE`. Impostare anche ogni replica con `FAILOVER_MODE = MANUAL`. Le applicazioni client che eseguono carichi di lavoro di analisi o esecuzione report possono connettersi direttamente ai database secondari. È anche possibile creare un elenco di routing di sola lettura. Le connessioni alla replica primaria inoltrano le richieste di connessione in lettura a ogni replica secondaria dell'elenco di routing in base a uno schema round-robin.

Lo script Transact-SQL seguente crea un gruppo di disponibilità con nome `ag1`. Lo script configura le repliche del gruppo di disponibilità con `SEEDING_MODE = AUTOMATIC`. In base a questa impostazione, SQL Server crea automaticamente il database in ciascun server secondario dopo l'aggiunta al gruppo di disponibilità. Aggiornare lo script seguente per il proprio ambiente. Sostituire i valori `<node1>` e `<node2>` con i nomi delle istanze di SQL Server che ospitano le repliche. Sostituire il valore `<5022>` con la porta impostata per l'endpoint. Nella replica primaria di SQL Server eseguire lo script Transact-SQL seguente:

```SQL
CREATE AVAILABILITY GROUP [ag1]
    WITH (CLUSTER_TYPE = NONE)
    FOR REPLICA ON
        N'<node1>' WITH (
            ENDPOINT_URL = N'tcp://<node1>:<5022>',
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
                    SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
        N'<node2>' WITH ( 
            ENDPOINT_URL = N'tcp://<node2>:<5022>', 
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
            SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            );
        
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

### <a name="join-secondary-sql-servers-to-the-ag"></a>Aggiungere server SQL secondari al gruppo di disponibilità

Lo script Transact-SQL seguente aggiunge un server al gruppo di disponibilità con nome `ag1`. Aggiornare lo script per il proprio ambiente. In ogni replica secondaria di SQL Server eseguire lo script Transact-SQL seguente per l'aggiunta al gruppo di disponibilità:

```SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create post](../includes/ss-linux-cluster-availability-group-create-post.md)]

Questo gruppo di disponibilità non è una configurazione a disponibilità elevata. Se occorre una disponibilità elevata, seguire le istruzioni in [configurare un gruppo di disponibilità AlwaysOn per SQL Server in Linux](sql-server-linux-availability-group-configure-ha.md). In particolare, creazione del gruppo di disponibilità con `CLUSTER_TYPE=WSFC` (in Windows) o `CLUSTER_TYPE=EXTERNAL` (in Linux). Quindi integrato con un gestore del cluster usando uno di Windows Server failover clustering in Windows o Pacemaker in Linux.

## <a name="connect-to-read-only-secondary-replicas"></a>Eseguire la connessione a repliche secondarie di sola lettura

Esistono due modi per eseguire la connessione a repliche secondarie di sola lettura. Le applicazioni possono connettersi direttamente all'istanza di SQL Server che ospita la replica secondaria ed eseguire query sui database. Oppure possono usare il routing di sola lettura, per il quale è necessario un listener.

* [Repliche secondarie leggibili](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)
* [Routing di sola lettura](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-the-primary-replica-on-a-read-scale-availability-group"></a>Eseguire il failover della replica primaria in un gruppo di disponibilità con scalabilità in lettura

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

## <a name="next-steps"></a>Passaggi successivi

* [Configurare gruppi di disponibilità distribuiti](..\database-engine\availability-groups\windows\distributed-availability-groups-always-on-availability-groups.md)
* [Altre informazioni sui gruppi di disponibilità](..\database-engine\availability-groups\windows\overview-of-always-on-availability-groups-sql-server.md)
* [Eseguire un failover manuale forzato](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)

