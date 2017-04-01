---
title: "Impostazione dell&#39;account del servizio dell&#39;Utilit&#224; di avvio del daemon di filtri full-text | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ricerca full-text [SQL Server], account del servizio Utilità di avvio del daemon filtri full-text (MSSQLFDLauncher)"
  - "utilità di avvio di FDHOST (MSSQLFDLauncher) [SQL Server]"
ms.assetid: 3ab1d101-7ae0-488f-9b57-468e2517b737
caps.latest.revision: 50
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 49
---
# Impostazione dell&#39;account del servizio dell&#39;Utilit&#224; di avvio del daemon di filtri full-text
  In questo argomento viene illustrato come impostare l'account del servizio Utilità di avvio del daemon filtri full-text di SQL (MSSQLFDLauncher) utilizzando Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il servizio Utilità di avvio del daemon filtri full-text di SQL viene usato dalla ricerca full-text ssNoVersion per avviare il processo host del daemon di filtri che gestisce il word breaking e l'applicazione di filtri per la ricerca full-text. Per utilizzare la ricerca full-text, questo servizio deve essere in esecuzione.  
  
 Il servizio Utilità di avvio del daemon filtri full-text di SQL è un servizio specifico dell'istanza associato a una determinata istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Tale servizio propaga le informazioni sull'account del servizio a ogni processo host del daemon di filtri.  
  
##  <a name="TOP"></a> Argomenti della sezione  
  
-   [Consigli relativi alla sicurezza](#rec)  
  
-   [Impostazione dell'account di servizio](#setting)  
  
-   [Se il servizio Utilità di avvio del daemon filtri full-text di SQL non viene avviato](#error)  
  
##  <a name="setting"></a> Impostazione dell'account di servizio  
  
#### Per impostare l'account del servizio Utilità di avvio del daemon filtri full-text di SQL per la ricerca full-text  
  
1.  Fare clic sul menu **Start** , scegliere **Tutti i programmi**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Strumenti di configurazione**e quindi **Gestione configurazione SQL Server**.  
  
2.  In **Gestione configurazione SQL Server**, fare clic su **Servizi di SQL Server**, fare clic con il pulsante destro del mouse su **Utilità di avvio del daemon filtri full-text di SQL (***nome istanza***)**, quindi scegliere **Proprietà**.  
  
3.  Fare clic sulla scheda **Accesso** della finestra di dialogo, quindi selezionare o immettere l'account con il quale eseguire ogni processo creato dal servizio Utilità di avvio del daemon filtri full-text di SQL.  
  
4.  Dopo avere chiuso la finestra di dialogo, fare clic su **Riavvia** per riavviare il servizio Utilità di avvio del daemon filtri full-text di SQL.  
  
 [Argomenti della sezione](#TOP)  
  
##  <a name="error"></a> Se il servizio Utilità di avvio del daemon filtri full-text di SQL non viene avviato  
 Se il servizio Utilità di avvio del daemon filtri full-text di SQL non viene avviato, è possibile che si siano verificati uno o più dei problemi elencati di seguito:  
  
-   La password associata all'account del servizio Utilità di avvio del daemon filtri full-text di SQL è scaduta.  
  
     Se si utilizza un account utente locale per il servizio Utilità di avvio del daemon filtri full-text di SQL e la password scade, è necessario:  
  
    1.  Impostare una nuova password di Windows per l'account.  
  
    2.  Aggiornare il servizio Utilità di avvio del daemon filtri full-text di SQL per utilizzare la nuova password in Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   La password o l'account utente dell'account del servizio non è corretto.  
  
     Il servizio Utilità di avvio del daemon filtri full-text di SQL potrebbe tentare di accedere con un account utente e una password non corretti. Seguire le procedure indicate in precedenza per verificare che l'account utente per il servizio non sia stato modificato.  
  
-   L'account utilizzato per accedere al servizio non dispone di privilegi.  
  
     È possibile che sia in uso un account che non dispone di privilegi di accesso nel computer in cui è installata l'istanza del server. Assicurarsi di accedere con un account che disponga di diritti e autorizzazioni utente nel computer locale.  
  
-   Un'altra istanza della stessa named pipe è già in esecuzione.  
  
     Il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] funge da server named pipe per il client del servizio Utilità di avvio del daemon filtri full-text di SQL. Se la named pipe è già stata creata da un altro processo prima dell'avvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], viene registrato un errore nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e nel registro eventi di Windows e la ricerca full-text non è disponibile.  Individuare il processo o l'applicazione che tenta di utilizzare la stessa named pipe e arrestare l'applicazione.  
  
-   Il servizio Utilità di avvio del daemon filtri full-text di SQL non è configurato correttamente.  
  
     Il servizio potrebbe non essere configurato correttamente nel computer locale.  
  
     Se la funzionalità delle named pipe è stata disabilitata nel computer locale o se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è stato configurato per l'utilizzo di una named pipe diversa da quella predefinita, il servizio Utilità di avvio del daemon filtri full-text di SQL potrebbe non essere avviato.  
  
-   Il gruppo di servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non dispone dell'autorizzazione necessaria per avviare il servizio Utilità di avvio del daemon filtri full-text di SQL.  
  
     Durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], al gruppo di servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene concessa l'autorizzazione predefinita per gestire, eseguire query sul e avviare il servizio Utilità di avvio del daemon filtri full-text di SQL. Se le autorizzazioni del gruppo di servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'account del servizio Utilità di avvio del daemon filtri full-text sono state rimosse dopo l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], questo servizio non viene avviato e la ricerca full-text viene disabilitata. Assicurarsi che il gruppo di servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abbia le autorizzazioni necessarie per l'account del servizio Utilità di avvio del daemon filtri full-text di SQL.  
  
 [Argomenti della sezione](#TOP)  
  
## Vedere anche  
 [Procedure per la gestione dei servizi &#40;Gestione configurazione SQL Server&#41;](../Topic/Managing%20Services%20How-to%20Topics%20\(SQL%20Server%20Configuration%20Manager\).md)   
 [Aggiornamento della ricerca full-text](../../relational-databases/search/upgrade-full-text-search.md)  
  
  