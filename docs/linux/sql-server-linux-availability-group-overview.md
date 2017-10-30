---
title: "Disponibilità gruppo AlwaysOn per SQL Server in Linux | Documenti Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 06/14/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: e37742d4-541c-4d43-9ec7-a5f9b2c0e5d1
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c5c7e602ac1beedb028072b4c82578e9948af43d
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="availability-groups-for-sql-server-on-linux"></a>Gruppi di disponibilità per SQL Server in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Un gruppo di disponibilità SQL Server Always On è a disponibilità elevata (HA), ripristino di emergenza (ripristino di emergenza) e di soluzione di scalabilità orizzontale. Fornisce disponibilità elevata per i gruppi di database in archiviazione collegata direttamente. Supporta più database secondari per integrato a disponibilità elevata e ripristino di emergenza, il rilevamento degli errori automatico, il failover rapido trasparente e il bilanciamento del carico di lettura. L'ampia gamma di funzionalità consente di ottenere una disponibilità ottimale i contratti di servizio per i carichi di lavoro.

Gruppi di disponibilità di SQL Server sono state introdotte in SQL Server 2012 e sono stati migliorati con ogni versione. Questa funzionalità è ora disponibile in Linux. Per gestire carichi di lavoro di SQL Server con requisiti di continuità aziendale rigorosi, gruppi di disponibilità eseguire su tutte le versioni [le distribuzioni del sistema operativo Linux](sql-server-linux-release-notes.md). Inoltre, tutte le funzionalità che rendono i gruppi di disponibilità di una soluzione di ripristino di emergenza a disponibilità elevata flessibile, integrata ed efficiente sono disponibili in Linux nonché. tra cui: 

- **Failover di più database** un gruppo di disponibilità supporta un ambiente di failover per un set di database utente, noti come database di disponibilità.
- **Fast il rilevamento degli errori e failover** come risorsa in un cluster a disponibilità elevata, un gruppo di disponibilità può beneficiare della business intelligence di cluster predefinite per il rilevamento immediato del failover e l'azione di failover.
- **Risorsa IP virtuale tramite il failover trasparente** client consente di utilizzare una singola stringa di connessione primaria in caso di failover. Richiede l'integrazione con un gestore cluster.
- **Più database secondari sincroni e asincroni** un gruppo di disponibilità supporta fino a otto repliche secondarie. Con repliche sincrone la replica primaria eseguirà il commit delle transazioni, che la replica primaria è in attesa di essere scritte sul disco del log delle transazioni le transazioni. La replica primaria non attende che scrive le repliche sincrone asincrona.  
- **Failover manuale o automatico** Failover una replica secondaria asincrona può essere attivato automaticamente dal cluster o su richiesta dall'amministratore del database.
- **Repliche secondarie attive disponibili per i carichi di lavoro di letture e di backup** uno o più repliche secondarie possono essere configurate per supportare l'accesso in sola lettura ai database secondari e/o per consentire i backup nei database secondari.
- **Il seeding automatico** SQL Server crea automaticamente le repliche secondarie per ogni database nel gruppo di disponibilità.
- **Routing di sola lettura** SQL Server instrada le connessioni in ingresso a un listener del gruppo di disponibilità a una replica secondaria è configurata per consentire carichi di lavoro di sola lettura. 
- **Trigger di monitoraggio e il failover di integrità di livello database** migliorato il monitoraggio a livello di database e di diagnostica. 
- **Configurazioni di ripristino di emergenza** con gruppi di disponibilità distribuiti o impostazione del gruppo di disponibilità su più subnet. 
- **Funzionalità di scalabilità di lettura** In SQL Server 2017, è possibile creare un gruppo di disponibilità con o senza disponibilità elevata per le operazioni di sola lettura di scalabilità orizzontale. 


Per ulteriori informazioni sui gruppi di disponibilità di SQL Server, vedere [gruppi di disponibilità di SQL Server Always On](http://msdn.microsoft.com/library/hh510230.aspx).

## <a name="availability-group-terminology"></a>Terminologia di gruppo di disponibilità

Un gruppo di disponibilità supporta un ambiente di failover per un set discreto di database utente, noti come database di disponibilità - che verifica il failover. Un gruppo di disponibilità supporta un set di database primari di lettura / scrittura e da una a otto set di database secondari corrispondenti. Facoltativamente, i database secondari possono essere resi disponibili per l'accesso di sola lettura e/o alcune operazioni di backup. Un gruppo di disponibilità definisce un set di due o più partner di failover, noti come repliche di disponibilità. Le repliche di disponibilità sono componenti del gruppo di disponibilità. Per informazioni dettagliate, vedere [Panoramica di sempre gruppi di disponibilità (SQL Server)](http://msdn.microsoft.com/library/ff877884.aspx).

I termini seguenti vengono descritte le parti principali di una soluzione di gruppo di disponibilità di SQL Server:

 gruppo di disponibilità  
 Contenitore per un set di database, i *database di disponibilità*, su cui si verifica il failover.  
  
 database di disponibilità  
 Database che appartiene a un gruppo di disponibilità. Per ogni database di disponibilità, il gruppo di disponibilità gestisce una sola copia di lettura e scrittura (il *database primario*) e da una a otto copie di sola lettura (*database secondari*).  
  
 database primario  
 Copia di lettura e scrittura di un database di disponibilità.  
  
 database secondario  
 Copia di sola lettura di un database di disponibilità.  
  
 replica di disponibilità  
 Creazione di un'istanza di un gruppo di disponibilità ospitato da un'istanza specifica di SQL Server e che mantiene una copia locale di ogni database di disponibilità che appartiene al gruppo di disponibilità. Sono disponibili due tipi di replica di disponibilità: una *replica primaria* e da una a otto *repliche secondarie*.  
  
 replica primaria  
 Replica di disponibilità che rende disponibili i database primari per le connessioni in lettura e scrittura dai client e invia i record del log delle transazioni per ogni database primario a ogni replica secondaria.  
  
 replica secondaria  
 Replica di disponibilità che mantiene una copia secondaria di ogni database di disponibilità e che rappresenta la destinazione potenziale del failover per il gruppo di disponibilità. Facoltativamente, una replica secondaria può supportare l'accesso in sola lettura ai database secondari creando backup sui database secondari.  
  
 listener del gruppo di disponibilità  
 Nome server a cui i client possono connettersi per accedere a un database in una replica primaria o secondaria di un gruppo di disponibilità. I listener del gruppo di disponibilità indirizzano le connessioni in ingresso alla replica primaria o a una replica secondaria in sola lettura.  


## <a name="new-in-sql-server-2017-for-availability-groups"></a>Novità di SQL Server 2017 per gruppi di disponibilità

SQL Server 2017 introduce nuove funzionalità per i gruppi di disponibilità.

**CLUSTER_TYPE** utilizzare con `CREATE AVAILABILITY GROUP`. Identifica il tipo di Gestione cluster di server che gestisce un gruppo di disponibilità. Può essere uno dei seguenti tipi:

   - **WSFC** Winows cluster di failover di server. In Windows, è il valore predefinito per CLUSTER_TYPE.
   - **ESTERNI** una gestione di cluster che è ad esempio, non Windows server failover cluster - in Linux con Pacemaker.
   - **Nessuna** alcun gestore cluster. Utilizzato per un gruppo di disponibilità a livello di lettura.

Per ulteriori informazioni su queste opzioni, vedere [CREATE AVAILABILITY GROUP](http://msdn.microsoft.com/library/ff878399.aspx) o [ALTER AVAILABILITY GROUP](http://msdn.microsoft.com/library/ff878601.aspx).

**Viene eseguito il commit di garanzia su repliche secondarie sincrone**

Use `required_synchronized_secondaries_to_commit`with `CREATE AVAILABILITY GROUP` or `ALTER AVAILABILITY GROUP`. Quando `required_synchronized_secondaries_to_commit` è impostata su un valore maggiore di 0, le transazioni nella replica primaria database attenderà fino a quando non viene eseguito il commit della transazione al numero specificato di **database secondario sincrono** log delle transazioni del database di replica. Se sufficiente repliche secondarie sincrone non sono online, tutte le connessioni alla replica primaria verranno rifiutate fino a quando la comunicazione con repliche secondarie sufficiente riprendere.

**Gruppi di disponibilità a livello di lettura**

Creare un gruppo di disponibilità senza un cluster per supportare i carichi di lavoro di lettura della scala. Vedere [gruppi di disponibilità lettura scala](../database-engine/availability-groups/windows/read-scale-availability-groups.md).

## <a name="next-steps"></a>Passaggi successivi

[Configurare il gruppo di disponibilità per SQL Server in Linux](sql-server-linux-availability-group-configure-ha.md)

[Configurare il gruppo di disponibilità a livello di lettura per SQL Server in Linux](sql-server-linux-availability-group-configure-rs.md)

[Aggiungere il gruppo di disponibilità risorse Cluster su RHEL](sql-server-linux-availability-group-cluster-rhel.md)

[Aggiungere il gruppo di disponibilità risorsa Cluster in SLES](sql-server-linux-availability-group-cluster-sles.md)

[Aggiungere il gruppo di disponibilità risorsa Cluster in Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

