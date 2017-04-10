---
title: "Avvio dell&#39;utilit&#224; sqlcmd | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
caps.latest.revision: 41
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Avvio dell&#39;utilit&#224; sqlcmd
    
> [!NOTE]  
>  La modalità di autenticazione predefinita per **sqlcmd** è l'autenticazione di Windows. Per usare l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario specificare un nome utente e una password con le opzioni **-U** e **-P**.  
  
> [!NOTE]  
>  Per impostazione predefinita, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] viene installato come istanza denominata **sqlexpress**.  
  
### Avviare l'utilità sqlcmd e connettersi a un'istanza predefinita di SQL Server  
  
1.  Fare clic sul menu **Start** e scegliere **Esegui**. Nella casella **Apri** digitare **cmd** e quindi fare clic su **OK** per aprire una finestra del prompt dei comandi. Se non ci si è mai connessi a questa istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], potrebbe essere necessario configurare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in modo che accetti le connessioni.  
  
2.  Al prompt dei comandi digitare **sqlcmd**.  
  
3.  Premere INVIO.  
  
     Verrà quindi stabilita una connessione trusted all'istanza predefinita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in esecuzione nel computer in uso.  
  
     **1>** rappresenta il prompt di **sqlcmd** che indica il numero di riga. Il numero viene aumentato di un'unità ogni volta che si preme INVIO.  
  
4.  Per terminare la sessione di **sqlcmd**, digitare **EXIT** al prompt di **sqlcmd**.  
  
### Avviare l'utilità sqlcmd e connettersi a un'istanza denominata di SQL Server  
  
1.  Aprire una finestra del prompt dei comandi e digitare **sqlcmd -S***server\nomeIstanza*. Sostituire *server\nomeIstanza* con il nome del computer e dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui ci si vuole connettere.  
  
2.  Premere INVIO.  
  
     Il prompt di **sqlcmd** (1>) indica che si è connessi all'istanza specificata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  Le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] immesse vengono archiviate in un buffer. Vengono eseguite in batch quando viene rilevato il comando GO.  
  
## Vedere anche  
 [Esecuzione di file script Transact-SQL mediante sqlcmd](../../relational-databases/scripting/run-transact-sql-script-files-using-sqlcmd.md)  
  
  