---
title: "Sicurezza agente di distribuzione | Microsoft Docs"
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
  - "sql13.rep.security.DA.f1"
helpviewer_keywords: 
  - "Sicurezza agente di distribuzione - finestra di dialogo"
ms.assetid: de40cc21-2e58-4464-9be7-b5b90c925e9b
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Sicurezza agente di distribuzione
  Il **sicurezza agente di distribuzione** la finestra di dialogo consente di specificare l'account di Windows con cui viene eseguito l'agente di distribuzione. L'agente di distribuzione viene eseguito nel server di distribuzione per le sottoscrizioni push e nel Sottoscrittore per le sottoscrizioni pull. Il [!INCLUDE[msCoName](../../includes/msconame-md.md)] account di Windows è detta anche il *account di processo*, poiché il processo dell'agente viene eseguito con questo account. Le opzioni aggiuntive disponibili in questa finestra di dialogo dipendono dalla modalità con cui si accede a tale finestra di dialogo:  
  
-   Se si accede alla finestra di dialogo dalla Creazione guidata nuova sottoscrizione, è possibile specificare il contesto in cui l'agente di distribuzione stabilisce le connessioni al Sottoscrittore (per le sottoscrizioni push) o al server di distribuzione (per le sottoscrizioni pull). È possibile stabilire la connessione tramite rappresentazione dell'account di Windows o nel contesto di un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'account specificato.  
  
-   Se la finestra di dialogo è accessibile dal **le proprietà della sottoscrizione** finestra di dialogo specificare il contesto in cui l'agente di distribuzione stabilisce le connessioni facendo clic sul pulsante delle proprietà (**...**) nella **connessione al sottoscrittore** o **connessione server di distribuzione** riga della finestra di dialogo. Per ulteriori informazioni sull'accesso di **le proprietà della sottoscrizione** la finestra di dialogo, vedere [visualizzare e modificare le proprietà di sottoscrizione Push](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) e come: [visualizzare e modificare le proprietà di sottoscrizione Pull](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
 Tutti gli account devono essere validi e per ogni account deve essere stata specificata la password corretta. Gli account e le password vengono convalidati solo dopo l'avvio dell'esecuzione di un agente.  
  
## Opzioni  
 **Account processo**  
 Consente di immettere un account di Windows utilizzato per l'esecuzione dell'agente di distribuzione:  
  
-   Per le sottoscrizioni push, l'account deve:  
  
    -   Appartenere almeno il **db_owner** ruolo predefinito del database nel database di distribuzione.  
  
    -   Essere un membro dell'elenco di accesso alla pubblicazione.  
  
    -   Disporre delle autorizzazioni di lettura per la condivisione snapshot.  
  
    -   Disporre delle autorizzazioni di lettura per la directory di installazione del provider OLE DB per il Sottoscrittore se la sottoscrizione riguarda un Sottoscrittore non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Per le sottoscrizioni pull, l'account deve essere almeno un membro del **db_owner** ruolo predefinito del database nel database di sottoscrizione.  
  
 Sono necessarie autorizzazioni aggiuntive nel caso in cui l'account di processo sia rappresentato durante l'attivazione delle connessioni. Vedere il **Connetti al server di distribuzione** e **Connetti al sottoscrittore** nelle sezioni seguenti.  
  
 **Account di processo** non è possibile specificare per le sottoscrizioni pull [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], poiché l'agente di distribuzione non vengono eseguite le istanze di [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].  
  
 **Password** e **Conferma Password**  
 Immettere la password per l'account di Windows.  
  
 **Connetti al server di distribuzione**  
 Per le sottoscrizioni push, le connessioni al server di distribuzione vengono sempre stabilite tramite rappresentazione dell'account specificato nel **account di processo** casella di testo.  
  
 Per le sottoscrizioni pull, selezionare se l'agente di distribuzione deve stabilire connessioni al server di distribuzione tramite rappresentazione dell'account specificato nella **account di processo** casella di testo o utilizzando un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account. Se si seleziona l'opzione per l'utilizzo di un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , immettere un account di accesso e una password di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  È consigliabile scegliere di rappresentare l'account di Windows anziché di utilizzare un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 L'account di Windows o l'account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzato per la connessione deve:  
  
-   Essere un membro del ruolo PAL.  
  
-   Disporre delle autorizzazioni di lettura per la condivisione snapshot.  
  
 **Connetti al Sottoscrittore**  
 Per le sottoscrizioni pull, le connessioni al sottoscrittore vengono sempre stabilite tramite rappresentazione dell'account specificato nel **account di processo** casella di testo.  
  
 Per le sottoscrizioni push le opzioni sono diverse per i Sottoscrittori [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sottoscrittori: selezionare se l'agente di distribuzione deve stabilire connessioni al sottoscrittore tramite rappresentazione dell'account specificato nella **account di processo** casella di testo o utilizzando un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account. Se si seleziona l'opzione per l'utilizzo di un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , immettere un account di accesso e una password di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    > [!NOTE]  
    >  È consigliabile scegliere di rappresentare l'account di Windows anziché di utilizzare un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     L'account di Windows o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account utilizzato per la connessione al Sottoscrittore deve essere almeno un membro del **db_owner** ruolo predefinito del database nel database di sottoscrizione.  
  
-   Per i Sottoscrittori non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], specificare l'account di accesso al database nel Sottoscrittore da utilizzare quando l'agente di distribuzione si connette al Sottoscrittore. L'account di accesso deve disporre di autorizzazioni sufficienti per creare oggetti nel database di sottoscrizione. Per ulteriori informazioni sulla configurazione non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sottoscrittori, vedere [creare una sottoscrizione per un sottoscrittore Non SQL Server](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md).  
  
 **Opzioni di connessione aggiuntive**  
 Solo per Sottoscrittori non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specificare le opzioni di connessione per il Sottoscrittore sotto forma di una stringa di connessione (Oracle non richiede opzioni aggiuntive). Le opzioni devono essere separate dal punto e virgola. L'esempio seguente illustra una stringa di connessione IBM DB2 (le interruzioni di riga sono state inserite per favorire la leggibilità):  
  
```  
Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
Persist Security Info=False;Connection Pooling=True;  
```  
  
 La maggior parte delle opzioni nella stringa è specifica per il server DB2 configurato, ma è necessario che l'opzione **Process Binary as Character** sia sempre impostata su **False**. È necessario specificare un valore per l'opzione **Initial Catalog** per identificare il database di sottoscrizione. Per ulteriori informazioni, vedere [nei Sottoscrittori DB2 IBM](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
## Vedere anche  
 [Gestione degli account di accesso e delle password nella replica](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Panoramica degli agenti di replica](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  