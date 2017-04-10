---
title: "Propriet&#224; pubblicazione, Opzioni sottoscrizione | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.pubproperties.subscriptionoptions.f1"
ms.assetid: 31abd605-b273-419d-86df-d0ecf539a507
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Propriet&#224; pubblicazione, Opzioni sottoscrizione
  Il **Opzioni di sottoscrizione** pagina della **Proprietà pubblicazione** la finestra di dialogo consente di visualizzare e impostare le proprietà del livello associate alle sottoscrizioni pubblicazione. Le proprietà sono raggruppate nelle categorie seguenti:  
  
-   Proprietà che si applicano a tutte le pubblicazioni.  
  
-   Proprietà che si applicano alle pubblicazioni snapshot e transazionali, incluse le pubblicazioni che consentono le sottoscrizioni aggiornabili.  
  
-   Proprietà che si applicano alle pubblicazioni di tipo merge.  
  
> [!NOTE]  
>  Alcune proprietà sono di sola lettura, per i motivi spiegati nelle descrizioni delle proprietà all'interno di questo argomento. Per alcune modifiche alle proprietà è necessario un nuovo snapshot per la pubblicazione, mentre per altre è necessaria inoltre la reinizializzazione di tutte le sottoscrizioni. Per ulteriori informazioni, vedere [Modifica proprietà della pubblicazione e articolo](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
## Opzioni per tutte le pubblicazioni  
  
### Creazione e sincronizzazione  
 **Consenti sottoscrizioni anonime**  
 Determina se consentire le sottoscrizioni pull anonime. Le sottoscrizioni anonime sono supportate per [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEWEd2005](../../includes/ssewed2005-md.md)], [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssMobileEd2005](../../includes/ssmobileed2005-md.md)], e [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per Windows CE. Utilizzare questa opzione per pubblicazioni snapshot e transazionali, l'opzione **Snapshot sempre disponibile** deve essere impostato su **True**.  
  
 **Database di sottoscrizione collegabile**  
 Determina se è possano creare sottoscrizioni collegando una copia di un database di sottoscrizione (richiede che l'opzione **Snapshot sempre disponibile** è impostato su **True** per pubblicazioni snapshot e transazionali).  
  
> [!IMPORTANT]  
>  Le sottoscrizioni collegabili non saranno disponibili nelle versioni future. Questa funzionalità è deprecata.  
  
 **Consenti sottoscrizioni pull**  
 Determina se consentire ai Sottoscrittori di creare sottoscrizioni pull sulla pubblicazione corrente. Per ulteriori informazioni, vedere [sottoscrivere pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md).  
  
### Replica dello schema  
 **Replica modifiche dello schema**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. Determina se replicare le modifiche dello schema, ad esempio l'aggiunta di una colonna a una tabella o la modifica del tipo di dati di una colonna, agli oggetti pubblicati. Per ulteriori informazioni, vedere [apportare le modifiche dello Schema nei database di pubblicazione](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
## Opzioni per le pubblicazioni snapshot e transazionali  
  
### Creazione e sincronizzazione  
 **Agente di distribuzione indipendente**  
 Determina se utilizzare un agente che sia indipendente da altre pubblicazioni del database. Questa opzione è di sola lettura. è impostato su **True** per impostazione predefinita per le pubblicazioni creano con la creazione guidata nuova pubblicazione e non possono essere modificate dopo la creazione della pubblicazione. Per ulteriori informazioni, vedere [amministrazione dell'agente di replica](../../relational-databases/replication/agents/replication-agent-administration.md).  
  
 **Snapshot sempre disponibile**  
 Determina se i file di snapshot vengono creati ogni volta che viene eseguito l'agente Snapshot (richiede **agente di distribuzione indipendente**). Questa opzione è di sola lettura. è impostato su **True** Se si seleziona **Crea uno snapshot immediatamente e Mantieni lo snapshot disponibile per l'inizializzazione delle sottoscrizioni** sul **agente Snapshot** pagina della creazione guidata pubblicazione (impostazione predefinita). Per ulteriori informazioni, vedere [creare e applicare lo Snapshot](../../relational-databases/replication/create-and-apply-the-snapshot.md).  
  
 **Consenti inizializzazione dai file di backup**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. Determina se consentire l'utilizzo dei file di backup per inizializzare le sottoscrizioni. Per ulteriori informazioni, vedere [inizializzare una sottoscrizione transazionale senza uno Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 **Consenti Sottoscrittori non SQL Server**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. Determina se la pubblicazione supporta Sottoscrittori non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Impostazione dell'opzione **True** impostate altre proprietà di pubblicazione per il supporto non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i sottoscrittori. Questa opzione è di sola lettura se esistono sottoscrizioni; non può essere impostata su **True** Se **Consenti sottoscrizioni ad aggiornamento immediato**, **in coda Consenti sottoscrizioni ad aggiornamento**, o **Consenti sottoscrizioni peer-to-peer** è impostato su **True**. Per ulteriori informazioni, vedere [sottoscrittori Non SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
### Trasformazioni dei dati  
 **Consenti trasformazioni dei dati**  
 Determina se utilizzare Data Transformation Services (DTS) per trasformare i dati prima di distribuirli a un Sottoscrittore. Questa opzione è di sola lettura. Le trasformazioni dei dati possono essere abilitate solo se una pubblicazione viene creata utilizzando le stored procedure.  
  
> [!IMPORTANT]  
>  Le sottoscrizioni trasformabili non saranno disponibili nelle versioni future. Questa funzionalità è deprecata.  
  
### Replica peer-to-peer  
 **Consenti sottoscrizioni peer-to-peer**  
 Si applica solo a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. Determina se la pubblicazione supporta la replica peer-to-peer. Impostazione dell'opzione **True** impostate altre proprietà di pubblicazione per supportare la replica peer-to-peer. Se esistono sottoscrizioni questa opzione è di sola lettura. Questa opzione non può essere impostata su **True** Se **Consenti sottoscrizioni ad aggiornamento immediato** o **in coda Consenti sottoscrizioni ad aggiornamento**, o **Consenti sottoscrittori non SQL Server** è impostato su **True**. Per ulteriori informazioni, vedere [la replica transazionale Peer-to-Peer](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 **Consenti rilevamento conflitti peer-to-peer**  
 Si applica solo a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive. Specifica se il rilevamento dei conflitti è abilitato per la pubblicazione. Per usare il rilevamento dei conflitti, tutti i nodi devono eseguire [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] o versioni successive e il rilevamento deve essere abilitato per tutti i nodi. Per utilizzare il rilevamento dei conflitti, è inoltre necessario specificare un valore per **id origine Peer**. Per ulteriori informazioni, vedere [il rilevamento dei conflitti nella replica Peer-to-Peer](../../relational-databases/replication/transactional/conflict-detection-in-peer-to-peer-replication.md).  
  
 **ID origine peer**  
 Si applica solo a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive. Specifica un ID per un nodo in una topologia peer-to-peer. Questo ID viene utilizzato per il rilevamento dei conflitti se **Consenti rilevamento conflitti peer-to-peer** è impostato su **True**. Specificare un ID positivo diverso da zero che non sia mai stato utilizzato nella topologia. Per un elenco di ID che sono già stati utilizzati, eseguire una query di [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md) tabella di sistema.  
  
### Sottoscrizioni aggiornabili  
 **Consenti sottoscrizioni ad aggiornamento immediato**  
 Determina se le modifiche apportate ai dati del Sottoscrittore possono essere replicate immediatamente nel server di pubblicazione. Questa opzione è di sola lettura. Le sottoscrizioni aggiornabili possono essere abilitate solo al momento della creazione di una pubblicazione. Per ulteriori informazioni, vedere [sottoscrizioni aggiornabili per la replica transazionale](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 **Consenti sottoscrizioni ad aggiornamento in coda**  
 Determina se le modifiche apportate ai dati del Sottoscrittore possono essere inserite in coda e replicate successivamente nel server di pubblicazione. Questa opzione è di sola lettura. Le sottoscrizioni aggiornabili possono essere abilitate solo al momento della creazione di una pubblicazione. Per ulteriori informazioni, vedere [sottoscrizioni aggiornabili per la replica transazionale](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 **Segnala conflitti a livello centrale**  
 Determina se segnalare le modifiche di dati in conflitto solo nel server di pubblicazione o sia il server di pubblicazione che nel Sottoscrittore (richiede che l'opzione **in coda Consenti sottoscrizioni ad aggiornamento**). Questa opzione è di sola lettura. è impostato su **True** per impostazione predefinita per le pubblicazioni creano con la creazione guidata nuova pubblicazione e non possono essere modificate dopo la creazione della pubblicazione. Il valore **True** significa che i conflitti vengono segnalati solo nel server di pubblicazione. I conflitti possono essere visualizzati solo sul server in cui vengono segnalati.  
  
 **Criteri di risoluzione dei conflitti**  
 Specifica l'azione da intraprendere quando una modifica nel Sottoscrittore è in conflitto con una modifica di server di pubblicazione (è necessaria l'opzione **in coda Consenti sottoscrizioni ad aggiornamento**). Per ulteriori informazioni, vedere [rilevamento dei conflitti di aggiornamento in coda e la risoluzione](../../relational-databases/replication/transactional/queued-updating-conflict-detection-and-resolution.md).  
  
 **Tipo di coda**  
 Determina se utilizzare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] coda o [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing (MSMQ) per accodare le modifiche nel Sottoscrittore fino a quando non è possibile applicarle al server di pubblicazione (è necessaria l'opzione **in coda Consenti sottoscrizioni ad aggiornamento**). Questa opzione riguarda solo [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], poiché nelle versioni successive per l'accodamento vengono sempre utilizzate tabelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Opzioni per le pubblicazioni di tipo merge  
  
### Report sui conflitti  
 **Segnala conflitti a livello centrale**  
 Determina se segnalare i conflitti generati dalle modifiche apportate ai dati solo nel server di pubblicazione o sia nel server di pubblicazione che nel Sottoscrittore. Questa opzione è di sola lettura. è impostato su **True** per impostazione predefinita per le pubblicazioni creano con la creazione guidata nuova pubblicazione e non possono essere modificate dopo la creazione della pubblicazione. Il valore **True** significa che i conflitti vengono segnalati solo nel server di pubblicazione. I conflitti possono essere visualizzati solo sul server in cui vengono segnalati. Per ulteriori informazioni, vedere la sezione "Visualizzazione dei conflitti" di [Avanzate rilevamento dei conflitti della replica di tipo Merge e la risoluzione](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
### Filtro  
 **Consenti filtri con parametri**  
 Viene impostata in base al fatto che una pubblicazione utilizzi i filtri con parametri. Questa opzione è sempre di sola lettura. Per altre informazioni, vedere [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 **Convalida Sottoscrittori**  
 Determina le funzioni da utilizzare per convalidare che un Sottoscrittore disponga della partizione dati corretta. È possibile immettere più valori separandoli con una virgola. Per ulteriori informazioni, vedere [convalidare le informazioni di partizione per un sottoscrittore di tipo Merge](../../relational-databases/replication/validate-partition-information-for-a-merge-subscriber.md).  
  
 **Pre-calcola partizioni**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. Determina se ottimizzare la sincronizzazione calcolando in anticipo quali righe di dati appartengono alle varie partizioni. Per impostazione predefinita **True** Se la pubblicazione soddisfa i criteri per le partizioni precalcolate. Per ulteriori informazioni, vedere [Ottimizza prestazioni filtro con parametri con le partizioni precalcolate](../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md).  
  
 **Ottimizza sincronizzazione**  
 Determina se ottimizzare l'elaborazione di processi merge archiviando metadati aggiuntivi in ogni Sottoscrittore. Questa ottimizzazione è stata sostituita da partizioni precalcolate. il **Ottimizza sincronizzazione** opzione è rilevante solo se **Pre-calcola partizioni** è impostato su **False**. Per altre informazioni, vedere [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
### Processi di merge  
 **Limita processi simultanei**  
 Determina se limitare il numero di agenti di merge che possono essere eseguiti contemporaneamente. Questa opzione viene in genere utilizzata se una pubblicazione include un elevato numero di sottoscrizioni push che potrebbero sincronizzarsi contemporaneamente.  
  
 **Numero massimo processi simultanei**  
 Il numero massimo di agenti di Merge eseguibili contemporaneamente (richiede **Limita processi simultanei**). Se il numero di agenti in sincronizzazione supera il numero massimo, gli agenti vengono inseriti in una coda fino a quando il loro numero non scende al di sotto di tale soglia.  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzazione e modifica delle proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Pubblicazione di dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  