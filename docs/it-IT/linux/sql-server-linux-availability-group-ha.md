---
title: SQL Server Always On modelli distribuzione gruppo di disponibilità | Documenti Microsoft
ms.custom: sql-linux
ms.date: 10/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
caps.latest.revision: 34
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: be101608971d9bb40def9f8f1df22bc867c4dd0d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="high-availability-and-data-protection-for-availability-group-configurations"></a>Elevata disponibilità e protezione dei dati per le configurazioni di gruppo di disponibilità

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questo articolo è configurazioni di distribuzione supportate per i gruppi di disponibilità di SQL Server Always On su server Linux. Un gruppo di disponibilità supporta la disponibilità elevata e la protezione dei dati. Il rilevamento degli errori automatico, failover automatico e la riconnessione dopo il failover trasparente garantire un'elevata disponibilità. Le repliche sincronizzate forniscono la protezione dei dati. 

In un Windows Server Failover Cluster (WSFC), una configurazione comune per la disponibilità elevata utilizza due repliche sincrone e una terzo server o la condivisione file per fornire quorum. La condivisione di file di controllo convalida la configurazione del gruppo di disponibilità - stato di sincronizzazione e il ruolo della replica, ad esempio. Questa configurazione assicura che la replica secondaria scelta come destinazione del failover è disponibili dati più recenti le modifiche alla configurazione gruppo di disponibilità. 

Il cluster WSFC Sincronizza i metadati di configurazione per l'arbitraggio failover tra le repliche del gruppo di disponibilità e la condivisione di file di controllo. Quando un gruppo di disponibilità non è presente su un cluster WSFC, le istanze di SQL Server archiviano i metadati di configurazione nel database master.

Ad esempio, dispone di un gruppo di disponibilità in un cluster Linux `CLUSTER_TYPE = EXTERNAL`. Non vi è alcun WSFC in corso il failover. In questo caso i metadati di configurazione gestito e gestito da istanze di SQL Server. Poiché non esiste alcun server di controllo del cluster, una terza istanza di SQL Server è necessario per archiviare i metadati di stato di configurazione. Tutte e tre le istanze di SQL Server, insieme, forniscono metadati distribuiti archiviazione per il cluster. 

Gestione cluster di è possibile eseguire una query di istanze di SQL Server nel gruppo di disponibilità e orchestrare il failover per mantenere la disponibilità elevata. In un cluster Linux, Pacemaker è il gestore del cluster. 

SQL Server 2017 CU 1 abilita la disponibilità elevata per un gruppo di disponibilità con `CLUSTER_TYPE = EXTERNAL` per una replica di sola configurazione più di due repliche sincrone. L'unica replica configurazione può essere ospitato in qualsiasi edizione di SQL Server 2017 CU1 o versioni successive, incluso SQL Server Express edition. L'unica replica configurazione mantiene le informazioni di configurazione relative al gruppo di disponibilità nel database master, ma non contiene i database utente nel gruppo di disponibilità. 

## <a name="how-the-configuration-affects-default-resource-settings"></a>Le impostazioni predefinite di influenza la configurazione

SQL Server 2017 introduce il `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` impostazione della risorsa del cluster. Questa impostazione garantisce il numero specificato di repliche secondarie scrittura i dati di transazione per l'accesso prima che la replica primaria esegue il commit di ogni transazione. Quando si utilizza una gestione di cluster esterne, questa impostazione influisce su un'elevata disponibilità e la protezione dei dati. Il valore predefinito per l'impostazione dipende dall'architettura al momento che della creazione della risorsa cluster. Quando si installa l'agente di risorse di SQL Server - `mssql-server-ha` - e creare una risorsa cluster del gruppo di disponibilità, la gestione di cluster rileva la disponibilità del gruppo configurazione e set `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` di conseguenza. 

Se è supportata dalla configurazione, il parametro dell'agente risorsa `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` è impostata sul valore che fornisce la protezione dati e la disponibilità elevata. Per ulteriori informazioni, vedere [comprendere SQL Server agent di risorsa per pacemaker](#pacemakerNotify).

Le sezioni seguenti illustrano il comportamento predefinito per la risorsa cluster. 

Scegliere una struttura di gruppo di disponibilità per soddisfare specifici requisiti aziendali per la disponibilità elevata, protezione dei dati e la scalabilità di lettura.

Le configurazioni seguenti vengono descritti i modelli di progettazione di gruppo di disponibilità e le funzionalità di ogni modello. Questi modelli di progettazione si applicano ai gruppi di disponibilità con `CLUSTER_TYPE = EXTERNAL` per soluzioni a disponibilità elevata. 

- **Tre repliche sincrone**
- **Due repliche sincrone**
- **Una replica di sola configurazione e di due repliche sincrone**

<a name="threeSynch"></a>

## <a name="three-synchronous-replicas"></a>Tre repliche sincrone

Questa configurazione è costituita da tre repliche sincrone. Per impostazione predefinita, fornisce ad alta disponibilità e protezione dei dati. Inoltre, fornisce scalabilità di lettura.

![Tre repliche][3]

Scala di lettura, la disponibilità elevata e la protezione dei dati, può fornire un gruppo di disponibilità con tre repliche sincrone. Nella tabella seguente descrive il comportamento di disponibilità. 

| |scala di lettura|Disponibilità elevata & </br> protezione dei dati | Protezione dei dati
|:---|---|---|---
|`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT=`|0 |1<sup>*</sup>|2
|Interruzione primaria | Failover manuale. Potrebbe verificarsi la perdita di dati. Nuovo database primario è R / w. |Failover automatico. Nuovo database primario è R / w. |Failover automatico. Nuovo database primario non è disponibile per le transazioni utente fino a quando non primario precedente consente di recuperare e join di gruppo di disponibilità secondaria. 
|Interruzione di una replica secondaria  | Primario è R / w. Nessun failover automatico se primario ha esito negativo. |Primario è R / w. Nessun failover automatico se primario non riesce. | Database primario non è disponibile per le transazioni utente. 
<sup>*</sup> Impostazione predefinita

<a name="twoSynch"></a>

## <a name="two-synchronous-replicas"></a>Due repliche sincrone

Questa configurazione consente la protezione dei dati. Come le altre configurazioni gruppo disponibilità, è possibile attivare in scala di lettura. La configurazione di due repliche sincrone non fornisce la disponibilità elevata automatica. 

![Due repliche sincrone][1]

Un gruppo di disponibilità con due repliche sincrone offre una protezione a livello di lettura e di dati. Nella tabella seguente descrive il comportamento di disponibilità. 

| |scala di lettura |Protezione dei dati
|:---|---|---
|`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT=`|0 <sup>*</sup>|1
|Interruzione primaria | Failover manuale. Potrebbe verificarsi la perdita di dati. Nuovo database primario è R / w.| Failover automatico. Nuovo database primario non è disponibile per le transazioni utente fino a quando non primario precedente consente di recuperare e join di gruppo di disponibilità secondaria.
|Interruzione di una replica secondaria  |Primario è di lettura/scrittura, esecuzione senza perdita di dati. |Database primario non è disponibile per le transazioni utente finché non viene ripristinato secondario.
<sup>*</sup> Impostazione predefinita

>[!NOTE]
>Lo scenario precedente è il comportamento prima di SQL Server 2017 aggiornamento Cumulativo 1. 

<a name = "configOnly"></a>

## <a name="two-synchronous-replicas-and-a-configuration-only-replica"></a>Una replica di sola configurazione e di due repliche sincrone

Un gruppo di disponibilità con repliche sincrone due (o più) e una replica di sola configurazione fornisce la protezione dei dati e può anche fornire disponibilità elevata. Nel diagramma seguente rappresenta questa architettura:

![Gruppo di disponibilità solo di configurazione][2]

1. Replica sincrona dei dati utente per la replica secondaria. Include inoltre i metadati di configurazione gruppo di disponibilità.
2. Replica sincrona di metadati di configurazione gruppo di disponibilità. Non include dati utente.

Nel diagramma gruppo di disponibilità, una replica primaria inserisce i dati di configurazione per la replica secondaria sia l'unica replica di configurazione. La replica secondaria inoltre riceve i dati utente. L'unica replica configurazione non riceve dati utente. La replica secondaria è in modalità sincrona di disponibilità. L'unica replica configurazione non contiene i database nel gruppo di disponibilità - solo i metadati relativi al gruppo di disponibilità. L'unica replica configurazione dati di configurazione viene eseguito il commit in modo sincrono.

>[!NOTE]
>Un gruppo di availabilility con la replica solo configurazione è nuovo per SQL Server 2017 CU1. Tutte le istanze di SQL Server nel gruppo di disponibilità devono essere SQL Server 2017 CU1 o versione successiva. 

Il valore predefinito per `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` è 0. Nella tabella seguente descrive il comportamento di disponibilità. 

| |Disponibilità elevata & </br> protezione dei dati | Protezione dei dati
|:---|---|---
|`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT=`|0 <sup>*</sup>|1
|Interruzione primaria | Failover automatico. Nuovo database primario è R / w. | Failover automatico. Nuovo database primario non è disponibile per le transazioni utente. 
|Interruzione di replica secondaria | Filegroup primario è L/S, in esecuzione esposto alla perdita di dati (se primario ha esito negativo e non può essere ripristinato). Nessun failover automatico se primario non riesce. | Database primario non è disponibile per le transazioni utente. Nessuna replica per eseguire il failover se primario non riesce. 
|Interruzione di replica sola configurazione | Primario è R / w. Nessun failover automatico se primario non riesce. | Primario è R / w. Nessun failover automatico se primario non riesce. 
|Database secondario sincrono + configurazione solo un'interruzione di replica| Database primario non è disponibile per le transazioni utente. Nessun failover automatico. | Database primario non è disponibile per le transazioni utente. Per eseguire il failover se non vi sono repliche primarie non riuscirà. 
<sup>*</sup> Impostazione predefinita

>[!NOTE]
>L'istanza di SQL Server che ospita la replica solo configurazione può ospitare anche altri database. Può anche fare parte di un database di configurazione solo per più di un gruppo di disponibilità. 

## <a name="requirements"></a>Requisiti

* Tutte le repliche di un gruppo di disponibilità con una replica di sola configurazione devono essere SQL Server 2017 CU 1 o versione successiva.
* Qualsiasi edizione di SQL Server può ospitare una replica di sola configurazione, incluso SQL Server Express. 
* Il gruppo di disponibilità richiede almeno una replica secondaria, oltre alla replica primaria.
* Il numero massimo di repliche per ogni istanza di SQL Server non vengono contano sole repliche di configurazione. SQL Server standard edition consente fino a tre repliche, SQL Server Enterprise Edition consente un massimo di 9.

## <a name="considerations"></a>Considerazioni

* Replica di sola non più di una configurazione per ogni gruppo di disponibilità. 
* Una replica di sola configurazione non può essere una replica primaria.
* È possibile modificare la modalità di disponibilità di una replica di sola configurazione. Per passare da una replica di sola configurazione a una replica secondaria sincrona o asincrona, rimuovere la replica solo di configurazione e aggiungere una replica secondaria con la modalità di disponibilità richiesto. 
* Una replica di sola configurazione è sincrona con i metadati del gruppo di disponibilità. Non sono presenti dati utente. 
* Un gruppo di disponibilità con una replica primaria e replica solo una configurazione, ma nessuna replica secondaria non è valido. 
* È possibile creare un gruppo di disponibilità in un'istanza di SQL Server Express edition. 

<a name="pacemakerNotify"></a>

## <a name="understand-sql-server-resource-agent-for-pacemaker"></a>Comprendere l'agente di risorse di SQL Server per pacemaker

SQL Server 2017 CTP 1.4 aggiunto `sequence_number` a `sys.availability_groups` per consentire il Pacemaker identificare secondario di aggiornamento delle repliche sono con la replica primaria. `sequence_number` è un valore BIGINT a incremento progressivo costante che rappresenta di aggiornamento di replica del gruppo di disponibilità locale. Gli aggiornamenti pacemaker il `sequence_number` con ogni modifica della configurazione gruppo di disponibilità. Esempi di modifiche di configurazione includono il failover, aggiunta di replica o la rimozione. Il numero viene aggiornato nel server primario, quindi replicato a repliche secondarie. In questo modo una replica secondaria con configurazione aggiornata ha lo stesso numero di sequenza del database primario. 

Quando il Pacemaker decide di alzare di livello una replica primaria, prima invia un *pre-alzare di livello* notifica a tutte le repliche. Le repliche di restituiscono il numero di sequenza. Successivamente, quando Pacemaker esegue effettivamente un tentativo di promuovere una replica primaria, la replica solo promuove se stesso se il numero di sequenza è il più elevato di tutti i numeri di sequenza. Se il proprio numero di sequenza non corrisponde il numero di sequenza più alto, la replica rifiuta l'operazione Alza di livello. In questo modo, solo la replica con il numero di sequenza più alto può essere alzata di livello e impostata come primaria e non si verifica alcuna perdita dei dati. 

Questo processo richiede almeno una replica è disponibile per l'innalzamento di livello con lo stesso numero di sequenza come database primario precedente. Il set di agente di risorse Pacemaker `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` in modo che almeno una replica secondaria asincrona è aggiornato e disponibile per essere la destinazione di un failover automatico per impostazione predefinita. Con ogni azione di monitoraggio, il valore di `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` viene calcolato (e aggiornati se necessario). Il `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` valore è 'numero di repliche sincrone' diviso 2. In fase di failover, è necessario l'agente di risorsa (`total number of replicas`  -  `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` repliche) per rispondere al pre-promuovere notifica. La replica con il più elevato `sequence_number` viene promossa a primaria. 

Ad esempio, un gruppo di disponibilità con tre repliche sincrone - una replica primaria e due repliche secondarie sincrone.

- `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` è 1; (3 / 2 -> 1).

- Il numero di repliche per rispondere ai pre-fini dell'azione di richiesto è 2. (3 - 1 = 2). 

In questo scenario, è necessario rispondere per il failover deve essere attivata due repliche. Per il failover automatico ha esito positivo dopo un'interruzione della replica primaria, sia nelle repliche secondarie desidera essere aggiornate e rispondere alla pre-promuovere notifica. Se sono online e sincrona, hanno lo stesso numero di sequenza. Il gruppo di disponibilità Alza di livello uno di essi. Se solo una delle repliche secondarie risponde a di alzare di pre-livello azione, l'agente di risorsa non può garantire che il database secondario che ha risposto ha sequence_number il più elevato, e non viene attivato un failover.

>[!IMPORTANT]
>Quando `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` è 0 esiste il rischio di perdita dei dati. Durante un'interruzione di replica primaria, l'agente di risorsa non verrà automaticamente avviato un failover. È possibile attendere per il sito primario ripristinare o eseguire manualmente il failover utilizzando `FORCE_FAILOVER_ALLOW_DATA_LOSS`.

È possibile scegliere di ignorare il comportamento predefinito e impedire l'impostazione della risorsa del gruppo di disponibilità `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` automaticamente.

Lo script seguente imposta `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` su 0 in un gruppo di disponibilità denominato `<**ag1**>`. Prima di eseguire lo script, sostituire `<**ag1**>` con il nome del gruppo di disponibilità.

```bash
sudo pcs resource update <**ag1**> required_synchronized_secondaries_to_commit=0
```

Per ripristinare il valore predefinito, in base alla configurazione gruppo di disponibilità eseguire:

```bash
sudo pcs resource update <**ag1**> required_synchronized_secondaries_to_commit=
```

>[!NOTE]
>Quando si eseguono i comandi precedenti, il database primario è temporaneamente abbassato di livello a secondario, quindi promossa nuovamente. L'aggiornamento della risorsa fa sì che tutte le repliche arrestare e riavviare. Il nuovo valore per`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` viene impostata solo una volta le repliche vengono riavviate, non immediatamente.

## <a name="see-also"></a>Vedere anche

[Gruppi di disponibilità su Linux](sql-server-linux-availability-group-overview.md)

<!--Image references-->
[1]: ./media/sql-server-linux-availability-group-ha/1-read-scale-out.png
[2]: ./media/sql-server-linux-availability-group-ha/2-configuration-only.png
[3]: ./media/sql-server-linux-availability-group-ha/3-three-replica.png
[4]: ./media/sql-server-linux-availability-group-ha/configuration-only-example.png
