---
title: "Convalida dei dati replicati | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "convalida diretta di dati [replica di SQL Server]"
  - "amministrazione della replica, convalida dei dati"
  - "replica [SQL Server], convalida dei dati"
  - "transactional replication, validating data"
  - "convalida di dati"
  - "convalida di dati di replica di tipo merge [replica di SQL Server]"
  - "convalida di dati di replica di tipo merge [replica di SQL Server], informazioni"
  - "convalida di dati replicati"
ms.assetid: f7500a2b-61cb-41b5-816d-27609a6c58e7
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# Convalida dei dati replicati
  La replica transazionale e la replica di tipo merge consentono di verificare che i dati presenti nel Sottoscrittore corrispondano ai dati nel server di pubblicazione. La convalida può essere eseguita per sottoscrizioni specifiche o per tutte le sottoscrizioni di una pubblicazione. Specificare uno dei tipi seguenti di convalida dei dati, che verrà eseguita dall'agente di distribuzione o dall'agente di merge alla successiva sincronizzazione:  
  
-   Conteggio delle sole righe. Questo tipo di convalida verifica se la tabella nel Sottoscrittore ha lo stesso numero di righe della tabella nel server di pubblicazione, ma non verifica che il contenuto delle righe corrisponda. La convalida del conteggio delle righe è un controllo non approfondito che consente comunque di evidenziare eventuali problemi dei dati.  
  
-   Conteggio delle righe e checksum binario. Oltre al conteggio delle righe nel server di pubblicazione e nel Sottoscrittore, viene calcolato il checksum di tutti i dati tramite lo specifico algoritmo di checksum. In caso di esito negativo durante il conteggio delle righe il checksum non viene eseguito.  
  
 Oltre a verificare che i dati nel Sottoscrittore corrispondano ai dati nel server di pubblicazione, la replica di tipo merge consente di verificare che i dati vengano partizionati correttamente per ogni Sottoscrittore. Per ulteriori informazioni, vedere [convalidare le informazioni di partizione per un sottoscrittore di tipo Merge](../../relational-databases/replication/validate-partition-information-for-a-merge-subscriber.md).  
  
 **Per convalidare i dati**  
  
 Per convalidare tutti gli articoli di una sottoscrizione, utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], stored procedure o Replication Management Objects (RMO). Per altre informazioni, vedere [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md). Per convalidare singoli articoli di pubblicazioni snapshot e transazionali, è necessario utilizzare stored procedure.  
  
## Risultati della convalida dei dati  
 Al termine della convalida nell'agente di distribuzione o nell'agente di merge vengono registrati messaggi relativi all'esito positivo o negativo dell'operazione. Non vengono specificate le righe con esito negativo. È possibile visualizzare tali messaggi in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], Monitoraggio replica e nelle tabelle di sistema di replica. Nell'argomento elencato sopra vengono illustrate le procedure di esecuzione della convalida e di visualizzazione dei risultati.  
  
 Per gestire gli errori di convalida, considerare quanto segue:  
  
-   Configurare l'avviso di replica denominato **replica: sottoscrittore non supera la convalida dei dati** in modo da ricevere una notifica dell'errore. Per ulteriori informazioni, vedere [Configura avvisi di replica predefiniti & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/administration/configure-predefined-replication-alerts-sql-server-management-studio.md).  
  
-   L'errore di convalida rappresenta un problema per l'applicazione utilizzata? Se sì, aggiornare manualmente i dati in modo che siano sincronizzati oppure reinizializzare la sottoscrizione:  
  
    -   Dati possono essere aggiornati mediante il [utilità tablediff](../../tools/tablediff-utility.md). Per ulteriori informazioni sull'utilizzo di questa utilità, vedere [confrontare le tabelle replicate per differenze & #40; Programmazione della replica & #41;](../../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md).  
  
    -   Per ulteriori informazioni sulla reinizializzazione, vedere [reinizializzare le sottoscrizioni](../../relational-databases/replication/reinitialize-subscriptions.md).  
  
## Considerazioni sulla convalida dei dati  
 Durante la convalida dei dati è opportuno considerare gli aspetti seguenti:  
  
-   Prima di eseguire la convalida dei dati è necessario arrestare tutte le attività di aggiornamento nei Sottoscrittori. Non è necessario arrestare l'eventuale aggiornamento nel server di pubblicazione durante la convalida.  
  
-   Poiché la convalida di set di dati estesi mediante checksum e checksum binari può richiedere quantità elevate di risorse di elaborazione, è opportuno pianificare la convalida in modo che venga eseguita nei periodi di attività minore nei server utilizzati per la replica.  
  
-   La replica convalida soltanto le tabelle e non verifica che gli articoli solo schema, ad esempio le stored procedure, presenti nel server di pubblicazione e nel Sottoscrittore corrispondano.  
  
-   Il checksum binario può essere utilizzato per qualsiasi tabella pubblicata. Non è possibile convalidare mediante il calcolo del checksum tabelle con filtri colonne o strutture di tabelle logiche con offset di colonna diversi, a causa di istruzioni di tipo ALTER TABLE tramite cui vengono eliminate o aggiunte colonne.  
  
-   Convalida della replica utilizza il **checksum** e **binary_checksum** funzioni. Per informazioni sul comportamento, vedere  [CHECKSUM & #40; Transact-SQL & #41;](../../t-sql/functions/checksum-transact-sql.md) e [BINARY_CHECKSUM & #40; Transact-SQL & #41;](../../t-sql/functions/binary-checksum-transact-sql.md).  
  
-   La convalida eseguita mediante checksum o checksum binario può segnalare erroneamente un problema se nel Sottoscrittore vi sono tipi di dati diversi rispetto al server di pubblicazione. Ciò può verificarsi se si effettua una delle operazioni indicate di seguito.  
  
    -   Impostazione esplicita delle opzioni per lo schema per l'esecuzione del mapping dei tipi di dati per versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Impostazione del livello di compatibilità della pubblicazione per una pubblicazione di tipo merge su una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], qualora le tabelle pubblicate contengano uno o più tipi di dati di cui è necessario eseguire il mapping per questa versione.  
  
    -   Inizializzazione manuale di una sottoscrizione, in caso di utilizzo di tipi di dati diversi nel Sottoscrittore.  
  
-   Le convalide mediante calcoli del checksum e checksum binario non sono supportate per la replica transazionale di sottoscrizioni trasformabili.  
  
-   La convalida non è supportata per i dati replicati in Sottoscrittori non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Funzionamento della convalida dei dati  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convalida i dati calcolando un conteggio delle righe o un valore di checksum nel server di pubblicazione e quindi confrontare i valori per il conteggio delle righe o checksum calcolato nel Sottoscrittore. Viene calcolato un valore per l'intera tabella di pubblicazione e viene calcolato un valore per l'intera tabella di sottoscrizione, ma i dati in **testo**, **ntext**, o **immagine** colonne non è incluso nei calcoli.  
  
 Durante l'esecuzione del calcolo vengono attivati temporaneamente i blocchi condivisi sulle tabelle per le quali viene eseguito il conteggio delle righe o il calcolo del checksum. Il calcolo viene comunque completato e i blocchi condivisi vengono subito rimossi.  
  
 Quando si utilizzano valori checksum binari, il controllo di ridondanza ciclico (CRC) a 32 bit viene eseguito su ogni colonna anziché sulla riga fisica di una pagina di dati. Le colonne possono essere pertanto ordinate fisicamente in qualsiasi modo nella pagina di dati e al medesimo tempo ottenere lo stesso CRC per la riga. La convalida mediante checksum binario può essere utilizzata quando alla pubblicazione sono applicati filtri di riga o di colonna.  
  
## Vedere anche  
 [Procedure consigliate per l'amministrazione della replica](../../relational-databases/replication/administration/best-practices-for-replication-administration.md)  
  
  