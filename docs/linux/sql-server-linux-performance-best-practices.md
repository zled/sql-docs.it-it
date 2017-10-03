---
title: Procedure consigliate per SQL Server in Linux | Documenti Microsoft
description: Questo argomento fornisce linee guida e procedure consigliate per l'esecuzione di SQL Server 2017 in Linux.
author: rgward
ms.author: bobward
manager: jhubbard
ms.date: 09/14/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: 18d40800ee74783b0ce3df4d9d4e0458fbb72ebb
ms.contentlocale: it-it
ms.lasthandoff: 10/02/2017

---

# <a name="performance-best-practices-and-configuration-guidelines-for-sql-server-2017-on-linux"></a>Procedure consigliate e linee guida di configurazione per SQL Server 2017 su Linux

In questo argomento fornisce le procedure consigliate e indicazioni per ottimizzare le prestazioni per applicazioni di database che si connettono a SQL Server in Linux. Questi suggerimenti sono specifici per l'esecuzione nella piattaforma Linux. Tutti i consigli per SQL Server normali, ad esempio la progettazione degli indici, vengono mantenuti.

Le linee guida seguenti sono inclusi suggerimenti per la configurazione di SQL Server e il sistema operativo Linux.

## <a name="sql-server-configuration"></a>Configurazione di SQL Server

È consigliabile eseguire le seguenti attività di configurazione dopo l'installazione di SQL Server in Linux per ottenere prestazioni ottimali per l'applicazione.

### <a name="best-practices"></a>Procedure consigliate

- **Utilizzare l'AFFINITÀ di processo per nodo e/o CPU**

   È consigliabile utilizzare `ALTER SERVER CONFIGURATION` impostare `PROCESS AFFINITY` per tutti i **NUMANODEs** e/o CPU in uso per SQL Server (che è in genere per tutti i nodi e CPU) in un sistema operativo Linux. Affinità processori consente di mantenere il comportamento di Linux e la pianificazione di SQL efficiente. Utilizzo di **NUMANODE** opzione è il metodo più semplice. Si noti che è necessario utilizzare **AFFINITÀ di processo** anche se si dispone di un singolo nodo NUMA nel computer in uso.  Vedere il [ALTER SERVER CONFIGURATION](../t-sql/statements/alter-server-configuration-transact-sql.md) documentazione per maggiori dettagli su come impostare **AFFINITÀ di processo**.

- **Configurare più file di dati di tempdb**

   Poiché SQL Server in Linux installazione non offre un'opzione per configurare più file di tempdb, è consigliabile prendere in considerazione la creazione di file di dati tempdb più dopo l'installazione. Per ulteriori informazioni, vedere le istruzioni fornite nell'articolo, [indicazioni per ridurre la contesa per l'allocazione nel database tempdb di SQL Server](https://support.microsoft.com/en-us/help/2154845/recommendations-to-reduce-allocation-contention-in-sql-server-tempdb-d).

### <a name="advanced-configuration"></a>Configurazione avanzata

Le raccomandazioni seguenti sono impostazioni di configurazione facoltative che è possibile scegliere di eseguire dopo l'installazione di SQL Server in Linux. Queste scelte sono basate sui requisiti del carico di lavoro e alla configurazione del sistema operativo Linux.

- **Impostare un limite di memoria con mssql conf**

   Per verificare che sia disponibile memoria fisica sufficiente per il sistema operativo Linux, il processo di SQL Server utilizza solo l'80% della RAM fisica per impostazione predefinita. Per alcuni sistemi quali grandi quantità di RAM fisica, 20% potrebbe essere un numero significativo. Ad esempio, in un sistema con 1 TB di RAM, l'impostazione predefinita lascia circa 200 GB di RAM inutilizzati. In questo caso, è possibile configurare il limite di memoria su un valore superiore. Vedere la documentazione sul **mssql conf** strumento e [memory.memorylimitmb](sql-server-linux-configure-mssql-conf.md#memorylimit) impostazione che controlla la memoria visibile a SQL Server (in unità di MB).

   Quando si modifica questa impostazione, prestare attenzione a non impostare un valore troppo elevato. Se non si lascia memoria sufficiente, si potrebbero verificare problemi con il sistema operativo Linux e altre applicazioni di Linux.

## <a name="linux-os-configuration"></a>Configurazione del sistema operativo Linux

È consigliabile utilizzare le seguenti impostazioni di configurazione di sistema operativo Linux per sfruttare le migliori prestazioni per un'installazione di SQL Server.

### <a name="kernel-settings-for-high-performance"></a>Impostazioni del kernel per prestazioni elevate

Si tratta di consigliato prestazioni correlati ad alta le impostazioni di sistema operativo Linux e velocità effettiva per un'installazione di SQL Server. Vedere la documentazione del sistema operativo Linux per il processo configurare queste impostazioni.



> [!Note]
> Per gli utenti di Red Hat Enterprise Linux (RHEL), il profilo delle prestazioni di velocità effettiva verrà configurare queste impostazioni automaticamente (tranne gli stati C).

Nella tabella seguente vengono forniti consigli per le impostazioni della CPU:

| Impostazione | Valore | Ulteriori informazioni |
|---|---|---|
| Governor frequenza della CPU | prestazioni | Vedere il **cpupower** comando |
| ENERGY_PERF_BIAS | prestazioni | Vedere il **x86_energy_perf_policy** comando |
| min_perf_pct | 100 | Vedere la documentazione di intel p-stato |
| Stati C | Solo C1 | Vedere la documentazione di Linux o sistema su come assicurare che gli stati C sono impostato su C1 solo |

Nella tabella seguente vengono forniti consigli per le impostazioni del disco:

| Impostazione | Valore | Ulteriori informazioni |
|---|---|---|
| Read-ahead disco | 4096 | Vedere il **blockdev** comando |
| impostazioni sysctl | kernel.sched_min_granularity_ns = 10000000<br/>kernel.sched_wakeup_granularity_ns = 15000000<br/>VM.dirty_ratio = 40<br/>VM.dirty_background_ratio = 10<br/>VM.swappiness=10 | Vedere il **sysctl** comando |

### <a name="kernel-setting-auto-numa-balancing-for-multi-node-numa-systems"></a>Kernel impostazione automatica numa bilanciamento del carico per i sistemi a più nodi NUMA

Se si installa SQL Server in un nodo più **NUMA** sistemi, le operazioni seguenti **kernel.numa_balancing** kernel è abilitata per impostazione predefinita. Per consentire a SQL Server su cui operare al massimo un **NUMA** sistema, disabilita automaticamente numa bilanciamento del carico nei sistemi a più nodi NUMA:

```bash
sysctl -w kernel.numa_balancing=0
```

### <a name="kernel-settings-for-virtual-address-space"></a>Impostazioni del kernel per spazio degli indirizzi virtuali

L'impostazione predefinita **vm.max_map_count** potrebbe non essere sufficientemente elevato per un'installazione di SQL Server (ovvero 65536). Modificare questo valore (che è un limite superiore) a 256 KB.

```bash
sysctl -w vm.max_map_count 262144
```

### <a name="disable-last-accessed-datetime-on-file-systems-for-sql-server-data-and-log-files"></a>Disabilitare la data/ora dell'ultimo accesso nei sistemi di file per i file di dati e di log di SQL Server

Utilizzare il **noatime** attributo con il file system che viene utilizzato per archiviare i dati di SQL Server e i file di log. Consultare la documentazione di Linux su come impostare questo attributo.

### <a name="leave-transparent-huge-pages-thp-enabled"></a>Lasciare trasparente enorme pagine (THP) abilitato

La maggior parte delle installazioni di Linux devono disporre questa opzione per impostazione predefinita. È consigliabile per un'esperienza più coerenza delle prestazioni mantenere abilitata questa opzione di configurazione.

### <a name="swapfile"></a>file di scambio

Assicurarsi di disporre di un file di scambio configurato correttamente per evitare eventuali problemi di memoria insufficiente. Consultare la documentazione di Linux per informazioni su come creare e impostare correttamente le dimensioni di un file di scambio.

### <a name="virtual-machines-and-dynamic-memory"></a>Macchine virtuali e la memoria dinamica

Se si esegue SQL Server in Linux in una macchina virtuale, assicurarsi di che selezionare le opzioni per risolvere la quantità di memoria riservata per la macchina virtuale. Non usare funzionalità come la memoria dinamica di Hyper-V.

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni sulle funzionalità di SQL Server che consentono di migliorare le prestazioni, vedere [Introduzione a caratteristiche di prestazioni](sql-server-linux-performance-get-started.md).

Per ulteriori informazioni su SQL Server in Linux, vedere [Panoramica di SQL Server in Linux](sql-server-linux-overview.md).

