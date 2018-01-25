---
title: Soft-NUMA (SQL Server) | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NUMA
- soft-NUMA
helpviewer_keywords:
- NUMA
- non-uniform memory access
- soft-NUMA
ms.assetid: 1af22188-e08b-4c80-a27e-4ae6ed9ff969
caps.latest.revision: "53"
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 41d4c5d62d227f6ba5a89fcacb24e22ae27905db
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="soft-numa-sql-server"></a>Soft-NUMA (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  I processori moderni sono costituiti da multipli a molti core per socket. Ogni socket è solitamente rappresentato come un unico nodo NUMA. Il motore di database di SQL Server suddivide le varie strutture interne e i thread del servizio per nodo NUMA.  In caso di processori che contengono da 10 a più core per socket, l'uso di soft-NUMA (software non-uniform memory access) per suddividere i nodi NUMA hardware aumenta generalmente la scalabilità e le prestazioni. Prima di SQL Server 2014 SP2, l'architettura soft-NUMA era configurata per computer anziché per istanza. Era anche necessario modificare il registro per aggiungere una maschera di affinità alla configurazione del nodo.  Grazie a SQL Server 2014 SP2 e SQL Server 2016, l'architettura soft-NUMA viene configurata automaticamente a livello di istanza database all'avvio del servizio SQL Server.  
  
> [!NOTE]  
>  L'architettura soft-NUMA consente di aggiungere processori a caldo.  
  
## <a name="automatic-soft-numa"></a>Architettura soft-NUMA automatica  
 Ogni volta che il server del motore di database rileva più di 8 core fisiche per ogni nodo o socket NUMA all'avvio, per impostazione predefinita di SQL Server 2016 vengono creati automaticamente nodi soft-NUMA. Il conteggio delle core fisiche in un nodo non distingue tra core di processori fisici e con hyperthreading.  Quando il numero di core fisiche rilevato è superiore a 8 per ogni socket, il motore di database crea nodi soft-NUMA che possono idealmente contenere 8 core. Il numero delle core logiche per nodo può essere tuttavia ridotto a 5 o incrementato a 9. La dimensione del nodo hardware può essere limitata da una maschera di affinità di CPU. Vedere   
            [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md). Il numero di nodi NUMA non supererà mai il numero massimo di nodi NUMA supportati.  
  
 È possibile disabilitare o riabilitare soft-NUMA tramite l'istruzione [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md) con l'argomento SET SOFTNUMA. Per rendere effettiva la modifica del valore di questa impostazione è necessario riavviare il motore di database.  
  
 La figura seguente rappresenta il log degli errori di SQL Server contenente le informazioni riguardanti soft-NUMA nel caso in cui SQL Server rilevi nodi NUMA hardware con più di 8 core fisiche in ogni nodo o socket.  


``2016-11-14 13:39:43.17 Server      SQL Server detected 2 sockets with 12 cores per socket and 24 logical processors per socket, 48 total logical processors; using 48 logical processors based on SQL Server licensing. This is an informational message; no user action is required.``  
  **``2016-11-14 13:39:43.35 Server      Automatic soft-NUMA was enabled because SQL Server has detected hardware NUMA nodes with greater than 8 physical cores.``**  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 0: CPU mask: 0x0000000000555555:0 Active CPU mask: 0x0000000000555555:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 1: CPU mask: 0x0000000000aaaaaa:0 Active CPU mask: 0x0000000000aaaaaa:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 2: CPU mask: 0x0000555555000000:0 Active CPU mask: 0x0000555555000000:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 3: CPU mask: 0x0000aaaaaa000000:0 Active CPU mask: 0x0000aaaaaa000000:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``

  
## <a name="manual-soft-numa"></a>Architettura soft-NUMA manuale  
 Per configurare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] manualmente per l'uso di soft-NUMA, è necessario disabilitare l'architettura soft_NUMA automatica e modificare il registro per aggiungere una maschera di affinità alla configurazione del nodo. Se si usa questo metodo, la maschera soft-NUMA può essere definita come voce del Registro di sistema binaria, DWORD (esadecimale o decimale) o QWORD (esadecimale o decimale). Per configurare un numero maggiore rispetto alle prime 32 CPU, utilizzare i valori del Registro di sistema QWORD o BINARY. I valori QWORD non possono essere usati nelle versioni precedenti a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Dopo aver modificato il Registro di sistema, è necessario riavviare [!INCLUDE[ssDE](../../includes/ssde-md.md)] per rendere effettiva la configurazione dell'architettura soft-NUMA.  
  
> [!TIP]
> Le CPU sono numerate partendo da 0.  

> [!WARNING]
> [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
 Si consideri l'esempio seguente. In un computer con otto CPU non è disponibile NUMA hardware. Vengono configurati tre nodi soft-NUMA.   
            L'istanza A del[!INCLUDE[ssDE](../../includes/ssde-md.md)] è configurata per utilizzare le CPU da 0 a 3. Una seconda istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] viene installata e configurata per utilizzare le CPU da 4 a 7. Questo esempio può essere rappresentato visivamente come segue:  
  
 `CPUs          0  1  2  3  4  5  6  7`  
  
 `Soft-NUMA   <-N0--><-N1-><----N2---->`  
  
 `SQL Server  <instance A ><instance B>`  
  
 Nell'istanza A che presenta un I/O significativo sono disponibili ora due thread di I/O e un thread Lazywriter mentre nell'istanza B in cui vengono eseguite operazioni con utilizzo elevato del processore sono disponibili solo un thread di I/O e un thread Lazywriter. È possibile assegnare alle istanze quantità di memoria diverse ma, a differenza di quanto avviene con hardware NUMA, entrambe le istanze ricevono memoria dallo stesso blocco di memoria del sistema operativo e non è presente affinità tra memoria e processore.  
  
 Il thread Lazywriter è correlato alla vista del sistema operativo SQL dei nodi di memoria NUMA fisici. Pertanto, qualsiasi elemento venga presentato come nodo NUMA fisico da parte dell'hardware corrisponderà al numero di thread Lazywriter creati. Per ulteriori informazioni, vedere   
            [How It Works: Soft NUMA, I/O Completion Thread, Lazy Writer Workers and Memory Nodes](http://blogs.msdn.com/b/psssql/archive/2010/04/02/how-it-works-soft-numa-i-o-completion-thread-lazy-writer-workers-and-memory-nodes.aspx)(Funzionamento: Soft-NUMA, thread di completamento di I/O, thread di lavoro Lazywriter e nodi di memoria).  
  
> [!NOTE]
> Le chiavi del Registro di sistema di **Soft-NUMA** non vengono copiate quando si aggiorna un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="set-the-cpu-affinity-mask"></a>Impostazione della maschera di affinità della CPU  
 Eseguire l'istruzione seguente nell'istanza A per configurarla per l'utilizzo delle CPU 0, 1, 2 e 3 impostando la maschera di affinità della CPU:  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY CPU=0 TO 3;  
```  
  
 Eseguire l'istruzione seguente nell'istanza B per configurarla per l'utilizzo delle CPU 4, 5, 6 e 7 impostando la maschera di affinità della CPU:  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY CPU=4 TO 7;  
```  
  
### <a name="map-soft-numa-nodes-to-cpus"></a>Mapping dei nodi soft-NUMA alle CPU  
 Utilizzando l'Editor del Registro di sistema (regedit.exe), aggiungere le chiavi del Registro di sistema seguenti per eseguire il mapping del nodo soft-NUMA 0 alle CPU 0 e 1, del nodo soft-NUMA 1 alle CPU 2 e 3 e del nodo soft-NUMA 2 alle CPU 4, 5, 6 e 7.  
  
> [!TIP]
> Per specificare le CPU da 60 a 63, usare un valore QWORD di F000000000000000 o un valore BINARY di 1111000000000000000000000000000000000000000000000000000000000000.  
  
 Nell'esempio seguente si presuppone di avere un server DL580 G9 con 18 core per socket (in 4 socket) e ciascun socket si trova nel proprio gruppo K. La configurazione soft-NUMA creata dovrebbe essere simile alla seguente: 6 core per nodo, 3 nodi per gruppo, 4 gruppi.  
  
|Esempio per un server [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] con più gruppi K|Tipo|Nome del valore|Dati del valore|  
|-----------------------------------------------------------------------------------------------------------------|----------|----------------|----------------|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node0|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node0|DWORD|Gruppo|0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node1|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node1|DWORD|Gruppo|0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node2|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node2|DWORD|Gruppo|0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node3|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node3|DWORD|Gruppo|1|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node4|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node4|DWORD|Gruppo|1|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node5|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node5|DWORD|Gruppo|1|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node6|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node6|DWORD|Gruppo|2|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node7|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node7|DWORD|Gruppo|2|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node8|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node8|DWORD|Gruppo|2|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node9|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node9|DWORD|Gruppo|3|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node10|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node10|DWORD|Gruppo|3|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node11|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node11|DWORD|Gruppo|3|  
  
## <a name="metadata"></a>Metadati  
 È possibile usare le viste a gestione dinamica seguenti per visualizzare lo stato e la configurazione correnti di soft_NUMA.  
  
-   [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md): visualizza il valore corrente (0 o 1) per SOFTNUMA  
  
-   [sys.dm_os_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-nodes-transact-sql.md): nella colonna node_state_desc di ogni nodo NUMA è indicato se il nodo è stato creato da soft-NUMA o meno.  
  
-   [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md): le colonne softnuma e softnuma_desc contengono i valori di configurazione.  
  
> [!NOTE]
> Sebbene sia possibile visualizzare il valore corrente per l'uso dell'architettura soft-NUMA automatica tramite [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md), non è possibile modificarne il valore usando **sp_configure**. È necessario usare l'istruzione [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md) con l'argomento SET SOFTNUMA.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il mapping delle porte TCP/IP ai nodi NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/map-tcp-ip-ports-to-numa-nodes-sql-server.md)   
 [Opzione di configurazione del server affinity mask](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)   
 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md)  
  
  

