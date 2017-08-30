---
title: "SQL Server Always On modelli distribuzione gruppo di disponibilità | Documenti Microsoft"
ms.custom: 
ms.date: 06/16/2017
ms.prod: sql-linux
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
caps.latest.revision: 34
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 353e7cf5cef8430303e3ee6fbefc92db08f5f733
ms.contentlocale: it-it
ms.lasthandoff: 08/28/2017

---
# <a name="high-availability-and-data-protection-for-availability-group-configurations"></a>Elevata disponibilità e protezione dei dati per le configurazioni di gruppo di disponibilità

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

In questo articolo è configurazioni di distribuzione supportate per i gruppi di disponibilità di SQL Server Always On su server Linux. Un gruppo di disponibilità supporta la disponibilità elevata e la protezione dei dati. Il rilevamento degli errori automatico, failover automatico e la riconnessione dopo il failover trasparente garantire un'elevata disponibilità. Le repliche sincronizzate forniscono la protezione dei dati. 

>[!NOTE]
>Oltre a disponibilità elevata e la protezione dei dati, un gruppo di disponibilità può anche fornire il ripristino di emergenza, piattaforma migrazione tra e lettura di scalabilità orizzontale. Questo articolo illustra principalmente le implementazioni per la protezione dati e la disponibilità elevata. 

Con Windows Server failover clustering, una configurazione comune per la disponibilità elevata utilizza due repliche sincrone e un [condivisione di file server di controllo](http://technet.microsoft.com/library/cc731739.aspx). La condivisione di file di controllo convalida la configurazione del gruppo di disponibilità - stato di sincronizzazione e il ruolo della replica, ad esempio. Questa configurazione assicura che la replica secondaria scelta come destinazione del failover è disponibili dati più recenti le modifiche alla configurazione gruppo di disponibilità. 

Le soluzioni a disponibilità elevata corrente per Linux non consentire l'inserimento di un controllo esterno come condivisione file di controllo in un cluster di failover di Windows Server. Quando è presente alcun cluster di failover di Windows Server, la configurazione del gruppo di disponibilità è archiviata nel database master in istanze di SQL Server coinvolte. Pertanto, il gruppo di disponibilità richiede almeno tre repliche sincrone per la protezione dati e la disponibilità elevata. Dopo aver creato un gruppo di disponibilità su server Linux, è possibile creare una risorsa cluster. Le impostazioni delle risorse cluster determinano la configurazione per la disponibilità elevata.

Scegliere una struttura di gruppo di disponibilità per soddisfare specifici requisiti aziendali per la disponibilità elevata, protezione dei dati e leggere scalabilità orizzontale.

>[!IMPORTANT]
>Le configurazioni seguenti vengono descritti i modelli di progettazione di gruppo di disponibilità e le funzionalità di ogni modello. Questi modelli di progettazione si applicano ai gruppi di disponibilità con `CLUSTER_TYPE = EXTERNAL` per soluzioni a disponibilità elevata. 

I modelli di progettazione sono due configurazioni di gruppo di disponibilità. Le configurazioni includono:

- **Tre repliche sincrone**

- **Due repliche sincrone**

## <a name="how-the-configuration-affects-default-resource-settings"></a>Le impostazioni predefinite di influenza la configurazione

L'impostazione della risorsa cluster `required_synchronized_secondaries_to_commit` garantisce che ogni transazione viene scritto un numero minimo di log di replica secondaria prima di eseguire il commit della transazione nella replica primaria. Questa impostazione può influenzare un'elevata disponibilità e la protezione dei dati, a seconda della configurazione. Quando si installa l'agente di risorse di SQL Server - `mssql-server-ha` - e creare una risorsa cluster del gruppo di disponibilità, la gestione di cluster rileva la disponibilità del gruppo configurazione e set `required_synchronized_secondaries_to_commit` di conseguenza. 

Se è supportata dalla configurazione, il parametro dell'agente risorsa `required_synchronized_secondaries_to_commit` è impostata sul valore che fornisce la protezione dati e la disponibilità elevata. Per ulteriori informazioni, vedere [comprendere SQL Server agent di risorsa per pacemaker](#pacemakerNotify).

Le sezioni seguenti illustrano il comportamento predefinito per la risorsa cluster. 

<a name="threeSynch"></a>

## <a name="three-synchronous-replicas"></a>Tre repliche sincrone

Questa configurazione è costituita da tre repliche sincrone. Per impostazione predefinita, fornisce ad alta disponibilità e protezione dei dati. È inoltre possibile fornire lettura scalabilità orizzontale.

![Tre repliche][3]

Nella tabella seguente viene descritto il comportamento di un protezione dati e la disponibilità elevato basato sulle impostazioni per un gruppo di disponibilità con repliche sincrone tre: 

|`required_synchronized_secondaries_to_commit`|0 |1 \*|2
| --- |:---:|:---:|:---:
|Failover automatico dopo un'interruzione di replica primaria| |✔| 
|Replica primaria disponibile dopo l'interruzione di una replica secondaria|✔|✔| 
|Replica primaria disponibile dopo due interruzioni di replica secondaria|✔| |
|Failover manuale dopo l'interruzione di replica primaria - possibile perdita di dati|✔| | 

\*Impostazione quando il gruppo di disponibilità viene aggiunto come risorsa in un cluster predefinita.

<a name="twoSynch"></a>

## <a name="two-synchronous-replicas"></a>Due repliche sincrone

Questa configurazione consente la protezione dei dati. Come le altre configurazioni gruppo disponibilità, è possibile attivare lettura scalabilità orizzontale. La configurazione di due repliche sincrone non fornisce la disponibilità elevata automatica. 

![Due repliche sincrone][1]

Questa configurazione richiede due server. Questi server ricoprire il ruolo della replica primaria e secondaria. 

La configurazione di due repliche sincrone è ottimizzata per i dati di protezione e la distribuzione del carico di lavoro di lettura per i database. Per impostazione predefinita, la risorsa è configurata per la protezione dati. Questa configurazione fornisce disponibilità elevata perché se l'istanza di SQL Server non riesce, il database non è completamente disponibile o vi è rischio di perdita di dati. 

Nella tabella seguente vengono descritti il comportamento di protezione dati in base ai valori possibili per un gruppo di disponibilità con due repliche sincrone: 

|`required_synchronized_secondaries_to_commit`|0 \*|1 
| --- |:---|:---
|Failover automatico dopo un'interruzione di replica primaria| |✔ \*\* | 
|Replica primaria disponibile dopo l'interruzione di replica secondaria|✔| |

\*Impostazione quando il gruppo di disponibilità viene aggiunto come risorsa in un cluster predefinita.

\*\*In questa configurazione, dopo l'interruzione della replica primaria del gruppo di disponibilità automatico viene eseguito il failover. Le applicazioni non possono connettersi al gruppo di disponibilità, fino a quando la replica primaria è in linea - ora come una replica secondaria. 

La configurazione di due repliche sincrone può essere più economica perché richiede solo due istanze di SQL Server in due server.

<a name="pacemakerNotify"></a>

## <a name="understand-sql-server-resource-agent-for-pacemaker"></a>Comprendere l'agente di risorse di SQL Server per pacemaker

SQL Server 2017 CTP 1.4 aggiunto `sequence_number` a `sys.availability_groups` per consentire il Pacemaker identificare secondario di aggiornamento delle repliche sono con la replica primaria. `sequence_number`è un valore BIGINT a incremento progressivo costante che rappresenta di aggiornamento di replica del gruppo di disponibilità locale. Gli aggiornamenti pacemaker il `sequence_number` con ogni modifica della configurazione gruppo di disponibilità. Esempi di modifiche di configurazione includono il failover, aggiunta di replica o la rimozione. Il numero viene aggiornato nel server primario, quindi replicato a repliche secondarie. In questo modo una replica secondaria con configurazione aggiornata ha lo stesso numero di sequenza del database primario. 

Quando il Pacemaker decide di alzare di livello una replica primaria, prima invia un *pre-alzare di livello* notifica a tutte le repliche. Le repliche di restituiscono il numero di sequenza. Successivamente, quando Pacemaker esegue effettivamente un tentativo di promuovere una replica primaria, la replica solo promuove se stesso se il numero di sequenza è il più elevato di tutti i numeri di sequenza. Se il proprio numero di sequenza non corrisponde il numero di sequenza più alto, la replica rifiuta l'operazione Alza di livello. In questo modo, solo la replica con il numero di sequenza più alto può essere alzata di livello e impostata come primaria e non si verifica alcuna perdita dei dati. 

Questo processo richiede almeno una replica è disponibile per l'innalzamento di livello con lo stesso numero di sequenza come database primario precedente. Il set di agente di risorse Pacemaker `required_synchronized_secondaries_to_commit` in modo che almeno una replica secondaria asincrona è aggiornato e disponibile per essere la destinazione di un failover automatico per impostazione predefinita. Con ogni azione di monitoraggio, il valore di `required_synchronized_secondaries_to_commit` viene calcolato (e aggiornati se necessario). Il `required_synchronized_secondaries_to_commit` valore è 'numero di repliche sincrone' diviso 2. In fase di failover, è necessario l'agente di risorsa (`total number of replicas`  -  `required_synchronized_secondaries_to_commit` repliche) per rispondere al pre-promuovere notifica. La replica con il più elevato `sequence_number` viene promossa a primaria. 

Ad esempio, un gruppo di disponibilità con tre repliche sincrone - una replica primaria e due repliche secondarie sincrone.

- `required_synchronized_secondaries_to_commit`è 1. (3 / 2 -> 1).

- Il numero di repliche per rispondere ai pre-fini dell'azione di richiesto è 2. (3 - 1 = 2). 

In questo scenario, è necessario rispondere per il failover deve essere attivata due repliche. Per il failover automatico ha esito positivo dopo un'interruzione della replica primaria, sia nelle repliche secondarie desidera essere aggiornate e rispondere alla pre-promuovere notifica. Se sono online e sincrona, hanno lo stesso numero di sequenza. Il gruppo di disponibilità Alza di livello uno di essi. Se solo una delle repliche secondarie risponde a di alzare di pre-livello azione, l'agente di risorsa non può garantire che il database secondario che ha risposto ha sequence_number il più elevato, e non viene attivato un failover.

>[!IMPORTANT]
>Quando `required_synchronized_secondaries_to_commit` è 0 esiste il rischio di perdita dei dati. Durante un'interruzione di replica primaria, l'agente di risorsa non verrà automaticamente avviato un failover. È possibile attendere per il sito primario ripristinare o eseguire manualmente il failover utilizzando `FORCE_FAILOVER_ALLOW_DATA_LOSS`.

È possibile scegliere di ignorare il comportamento predefinito e impedire l'impostazione della risorsa del gruppo di disponibilità `required_synchronized_secondaries_to_commit` automaticamente.

Lo script seguente imposta `required_synchronized_secondaries_to_commit` su 0 in un gruppo di disponibilità denominato `<**ag1**>`. Prima di eseguire sostituire `<**ag1**>` con il nome del gruppo di disponibilità.

```bash
sudo pcs resource update <**ag1**> required_synchronized_secondaries_to_commit=0
```

Per ripristinare il valore predefinito, in base alla configurazione gruppo di disponibilità eseguire:

```bash
sudo pcs resource update <**ag1**> required_synchronized_secondaries_to_commit=
```

>[!NOTE]
>Quando si eseguono i comandi precedenti, il database primario è temporaneamente abbassato di livello a secondario, quindi promossa nuovamente. L'aggiornamento della risorsa fa sì che tutte le repliche arrestare e riavviare. Il nuovo valore per`required_synchronized_secondaries_to_commit` viene impostata solo una volta le repliche vengono riavviate, non immediatamente.

<!--Image references-->
[1]: ./media/sql-server-linux-availability-group-ha/1-read-scale-out.png
[3]: ./media/sql-server-linux-availability-group-ha/3-three-replica.png
