---
title: "Scadenza e disattivazione delle sottoscrizioni | Microsoft Docs"
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
  - "database di distribuzione [replica di SQL Server], periodo di memorizzazione per la distribuzione"
  - "sottoscrizioni [replica di SQL Server], scadenza"
  - "pubblicazioni [replica di SQL Server], periodi di memorizzazione per la distribuzione"
  - "scadenza [replica di SQL Server]"
  - "periodi di memorizzazione [replica di SQL Server]"
  - "periodi di memorizzazione della pubblicazione"
  - "periodo di memorizzazione per la distribuzione"
  - "sottoscrizioni [replica di SQL Server], disattivazione"
  - "disattivazione di sottoscrizioni"
ms.assetid: 4d03f5ab-e721-4f56-aebc-60f6a56c1e07
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# Scadenza e disattivazione delle sottoscrizioni
  Le sottoscrizioni possono essere disattivate o scadere se non vengono sincronizzate entro un determinato *periodo di memorizzazione*. Vengono eseguite azioni diverse a seconda del tipo di replica e del periodo di memorizzazione scaduto.  
  
 Per impostare periodi di conservazione, vedere [impostare il periodo di scadenza per le sottoscrizioni](../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md), [impostare il periodo di memorizzazione della distribuzione per le pubblicazioni transazionali & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/set distribution retention period for transactional publications.md), e [configurare la pubblicazione e distribuzione](../../relational-databases/replication/configure-publishing-and-distribution.md).  
  
## Replica transazionale  
 La replica transazionale utilizza il periodo di memorizzazione massimo per la distribuzione (il **@max_distretention** parametro [sp_adddistributiondb & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)) e il periodo di memorizzazione della pubblicazione (il **@retention** parametro [sp_addpublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)):  
  
-   Se una sottoscrizione non è sincronizzata entro il periodo di memorizzazione massimo per la distribuzione (valore predefinito è 72 ore) e sono state apportate modifiche nel database di distribuzione che non sono state recapitate al sottoscrittore, la sottoscrizione verrà contrassegnata come disattivata dal **pulizia della distribuzione** processo eseguito nel server di distribuzione. La sottoscrizione deve essere reinizializzata.  
  
-   Se una sottoscrizione non è sincronizzata entro il periodo di memorizzazione della pubblicazione (valore predefinito è 336 ore), la sottoscrizione scade e viene eliminata dal **sottoscrizione scaduta pulizia** processo eseguito nel server di pubblicazione. La sottoscrizione deve essere ricreata e sincronizzata.  
  
     Se una sottoscrizione push scade, viene completamente rimossa, a differenza delle sottoscrizioni pull, che devono essere eliminate nel Sottoscrittore. Per ulteriori informazioni, vedere [eliminare una sottoscrizione Pull](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
## Replica di tipo merge  
 Replica di tipo merge utilizza il periodo di memorizzazione della pubblicazione (il **@retention** e **@retention_period_unit** parametri di [sp_addmergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)). Se una sottoscrizione è scaduta, è necessario reinizializzarla, poiché i relativi metadati vengono rimossi. Le sottoscrizioni che non vengono reinizializzate vengono rimosse mediante il **sottoscrizione scaduta pulizia** processo eseguito nel server di pubblicazione. Per impostazione predefinita, questo processo viene eseguito ogni giorno e rimuove tutte le sottoscrizioni push che non sono state sincronizzate per il doppio della durata del periodo di memorizzazione per la pubblicazione. Esempio:  
  
-   Se una pubblicazione ha un periodo di memorizzazione di 14 giorni, una sottoscrizione può scadere se non è stata sincronizzata entro 14 giorni.  
  
     Se il server di pubblicazione è in esecuzione [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] o versione successiva e l'agente per la sottoscrizione da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] o versione successiva, una sottoscrizione scade solo se sono state apportate modifiche ai dati nella partizione della sottoscrizione. Ad esempio, si supponga che un Sottoscrittore riceva dati relativi solo ai clienti residenti in Germania. Se il periodo di memorizzazione impostato è pari 14 giorni, la sottoscrizione scade il 14° giorno solo se sono state apportate modifiche ai dati dei clienti tedeschi negli ultimi 14 giorni.  
  
-   È possibile reinizializzare la sottoscrizione da 14 a 27 giorni dopo l'ultima sincronizzazione.  
  
-   28 giorni dopo l'ultima sincronizzazione, la sottoscrizione viene rimossa mediante il **sottoscrizione scaduta pulizia** processo. Se una sottoscrizione push scade, viene completamente rimossa, a differenza delle sottoscrizioni pull, che devono essere eliminate nel Sottoscrittore. Per ulteriori informazioni, vedere [eliminare una sottoscrizione Pull](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
### Considerazioni sull'impostazione del periodo di memorizzazione per la pubblicazione per le pubblicazioni di tipo merge  
 Tenere sempre presenti le considerazioni seguenti nell'impostazione del periodo di memorizzazione per le pubblicazioni di tipo merge:  
  
-   Il periodo di memorizzazione per le pubblicazioni di tipo merge ha un periodo di prova di 24 ore per adattarsi ai Sottoscrittori dei diversi fusi orari. Se, ad esempio, si imposta un periodo di memorizzazione di un giorno, il periodo di memorizzazione effettivo sarà di 48 ore.  
  
-   La pulizia dei metadati di replica di tipo merge dipende dal periodo di memorizzazione per la pubblicazione:  
  
    -   La replica non è in grado di eliminare i metadati dei database di pubblicazione e sottoscrizione prima della scadenza del periodo di memorizzazione. Quando si imposta un valore elevato per il periodo di memorizzazione, verificare che non sia tale da avere effetti negativi sulle prestazioni della replica. Se si prevede che la sincronizzazione di tutti i Sottoscrittori verrà eseguita regolarmente entro tale periodo di tempo, è consigliabile specificare un valore inferiore.  
  
    -   È possibile specificare che le sottoscrizioni non scadono mai (il valore 0 per **@retention**), ma è consigliabile non utilizzare questo valore, poiché i metadati non possono essere puliti.  
  
-   Il periodo di memorizzazione per i server di ripubblicazione deve essere impostato su un valore uguale o minore del periodo di memorizzazione impostato nel server di pubblicazione originale. Impostare lo stesso periodo di memorizzazione delle pubblicazioni per tutti i server di pubblicazione e i relativi partner di sincronizzazione alternativi. L'impostazione di periodi di memorizzazione diversi potrebbe causare la non convergenza dei dati. Se è necessario modificare il periodo di memorizzazione della pubblicazione, reinizializzare manualmente il Sottoscrittore per evitare la non convergenza dei dati.  
  
-   Se, dopo la pulizia dei metadati, si incrementa il periodo di memorizzazione della pubblicazione e una sottoscrizione tenta di eseguire il merge con il server di pubblicazione (in cui i metadati sono già stati eliminati), a causa dell'incremento del periodo di memorizzazione la sottoscrizione non scadrà. Tuttavia, il server di pubblicazione non dispone di metadati sufficienti per scaricare le modifiche al Sottoscrittore e si avrà pertanto una situazione di non convergenza.  
  
## Vedere anche  
 [Reinizializzare le sottoscrizioni](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Amministrazione dell'agente di replica](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  