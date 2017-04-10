---
title: "Raggruppamento di modifiche alla righe correlate con record logici | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "record logici di replica di tipo merge [replica di SQL Server]"
  - "articoli [replica di SQL Server], record logici"
  - "record logici [replica di SQL Server]"
ms.assetid: ad76799c-4486-4b98-9705-005433041321
caps.latest.revision: 55
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 55
---
# Raggruppamento di modifiche alla righe correlate con record logici
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 Per impostazione predefinita, i dati dei processi di replica di tipo merge cambiano riga per riga. In molti casi questo comportamento è appropriato, ma per alcune applicazioni è essenziale che le righe correlate vengano elaborate come unità. La funzionalità di record logici della replica di tipo merge consente di definire una relazione tra righe correlate di tabelle diverse, in modo che le righe vengano elaborate come unità.  
  
> [!NOTE]  
>  La funzionalità di record logici può essere utilizzata da sola o unitamente a filtri join. Per ulteriori informazioni sui filtri join, vedere [filtri Join](../../../relational-databases/replication/merge/join-filters.md). Per utilizzare i record logici, è necessario che il livello di compatibilità della pubblicazione sia almeno 90RTM.  
  
 Si considerino le tre tabelle correlate seguenti:  
  
 ![Record logico per tre tabelle, con solo i nomi di colonna](../../../relational-databases/replication/merge/media/logical-records-01.gif "Record logico per tre tabelle, con solo i nomi di colonna")  
  
 Il **clienti** tabella corrisponde alla tabella padre nella relazione e dispone di una colonna chiave primaria **CustID**. Il **ordini** tabella contiene una colonna chiave primaria **OrderID**, con un vincolo foreign key nella **CustID** colonna che fa riferimento il **CustID** colonna il **clienti** tabella. Allo stesso modo, il **OrderItems** tabella contiene una colonna chiave primaria **OrderItemID**, con un vincolo foreign key nella **OrderID** colonna che fa riferimento il **OrderID** colonna il **ordini** tabella.  
  
 In questo esempio, un record logico è costituito da tutte le righe di **ordini** tabella in cui sono correlati a un singolo **CustID** valore e tutte le righe nel **OrderItems** tabella in cui sono correlati a tali righe il **ordini** tabella. Nel grafico seguente vengono illustrate tutte le righe delle tre tabelle che si trovano nel record logico di Customer2:  
  
 ![Record logico per tre tabelle con valori](../../../relational-databases/replication/merge/media/logical-records-02.gif "Record logico per tre tabelle con valori")  
  
 Per definire una relazione tra record logici tra gli articoli, vedere [definire una logica Record relazione tra tabella articoli di Merge](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md).  
  
## Vantaggi dei record logici  
 La funzionalità di record logici offre due vantaggi principali:  
  
-   Applicazione delle modifiche ai dati come unità.  
  
-   Rilevamento e risoluzione di conflitti contemporaneamente in più righe di più tabelle.  
  
### Applicazione di modifiche come unità  
 Se l'elaborazione di tipo merge viene interrotta, ad esempio nel caso di interruzione della connessione, se sono stati utilizzati record logici, viene eseguito il rollback del set parzialmente completato di modifiche replicate correlate. Ad esempio, si consideri il caso in cui un sottoscrittore aggiunga un nuovo ordine con **OrderID** = 6 e due nuove righe nel **OrderItems** tabella **OrderItemID** = 10 e **OrderItemID** = 11 per **OrderID** = 6.  
  
 ![Record logico per tre tabelle con valori](../../../relational-databases/replication/merge/media/logical-records-04.gif "Record logico per tre tabelle con valori")  
  
 Se il processo di replica viene interrotta dopo il **ordini** riga per **OrderID** = 6 è stata completata, ma prima che il **OrderItems** 10 e 11 vengono completate e non vengono utilizzati record logici, il **OrderTotal** valore per **OrderID** = 6 non saranno coerenti con la somma del **OrderAmount** i valori per il **OrderItems** righe. Se vengono utilizzati record logici, il **ordini** riga per **OrderID** = 6 non viene eseguito il commit finché non correlato **OrderItems** le modifiche vengono replicate.  
  
 In uno scenario diverso, se vengono utilizzati i record logici e si esegue una query sulle tabelle mentre il processo di tipo merge sta applicando le modifiche, l'utente non vedrà le modifiche parzialmente replicate fino a quando non saranno tutte complete. Ad esempio, il processo di replica ha caricato la riga Orders per **OrderID** = 6, ma le query di un utente le tabelle prima che il processo di replica ha replicato il **OrderItems** righe, il **OrderTotal** valore non sarebbe uguale alla somma del **OrderAmount** valori. Se vengono utilizzati record logici, il **ordini** riga non sarà visibile fino a quando il **OrderItems** righe sono state completate e la transazione è stata eseguita come un'unità.  
  
### Applicazione della gestione dei conflitti a più di una tabella  
 Si consideri il caso in cui due Sottoscrittori dispongono del set di dati illustrato in precedenza:  
  
-   Un utente al primo sottoscrittore modifica il **OrderAmount** di **OrderItemID** 5 da 100 a 150 e **OrderTotal** di **OrderID** 3 da 200 a 250.  
  
-   Un utente al secondo sottoscrittore modifica il **OrderAmount** di **OrderItemID** 6 da 25 a 125 e **OrderTotal** di **OrderID** 3 da 200 a 300.  
  
 Se queste modifiche vengono replicate senza utilizzare record logici, le diverse **OrderTotal** valori provocherebbe un conflitto tra e solo uno di essi verrà replicato. Ma le modifiche non in conflitto nel **OrderItems** tabella verrà replicata senza entrare in conflitto, lasciando finale **OrderTotal** valori in uno stato incoerente rispetto al **OrderItems** righe. Se vengono utilizzati record logici in questo scenario, il **OrderItems** modifica associato perdita **ordini** Modifica tabella potrebbe inoltre essere annullato, back e finale **OrderTotal** valore deve corrispondere a un riepilogo accurato del **OrderItems** righe.  
  
 Per ulteriori informazioni sulle opzioni relative al rilevamento dei conflitti e la risoluzione con i record logici, vedere [rilevamento e risoluzione dei conflitti nei record logici](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md).  
  
## Considerazioni sull'utilizzo di record logici  
 Quando si utilizzano i record logici, tenere presenti le considerazioni seguenti:  
  
### Considerazioni generali  
  
-   È consigliabile che il numero di tabelle in un record logico sia il più basso possibile, ad esempio cinque tabelle o un numero inferiore.  
  
-   I record logici non possono fare riferimento a colonne con i tipi di dati seguenti:  
  
    -   **varchar (max)** e **nvarchar (max)**  
  
    -   **varbinary(max)**  
  
    -   **testo** e **ntext**  
  
    -   **image**  
  
    -   **XML**  
  
    -   **UDT (tipo definito dall'utente)**  
  
-   Le relazioni di chiavi esterne nelle tabelle pubblicate non possono essere definite mediante l'opzione CASCADE. Per ulteriori informazioni, vedere [CREATE TABLE & #40; Transact-SQL & #41;](../../../t-sql/statements/create-table-transact-sql.md) e [ALTER tabella & #40; Transact-SQL & #41;](../../../t-sql/statements/alter-table-transact-sql.md).  
  
-   Non è possibile aggiornare le colonne utilizzate nella clausola di relazione logica.  
  
-   La risoluzione dei conflitti personalizzata con gestori della logica di business o sistemi di risoluzione personalizzati non è supportata per gli articoli inclusi in un record logico.  
  
-   Se in una pubblicazione che include filtri con parametri vengono utilizzati record logici, è necessario inizializzare ogni Sottoscrittore con uno snapshot per la relativa partizione. Se si inizializza un Sottoscrittore con un altro metodo, l'agente di merge non verrà eseguito in modo corretto. Per altre informazioni, vedere [Snapshots for Merge Publications with Parameterized Filters](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
-   I conflitti a livello di record logici non vengono visualizzati nel Visualizzatore conflitti. Per visualizzare informazioni relative a questi conflitti, utilizzare le stored procedure di replica. Per ulteriori informazioni, vedere [visualizzare informazioni sul conflitto per le pubblicazioni di tipo Merge & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/view conflict information for merge publications.md).  
  
### Impostazioni di pubblicazione  
  
-   È necessario che la pubblicazione abbia un livello di compatibilità pari a 90RTM o superiore. Per ulteriori informazioni, vedere la sezione "Livello di compatibilità della pubblicazione" di [compatibilità con le versioni precedenti della replica](../../../relational-databases/replication/replication-backward-compatibility.md).  
  
-   È necessario che nella pubblicazione sia utilizzata la modalità snapshot nativa. Si tratta dell'impostazione predefinita a meno che non si esegua la replica in [!INCLUDE[ssEW](../../../includes/ssew-md.md)], che non supporta i record logici.  
  
-   La pubblicazione non consente la sincronizzazione tramite il Web. Per ulteriori informazioni sulla sincronizzazione Web, vedere [Web Synchronization for Merge Replication](../../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
-   Per utilizzare record logici in una pubblicazione filtrata:  
  
    -   È necessario utilizzare partizioni pre-calcolate. I requisiti delle partizioni pre-calcolate si applicano anche ai record logici. Per ulteriori informazioni, vedere [Ottimizza prestazioni filtro con parametri con le partizioni precalcolate](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md).  
  
    -   Non è possibile utilizzare filtri con parametri non sovrapposti. Per ulteriori informazioni, vedere la sezione "Impostazione 'opzioni di partizionamento'" di [i filtri di riga con parametri](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
-   Se la pubblicazione utilizza filtri di join, la **chiave univoca di join** proprietà deve essere impostata su **true** per tutti i filtri che sono coinvolti in relazioni tra record logici join. Per ulteriori informazioni, vedere [filtri Join](../../../relational-databases/replication/merge/join-filters.md).  
  
### Relazioni tra tabelle  
  
-   È necessario che le tabelle correlate tramite record logici presentino una relazione tra chiave primaria e chiave esterna.  
  
-   Non è possibile impostare l'opzione NOT FOR REPLICATION per i vincoli di chiave esterna.  
  
-   Le tabelle figlio possono avere solo una tabella padre.  
  
     Un database utilizzato per tenere traccia di classi e studenti potrebbe, ad esempio, avere una struttura simile alla seguente:  
  
     ![Tabella figlio con più di una tabella padre](../../../relational-databases/replication/merge/media/logical-records-03.gif "Tabella figlio con più di una tabella padre")  
  
     È possibile utilizzare un record logico per rappresentare le tre tabelle in questa relazione, perché le righe in **ClassMembers** non sono associati a una singola riga di chiave primaria. Le tabelle **classi** e **ClassMembers** potrebbero formare un record logico, così come le tabelle **ClassMembers** e **gli studenti**, ma non tutti e tre.  
  
-   La pubblicazione non può contenere relazioni circolari tra filtri join.  
  
     Utilizzo dell'esempio con le tabelle **clienti**, **ordini**, e **OrderItems**, non è possibile utilizzare record logici se il **ordini** tabella dispone di un vincolo di chiave esterna a cui fa riferimento il **OrderItems** tabella.  
  
## Effetti dei record logici sulle prestazioni  
 La funzionalità di record logici comporta alcuni costi relativi alle prestazioni. Se non vengono utilizzati record logici, l'agente di replica può elaborare contemporaneamente tutte le modifiche relative a un determinato articolo e poiché le modifiche vengono applicate riga per riga, i requisiti del log delle transazioni e di blocco necessari per l'applicazione di tali modifiche sono minimi.  
  
 Se vengono utilizzati record logici, è necessario che l'agente di merge elabori insieme le modifiche per ogni record logico completo. Questa operazione influisce sulla quantità di tempo necessaria per la replica delle righe da parte dell'agente di merge. Poiché, inoltre, tramite l'agente viene aperta una transazione separata per ogni record logico, i requisiti di blocco possono aumentare.  
  
## Vedere anche  
 [Opzioni degli articoli per la replica di tipo merge](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)  
  
  