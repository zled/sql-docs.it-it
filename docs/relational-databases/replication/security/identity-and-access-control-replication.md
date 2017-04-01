---
title: "Controllo di identit&#224; e accesso (replica) | Microsoft Docs"
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
  - "controlli di accesso [replica di SQL Server]"
  - "sicurezza [replica di SQL Server], controllo di identità e accesso"
  - "autenticazione [replica di SQL Server]"
  - "identità [replica]"
ms.assetid: 4da0e793-1ee4-4f69-a80b-45c6732a238d
caps.latest.revision: 8
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 8
---
# Controllo di identit&#224; e accesso (replica)
  L'autenticazione è il processo mediante il quale un'entità (in genere un computer in questo contesto) verifica che un'altra entità, detta anche un *principale*, (in genere un altro computer o utente), sia che essa dichiara di essere. L'autorizzazione è il processo che consente di concedere a un'entità autenticata l'accesso alle risorse, ad esempio un file nel file system o una tabella in un database.  
  
 La sicurezza della replica si basa sull'autenticazione e sull'autorizzazione per controllare l'accesso agli oggetti di database replicati e ai computer e agli agenti coinvolti nell'elaborazione della replica. Questo processo viene eseguito mediante tre meccanismi:  
  
-   Sicurezza degli agenti  
  
     Il modello di sicurezza degli agenti di replica garantisce un controllo dettagliato sugli account utilizzati per eseguire gli agenti e stabilire connessioni. Per informazioni dettagliate sul modello di sicurezza dell'agente, vedere [modello di sicurezza dell'agente di replica](../../../relational-databases/replication/security/replication-agent-security-model.md). Per informazioni sull'impostazione account di accesso e password per gli agenti, vedere [gestire account di accesso e password nella replica](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md).  
  
-   Ruoli di amministrazione  
  
     Verificare che vengano utilizzati i ruoli appropriati del server e del database per la configurazione, la manutenzione e l'elaborazione della replica. Per ulteriori informazioni, vedere [requisiti del ruolo di sicurezza per la replica](../../../relational-databases/replication/security/security-role-requirements-for-replication.md).  
  
-   Elenco di accesso alla pubblicazione  
  
     Concedere l'accesso alle pubblicazioni tramite l'elenco di accesso alla pubblicazione, che funziona in maniera analoga a un elenco di controllo di accesso [!INCLUDE[msCoName](../../../includes/msconame-md.md)]. Quando un Sottoscrittore si connette al server di pubblicazione o al server di distribuzione e richiede l'accesso a una pubblicazione, le informazioni di autenticazione passate dall'agente vengono controllate in base all'elenco di accesso alla pubblicazione. Per ulteriori informazioni e procedure consigliate per la pubblicazione, vedere [proteggere il server di pubblicazione](../../../relational-databases/replication/security/secure-the-publisher.md).  
  
## Applicazione di filtri ai dati pubblicati  
 Oltre a utilizzare l'autenticazione e l'autorizzazione per controllare l'accesso ai dati e agli oggetti replicati, la replica include due opzioni per controllare quali dati rendere disponibili nel Sottoscrittore: applicazione di filtri a colonne e a righe. Per ulteriori informazioni sull'applicazione di filtri, vedere [filtrare i dati pubblicati](../../../relational-databases/replication/publish/filter-published-data.md).  
  
 Quando si definisce un articolo, è possibile pubblicare solo le colonne necessarie per la pubblicazione e omettere quelle superflue o che contengono dati riservati. Ad esempio, quando si pubblica il **cliente** tabella dal database Adventure Works per i venditori nel campo, è possibile omettere il **AnnualSales** colonna, che può essere rilevante solo per i dirigenti dell'azienda.  
  
 L'applicazione di filtri ai dati pubblicati consente di limitare l'accesso ai dati e di specificare i dati da rendere disponibili nel Sottoscrittore. Ad esempio, è possibile filtrare il **cliente** tabella in modo che i partner aziendali ricevano solo informazioni relative ai clienti il cui **ShareInfo** colonna ha un valore di "Sì". Nella replica di tipo merge è necessario tenere in considerazione alcuni aspetti relativi alla sicurezza se si utilizza un filtro con parametri che include HOST_NAME(). Per ulteriori informazioni, vedere la sezione "Applicazione di filtri con HOST_NAME ()" in [i filtri di riga con parametri](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
## Vedere anche  
 [Sicurezza e protezione & #40; Replica & #41;](../../../relational-databases/replication/security/security-and-protection-replication.md)   
 [Cenni preliminari sulla sicurezza & #40; Replica & #41;](../../../relational-databases/replication/security/security-overview-replication.md)   
 [Rischio e attenuazione delle vulnerabilità e 40 #; Replica & #41;](../../../relational-databases/replication/security/threat-and-vulnerability-mitigation-replication.md)  
  
  