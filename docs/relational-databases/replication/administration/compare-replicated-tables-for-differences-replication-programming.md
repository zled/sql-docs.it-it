---
title: "Confronto di tabelle replicate al fine di individuare le differenze (programmazione della replica) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "utilità tablediff"
  - "confronto di tabelle replicate"
ms.assetid: cd253a17-0c85-42b4-912c-690169ebe799
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Confronto di tabelle replicate al fine di individuare le differenze (programmazione della replica)
  La convalida degli articoli consente di determinare se i dati pubblicati per gli articoli di tabella nel server di pubblicazione e nel Sottoscrittore non sono identici, fattore che può indicare la mancanza di convergenza. Per ulteriori informazioni, vedere [convalidare i dati replicati](../../../relational-databases/replication/validate-replicated-data.md). La convalida restituisce tuttavia solo un risultato positivo o negativo e non fornisce informazioni sulle differenze specifiche tra le tabelle di origine e di destinazione. Il **tablediff** restituisce utilità prompt dei comandi dettagliate differenza di informazioni tra due tabelle e può inoltre generare un [!INCLUDE[tsql](../../../includes/tsql-md.md)] script per portare una sottoscrizione convergenti con i dati nel server di pubblicazione.  
  
> [!NOTE]  
>  Il **tablediff** utilità è supportata solo per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server.  
  
### Per confrontare le tabelle replicate al fine di individuare le differenze mediante tablediff  
  
1.  Dal prompt dei comandi in qualsiasi server in una topologia di replica, eseguire il [utilità tablediff](../../../tools/tablediff-utility.md). Specificare i parametri seguenti:  
  
    -   **-sourceserver** : nome del server in cui i dati sono noti sia corretto, in genere il server di pubblicazione.  
  
    -   **-sourcedatabase** : nome del database contenente i dati corretti.  
  
    -   **-sourcetable** : nome della tabella di origine per l'articolo da confrontare.  
  
    -   (Facoltativo) **-sourceschema** -proprietario dello schema della tabella di origine, se non lo schema predefinito.  
  
    -   (Facoltativo) **-sourceuser** e **- sourcepassword** quando si utilizza l'autenticazione di SQL Server per connettersi al server di pubblicazione.  
  
        > [!IMPORTANT]  
        >  Se possibile, usare l'autenticazione di Windows. Se è necessario utilizzare l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
    -   **-destinationserver** : nome del server in cui i dati vengono confrontati, generalmente un sottoscrittore.  
  
    -   **-destinationdatabase** : nome di un database da confrontare.  
  
    -   **-destinationtable** : nome della tabella da confrontare.  
  
    -   (Facoltativo) **-destinationschema** -proprietario dello schema della tabella di destinazione, se non lo schema predefinito.  
  
    -   (Facoltativo) **-destinationuser** e **- destinationpassword** quando si utilizza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per eseguire la connessione al sottoscrittore.  
  
        > [!IMPORTANT]  
        >  Se possibile, usare l'autenticazione di Windows. Se è necessario utilizzare l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
    -   (Facoltativo) Utilizzare **- c** per eseguire un confronto a livello di colonna.  
  
    -   (Facoltativo) Utilizzare **- q** per effettuare un rapido, riga numero e schema solo a confronto.  
  
    -   (Facoltativo) Specificare un nome file e percorso per **-o** per restituire i risultati in un file.  
  
    -   (Facoltativo) Specificare una tabella nel database di sottoscrizione in cui inserire i risultati per **-et**. Se la tabella esiste già, specificare **-dt** innanzitutto eliminare la tabella.  
  
    -   (Facoltativo) Utilizzare **-f** per generare un [!INCLUDE[tsql](../../../includes/tsql-md.md)] file correggere i dati nel Sottoscrittore in modo che corrispondano a quelli nel server di pubblicazione. Utilizzare **-df** per specificare il numero di [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzioni in ogni file.  
  
    -   (Facoltativo) Utilizzare **-rc** e **-ri** per specificare il numero di tentativi di un'operazione e l'intervallo tra tentativi.  
  
    -   (Facoltativo) Utilizzare **-strict** per imporre il confronto schema strict tra le tabelle di origine e di destinazione.  
  
## Vedere anche  
 [Convalida dei dati nel Sottoscrittore](../../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  