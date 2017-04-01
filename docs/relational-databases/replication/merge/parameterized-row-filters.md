---
title: "Filtri di riga con parametri | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pubblicazioni [replica di SQL Server], filtri dinamici"
  - "replica di tipo merge [replica di SQL Server], filtri dinamici"
  - "filtri con parametri [replica di SQL Server]"
  - "filtri [replica di SQL Server], dinamici"
  - "filtri con parametri per replica di tipo merge [replica di SQL Server]"
  - "pubblicazioni [replica di SQL Server], filtri con parametri"
  - "filtri con parametri [replica di SQL Server], informazioni sui filtri con parametri"
  - "filtri [replica di SQL Server], con parametri"
  - "filtri dinamici [replica di SQL Server]"
ms.assetid: b48a6825-068f-47c8-afdc-c83540da4639
caps.latest.revision: 69
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Filtri di riga con parametri
  I filtri di riga con parametri consentono l'invio di partizioni di dati diverse a Sottoscrittori diversi senza che sia necessario creare più pubblicazioni. Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], i filtri con parametri vengono definiti filtri dinamici. Una partizione è un subset delle righe di una tabella. In base alle impostazioni scelte durante la creazione di un filtro di riga con parametri, ogni riga di una tabella pubblicata può appartenere a un'unica partizione, con la conseguente produzione di partizioni non sovrapposte, o a due o più partizioni, con la conseguente produzione di partizioni sovrapposte.  
  
 È possibile condividere le partizioni non sovrapposte tra sottoscrizioni oppure limitarle in modo che solo una sottoscrizione riceva una determinata partizione. Le impostazioni che controllano il comportamento delle partizioni vengono descritte nella sezione "Utilizzo delle opzioni di filtro appropriate" di seguito in questo argomento. L'utilizzo di tali impostazioni consente di personalizzare il filtro con parametri in base ai requisiti dell'applicazione e delle prestazioni. In generale, le partizioni sovrapposte offrono maggiore flessibilità, mentre le partizioni non sovrapposte replicate in una singola sottoscrizione garantiscono prestazioni superiori.  
  
 I filtri con parametri vengono utilizzati in una tabella singola e vengono in genere uniti ai filtri join per estendere il filtro alle tabelle correlate. Per ulteriori informazioni, vedere [filtri Join](../../../relational-databases/replication/merge/join-filters.md).  
  
 Per definire o modificare un filtro di riga con parametri, vedere [definire e modificare un filtro di riga con parametri per un articolo di Merge](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
## Modalità di funzionamento dei filtri con parametri  
 Un filtro di riga con parametri utilizza una clausola WHERE per selezionare i dati appropriati da pubblicare. Anziché specificare un valore letterale nella clausola, come avviene con il filtro di riga statico, si specificano una o entrambe le funzioni di sistema seguenti: SUSER_SNAME() e HOST_NAME(). È anche possibile utilizzare funzioni definite dall'utente, ma è necessario che le funzioni di sistema SUSER_SNAME() o HOST_NAME() siano incluse nel corpo della funzione oppure vengano valutate, ad esempio `MyUDF(SUSER_SNAME()`. Se una funzione definita dall'utente include SUSER_SNAME() o HOST_NAME() nel corpo della funzione, non è possibile passare parametri alla funzione.  
  
 Le funzioni di sistema SUSER_SNAME() e HOST_NAME() non sono specifiche della replica di tipo merge, ma vengono utilizzate da questo tipo di replica per il filtro con parametri:  
  
-   SUSER_SNAME() restituisce informazioni di accesso per le connessioni stabilite a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Quando viene impiegata in un filtro con parametri, restituisce le informazioni di accesso utilizzate dall'agente di merge per connettersi al server di pubblicazione. Le informazioni di accesso vengono specificate quando si crea una sottoscrizione.  
  
-   HOST_NAME() restituisce il nome del computer che sta effettuando la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Quando viene impiegata in un filtro con parametri, per impostazione predefinita restituisce il nome del computer in cui è in esecuzione l'agente di merge. Per le sottoscrizioni pull è il nome del Sottoscrittore, mentre per le sottoscrizioni push è il nome del server di distribuzione.  
  
     È inoltre possibile sostituire questa funzione con un valore diverso dal nome del Sottoscrittore o del server di distribuzione. In genere il valore di questa funzione viene sostituito con valori più significativi, ad esempio il nome o l'ID del venditore. Per ulteriori informazioni, vedere la sezione relativa alla sostituzione del valore di HOST_NAME() in questo argomento.  
  
 Il valore restituito dalla funzione di sistema viene confrontato con una colonna specificata nella tabella in cui viene applicato il filtro e i dati appropriati vengono scaricati nel Sottoscrittore. Il confronto viene effettuato quando la sottoscrizione è inizializzata, in modo che solo i dati appropriati siano contenuti nello snapshot iniziale, e ogni volta che la sottoscrizione viene sincronizzata. Per impostazione predefinita, se rileva una modifica nel server di pubblicazione in una riga viene spostata da una partizione, la riga viene eliminata nel Sottoscrittore (questo comportamento è controllato tramite il **@allow_partition_realignment** parametro [sp_addmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)).  
  
> [!NOTE]  
>  Quando i confronti vengono effettuati per i filtri con parametri, vengono sempre utilizzate le regole di confronto del database. Se, ad esempio, nelle regole di confronto del database non viene fatta distinzione tra maiuscole e minuscole, mentre in quelle della colonna o della tabella sì, durante il confronto non viene fatta tale distinzione.  
  
### Applicazione del filtro con SUSER_SNAME()  
 Si consideri il **tabella Employee** nel [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] database di esempio. Questa tabella è inclusa la colonna **LoginID**, che contiene l'account di accesso per ogni dipendente nel formato '*dominio\account di accesso*'. Per filtrare questa tabella in modo che i dipendenti ricevano solo i dati pertinenti, specificare una clausola di filtro:  
  
```  
LoginID = SUSER_SNAME()  
```  
  
 Il valore per uno dei dipendenti è, ad esempio, "adventure-works\john5". Quando l'agente di merge si connette al server di pubblicazione, utilizza l'account di accesso specificato durante la creazione della sottoscrizione, in questo caso "adventure-works\john5". L'agente di Merge, quindi confronta il valore restituito da SUSER_SNAME () con i valori nella tabella e Scarica solo la riga che contiene un valore di "Adventure-works\john5" di **LoginID** colonna.  
  
### Applicazione del filtro con HOST_NAME()  
 Si consideri il **HumanResources. Employee** tabella. Si supponga che la tabella inclusa una colonna, ad esempio **nomecomputer** con il nome del computer di ogni dipendente nel formato '*nome_tipo di computer*'. Per filtrare questa tabella in modo che i dipendenti ricevano solo i dati pertinenti, specificare una clausola di filtro:  
  
```  
ComputerName = HOST_NAME()  
```  
  
 Il valore per uno dei dipendenti potrebbe ad esempio essere "john5_laptop". Quando l'agente di Merge si connette al server di pubblicazione, confronta il valore restituito da HOST_NAME () con i valori nella tabella e Scarica solo la riga che contiene un valore di "john5_laptop" nella **nomecomputer** colonna.  
  
 Le funzioni possono inoltre essere combinate in un filtro. Per essere certi che un dipendente riceva i dati solo nel caso utilizzi il proprio account di accesso nel computer, ad esempio, la clausola di filtro sarà:  
  
```  
LoginID = SUSER_SNAME() AND ComputerName = HOST_NAME()  
```  
  
 A meno che non si sostituisca il valore di HOST_NAME(), il filtro con HOST_NAME() viene in genere utilizzato solo con le sottoscrizioni pull. Il valore restituito dalla funzione è il nome del computer in cui è in esecuzione l'agente di merge. Per quanto riguarda le sottoscrizioni pull, il valore è diverso per ogni sottoscrizione, mentre per quanto riguarda le sottoscrizioni push il valore è identico. Per le sottoscrizioni push tutti gli agenti di merge vengono eseguiti nel server di distribuzione.  
  
> [!IMPORTANT]  
>  Poiché è possibile sostituire il valore della funzione HOST_NAME(), per controllare l'accesso a partizioni di dati non è possibile utilizzare filtri che includano HOST_NAME(). Per controllare l'accesso a partizioni di dati, utilizzare SUSER_SNAME(), SUSER_SNAME() in combinazione con HOST_NAME() oppure filtri di riga statici.  
  
#### Sostituzione del valore di HOST_NAME()  
 Come già evidenziato, per impostazione predefinita HOST_NAME() restituisce il nome del computer che sta effettuando la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Quando vengono utilizzati filtri con parametri, è normale sostituire questo valore fornendo un valore durante la creazione di una sottoscrizione. La funzione HOST_NAME() restituisce quindi il valore specificato anziché il nome del computer.  
  
> [!NOTE]  
>  Se si sostituisce il valore HOST_NAME(), tutte le chiamate alla funzione HOST_NAME() restituiranno il valore specificato dall'utente. Verificare che il funzionamento di altre applicazioni non dipenda dal fatto che HOST_NAME() restituisca il nome del computer.  
  
 Si consideri il **HumanResources. Employee** tabella. Questa tabella è inclusa la colonna **EmployeeID**. Per filtrare questa tabella in modo che ogni dipendente riceva solo i dati di pertinenza, specificare una clausola di filtro:  
  
 `EmployeeID = CONVERT(int,HOST_NAME())`  
  
 Alla dipendente Pamela Ansman-Wolfe, ad esempio, è stato associato l'ID 280. Specificare il valore dell'ID del dipendente (280 nell'esempio) come valore di HOST_NAME() durante la creazione di una sottoscrizione per questo dipendente. Quando l'agente di Merge si connette al server di pubblicazione, confronta il valore restituito da HOST_NAME () con i valori nella tabella e Scarica solo la riga che contiene un valore di 280 nella **EmployeeID** colonna.  
  
> [!IMPORTANT]  
>  La funzione HOST_NAME () restituisce un **nchar** valore, è necessario utilizzare CONVERT se la colonna nella clausola di filtro è di tipo di dati numerico, come nell'esempio precedente. Per motivi relativi alle prestazioni, è consigliabile non applicare funzioni ai nomi di colonna nelle clausole di filtro di riga con parametri, come `CONVERT(nchar,EmployeeID) = HOST_NAME()`. È consigliabile invece utilizzare l'approccio indicato nell'esempio: `EmployeeID = CONVERT(int,HOST_NAME())`. Questa clausola può essere utilizzata per la **@subset_filterclause** parametro [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), ma in genere non può essere utilizzata la creazione guidata nuova pubblicazione (la procedura guidata esegue la clausola di filtro per la convalida, ha esito negativo poiché il nome del computer non può essere convertito in un **int**). Se si utilizza la creazione guidata nuova pubblicazione, è consigliabile specificare `CONVERT(nchar,EmployeeID) = HOST_NAME()` la procedura guidata e quindi utilizzare [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) per modificare la clausola `EmployeeID = CONVERT(int,HOST_NAME())` prima di creare uno snapshot per la pubblicazione.  
  
 **Per sostituire il valore di HOST_NAME()**  
  
 Utilizzare uno dei metodi seguenti per sostituire il valore di HOST_NAME():  
  
-   [! Includi [ssManStudioFull] (... / Token/ssManStudioFull_md.md)]: specify a value on the **HOST\_NAME\(\) Values** page of the New Subscription Wizard. For more information about creating subscriptions, see [Subscribe to Publications](../../../relational-databases/replication/subscribe-to-publications.md).  
  
-   Replica [!INCLUDE[tsql](../../../includes/tsql-md.md)] di programmazione: specificare un valore per il **@hostname** parametro [sp_addmergesubscription & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md) (per le sottoscrizioni push) o [sp_addmergepullsubscription_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) (per le sottoscrizioni pull).  
  
-   Agente di merge: specificare un valore per il **- Hostname** parametro dalla riga di comando o tramite un profilo agente. Per ulteriori informazioni sull'agente di Merge, vedere [agente Merge repliche](../../../relational-databases/replication/agents/replication-merge-agent.md). Per ulteriori informazioni sui profili degli agenti, vedere [Profili agenti di replica](../../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
## Inizializzazione di una sottoscrizione di una pubblicazione con filtri con parametri  
 Quando si utilizzano filtri di riga con parametri nelle pubblicazioni di tipo merge, ogni sottoscrizione con uno snapshot in due parti viene inizializzata dalla replica. Per altre informazioni, vedere [Snapshots for Merge Publications with Parameterized Filters](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
## Utilizzo delle opzioni di filtro appropriate  
 Quando si utilizzano filtri con parametri, è possibile avere il controllo su due aree principali:  
  
-   Come i filtri vengono elaborati dalla replica di tipo merge, viene controllata da una delle due impostazioni di pubblicazione: **utilizzare gruppi di partizioni** e **mantenere le modifiche alle partizioni**.  
  
-   La modalità di condivisione dei dati tra i sottoscrittori, che devono essere riflessa dall'impostazione dell'articolo **Opzioni di partizionamento**.  
  
 Per impostare le opzioni di filtro, vedere [ottimizzare i filtri di riga con parametri](../../../relational-databases/replication/publish/optimize-parameterized-row-filters.md).  
  
### Impostazione di "use partition groups" e "keep partition changes"  
 Entrambi i **utilizzare gruppi di partizioni** e **mantenere le modifiche alle partizioni** Opzioni di migliorare le prestazioni di sincronizzazione per le pubblicazioni con gli articoli filtrati mediante l'archiviazione di metadati aggiuntivi nel database di pubblicazione. Il **utilizzare gruppi di partizioni** opzione offre prestazioni superiori tramite la caratteristica delle partizioni precalcolate. Questa opzione è impostata su **true** per impostazione predefinita se gli articoli nella pubblicazione sono conformi a un set di requisiti. Per ulteriori informazioni su questi requisiti, vedere [Ottimizza prestazioni filtro con parametri con le partizioni precalcolate](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md). Se gli articoli non soddisfano i requisiti per l'utilizzo di partizioni pre-calcolate, il **mantenere le modifiche alle partizioni** opzione è impostata su **true**.  
  
### Impostazione di "partition options"  
 Specificare un valore per il **Opzioni di partizionamento** proprietà durante la creazione di un articolo, in base al modo in cui i dati della tabella filtrata verranno condivisi dai sottoscrittori. La proprietà può essere impostata su uno dei quattro valori utilizzando [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), e **Proprietà articolo** la finestra di dialogo. La proprietà può essere impostata su uno dei due valori utilizzando il **Aggiungi filtro** o **Modifica filtro** le finestre di dialogo disponibili dalla creazione guidata pubblicazione e la **Proprietà pubblicazione** la finestra di dialogo. Nella tabella seguente vengono descritti i valori disponibili.  
  
|Descrizione|Valore in Aggiungi filtro e Modifica filtro|Valore in Proprietà articolo|Valore nelle stored procedure|  
|-----------------|-----------------------------------------|---------------------------------|--------------------------------|  
|I dati nelle partizioni sono sovrapposti e il Sottoscrittore può aggiornare le colonne a cui si fa riferimento in un filtro con parametri.|**Una riga di questa tabella verrà inviata a più sottoscrizioni**|**Sovrapposte**|**0**|  
|I dati nelle partizioni sono sovrapposti e il Sottoscrittore non può aggiornare le colonne a cui si fa riferimento in un filtro con parametri.|N/D*|**Sovrapposte, non ammesse modifiche dei dati fuori partizione**|**1**|  
|I dati nelle partizioni non sono sovrapposti e vengono condivisi dalle sottoscrizioni. Il Sottoscrittore non può aggiornare le colonne a cui si fa riferimento in un filtro con parametri.|N/D*|**Non sovrapposte, condivise dalle sottoscrizioni**|**2**|  
|I dati nelle partizioni non sono sovrapposti ed esiste un'unica sottoscrizione per partizione. Il Sottoscrittore non può aggiornare le colonne a cui si fa riferimento in un filtro con parametri.**|**Una riga di questa tabella verrà inviata a una sola sottoscrizione**|**Non sovrapposte, sottoscrizione unica**|**3**|  
  
 \*Se l'opzione di filtro sottostante è impostata su **0**, o **1**, o **2**,  **Aggiungi filtro** e **Modifica filtro** verranno visualizzate finestre di dialogo **una riga di questa tabella verrà inviata a più sottoscrizioni**.  
  
 **Se si specifica questa opzione, per ogni partizione dei dati dell'articolo può esistere una sola sottoscrizione. Se si crea una seconda sottoscrizione nella quale il criterio di filtro porta alla restituzione della stessa partizione della sottoscrizione esistente, quest'ultima viene eliminata.  
  
> [!IMPORTANT]  
>  Il **Opzioni di partizionamento** valore deve essere impostato in base alla modalità di condivisione dati dai sottoscrittori. Se, ad esempio, si specifica che una partizione non sia sovrapposta, con una sola sottoscrizione per partizione, ma successivamente i dati vengono aggiornati in un altro Sottoscrittore, è possibile che si verifichi un errore nell'agente di merge durante la sincronizzazione e che quindi i dati non siano convergenti.  
  
#### Selezione dell'opzione di partizione appropriata  
 Le partizioni non sovrapposte vengono utilizzate insieme alle partizioni pre-calcolate per migliorare le prestazioni in situazioni in cui alcuni limiti funzionali sono accettabili. Le partizioni pre-calcolate consentono di velocizzare i download nei Sottoscrittori, ma rallentano le operazioni di caricamento. Le partizioni non sovrapposte riducono al minimo il costo di caricamento associato alle partizioni pre-calcolate. Il vantaggio a livello di prestazioni delle partizioni non sovrapposte è più evidente quando i filtri con parametri e i filtri join utilizzati sono più complessi.  
  
 Quando si scelgono le opzioni di partizione da utilizzare in una pubblicazione, considerare gli scenari seguenti.  
  
-   [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] dispone di una forza vendita mobile con ogni venditore responsabile dei clienti in un determinato codice postale. L'applicazione richiede l'aggiornamento del codice postale nel caso un cliente passi da un territorio di vendita a un altro, affinché il cliente venga assegnato a un altro venditore. Il filtro con parametri è basato sul codice postale del cliente e l'aggiornamento determina la rimozione del codice postale dalla partizione di un venditore e il relativo inserimento nella partizione di un altro venditore. A tale scopo, sono necessarie partizioni sovrapposte che consentano di aggiornare le colonne a cui si fa riferimento in un filtro con parametri. Questa opzione ottimizza la flessibilità, ma il funzionamento potrebbe non essere ottimale come quello delle partizioni non sovrapposte.  
  
-   Un'agenzia di collocamento dispone di dati che vengono inviati alle filiali di ogni regione dello stato. I dati non si sovrappongono e ogni riga della tabella nella sede centrale dell'agenzia è inclusa in un'unica partizione, ma tale partizione viene inviata a più uffici della stessa regione. L'opzione che prevede partizioni non sovrapposte con partizioni condivise dalle sottoscrizioni è appropriata, poiché garantisce prestazioni migliori rispetto alle partizioni sovrapposte soddisfacendo al tempo stesso i requisiti dell'applicazione.  
  
-   Se si dispone di partizioni non sovrapposte e una sola sottoscrizione riceve e aggiorna i dati in una partizione, sarà possibile ottenere ulteriori vantaggi a livello di prestazioni. Questo scenario è tipico dei sistemi POS e delle applicazioni relative al personale esterno in cui i dati vengono raccolti principalmente nel Sottoscrittore e caricati nel server di pubblicazione. Si consideri un **pacchetto** tabella in un'applicazione di distribuzione: mentre ogni pacchetto viene caricato su un furgone, lo stato del pacchetto viene modificato nel **pacchetto** tabella e la modifica viene replicata nella sede centrale. I driver non aggiorna lo stato di uno stesso pacchetto su due furgoni diversi, in modo che il **pacchetto** tabella è un buon candidato per una partizione non sovrapposta con una sola sottoscrizione per partizione.  
  
#### Considerazioni sulle partizioni non sovrapposte  
 Quando si utilizzano le partizioni non sovrapposte, tenere presenti le considerazioni seguenti:  
  
##### Considerazioni generali  
  
-   È necessario che nella pubblicazione vengano utilizzate partizioni pre-calcolate.  
  
-   È necessario che una riga appartenga a una sola partizione.  
  
-   Gli articoli non possono fare parte di un record logico.  
  
-   I partner di sincronizzazione alternativi non sono supportati. Questa funzionalità è deprecata.  
  
-   Il Sottoscrittore non può aggiornare le colonne a cui si fa riferimento in un filtro con parametri.  
  
-   Se un'operazione di inserimento nel Sottoscrittore non appartiene alla partizione, non viene eliminata. Tuttavia, non verrà replicata in altri Sottoscrittori.  
  
-   In alcuni casi con le partizioni sovrapposte, gli intervalli di valori Identity vengono modificati quando vengono inseriti dati tramite l'agente di merge. Con le partizioni non sovrapposte, gli intervalli possono essere modificati solo durante le operazioni di inserimento di un utente che dispone dell'autorizzazione necessaria per modificare gli intervalli di valori Identity nel database di sottoscrizione. L'utente proprietario della tabella, oppure essere un membro del **sysadmin** ruolo predefinito del server, il **db_owner** ruolo predefinito del database, o **db_ddladmin** ruolo predefinito del database.  
  
##### Considerazioni aggiuntive sulle partizioni non sovrapposte con una sola sottoscrizione per partizione  
  
-   Gli articoli possono esistere in una sola pubblicazione e non possono essere ripubblicati.  
  
-   La pubblicazione deve consentire ai Sottoscrittori di avviare l'elaborazione degli snapshot. Per altre informazioni, vedere [Snapshots for Merge Publications with Parameterized Filters](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
##### Considerazione aggiuntive sui filtri join  
  
-   In una gerarchia di filtri join un articolo con una partizione sovrapposta non può trovarsi sopra un articolo con una partizione non sovrapposta. In altre parole, un articolo padre deve utilizzare partizioni non sovrapposte se queste sono utilizzate dall'articolo figlio. Per informazioni sui filtri join, vedere [filtri Join](../../../relational-databases/replication/merge/join-filters.md).  
  
-   Deve avere un filtro di join in cui la partizione non sovrapposta è un figlio di **joinuniquekey** impostata su 1. Per ulteriori informazioni, vedere [filtri Join](../../../relational-databases/replication/merge/join-filters.md).  
  
-   È necessario che l'articolo abbia un solo filtro con parametri o un solo filtro join. L'articolo può avere un filtro con parametri ed essere l'elemento padre in un filtro join. Non può invece avere un filtro con parametri ed essere l'elemento figlio in un filtro join. Non può inoltre avere più di un filtro join.  
  
-   Se due tabelle nel server di pubblicazione hanno una relazione tra filtri join e la tabella figlio contiene righe che non hanno una riga corrispondente nella tabella padre, un'operazione di inserimento della riga padre mancante non avrà come conseguenza il download delle righe correlate nel Sottoscrittore. Le righe verrebbero invece scaricate con partizioni sovrapposte. Ad esempio, se il **SalesOrderDetail** tabella contiene righe con alcuna riga corrispondente nella **SalesOrderHeader** e si inserisce la riga mancante in **SalesOrderHeader**, la riga viene scaricata nel Sottoscrittore, ma le righe corrispondenti presenti **SalesOrderDetail** non sono.  
  
## Vedere anche  
 [Procedure consigliate per i filtri di riga basati sul tempo](../../../relational-databases/replication/merge/best-practices-for-time-based-row-filters.md)   
 [Filtro dei dati pubblicati](../../../relational-databases/replication/publish/filter-published-data.md)   
 [Filtro dei dati pubblicati per la replica di tipo merge](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)  
  
  