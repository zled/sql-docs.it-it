---
title: "Preparare SQL Server per CDC | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "prepSqlSrv"
ms.assetid: 20b51dbf-a545-4234-87ae-4228268a0fb2
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Preparare SQL Server per CDC
  Il servizio Oracle CDC richiede che tutte le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione contengano il database MSXDBCDC. Per creare questo database utilizzare l'azione Prepare SQL Server in CDC Service Configuration Console. Verrà creato uno script speciale eseguito per creare le tabelle, le stored procedure e altri artefatti obbligatori per il database. Questa attività viene eseguita una volta sola per ogni istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione.  
  
 Per ulteriori informazioni sul database MSXDBCDC, vedere Database MSXDBCDC.  
  
 In CDC Service Configuration Console, fare clic su **Prepare SQL Server** (Prepara SQL Server). Se questa opzione non è disponibile, verificare che nel riquadro sinistro della console sia selezionata l'opzione **Local CDC Services** (Servizi CDC locali).  
  
## Opzioni  
  
### Nome server  
 Digitare il nome del server in cui si trova [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### Autenticazione  
 Selezionare una delle opzioni seguenti:  
  
-   **Autenticazione di Windows**  
  
-   **Autenticazione di SQL Server**: se si seleziona questa opzione, è necessario digitare **Nome utente** e **Password** per l'utente nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui si esegue la connessione.  
  
 Per preparare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per Oracle CDC, l'account di accesso deve disporre di autorizzazioni di scrittura per il database MSXDBCDC. Immettere le credenziali per un account di accesso che dispone di autorizzazioni per il database MSXDBCDC, ad esempio un membro del ruolo `sysasmin` .  
  
### Opzioni  
 Fare clic sulla freccia per visualizzare le opzioni disponibili da configurare. È possibile scegliere di non modificare il valore predefinito per queste opzioni. Sono disponibili le opzioni seguenti:  
  
-   **Timeout connessione**: digitare il tempo, in secondi, di attesa del servizio CDC per Oracle per la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima che si verifichi un errore di timeout. Il valore predefinito è **15**.  
  
-   **Timeout esecuzione**: digitare il tempo, in secondi, di attesa del servizio Windows Oracle CDC per l'esecuzione di un comando prima che si verifichi un errore di timeout. Il valore predefinito è **30**.  
  
-   **Encrypt Connection**: selezionare **Encrypt Connection** per la comunicazione tra il servizio Oracle CDC e l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione tramite una connessione crittografata.  
  
-   **Advanced**: digitare eventuali proprietà di connessione aggiuntive, se necessario.  
  
### View Script  
 Fare clic su **Visualizza script** per visualizzare una versione di sola lettura dello script di impostazione. Se necessario, un amministratore di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può copiare questo script nella console di gestione di SQL Server per modificarlo. Per altre informazioni sulla preparazione di SQL Server per lo script, vedere [Preparare SQL Server per lo script di visualizzazione di Oracle CDC](../../integration-services/change-data-capture/prepare-sql-server-for-oracle-cdc-view-script.md).  
  
## Vedere anche  
 [Procedura di utilizzo dei servizi CDC](../../integration-services/change-data-capture/how-to-work-with-cdc-services.md)   
 [Procedura di preparazione di SQL Server per CDC](../../integration-services/change-data-capture/how-to-prepare-sql-server-for-cdc.md)  
  
  