---
title: "Visualizzazione dello stato di un database con mirroring (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "stati [SQL Server], mirroring del database"
  - "mirroring del database [SQL Server], stati"
ms.assetid: 544f4194-253e-4c57-96ca-31c16301434f
caps.latest.revision: 25
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 25
---
# Visualizzazione dello stato di un database con mirroring (SQL Server Management Studio)
  Durante una sessione di mirroring del database, è possibile visualizzare lo stato nella pagina **Mirroring** della finestra di dialogo **Proprietà database**.  
  
### Per visualizzare lo stato di una sessione di mirroring del database  
  
1.  Dopo aver attivato la connessione all'istanza del server principale, in Esplora oggetti fare clic sul nome del server per espandere l'albero.  
  
2.  Espandere **Database**e selezionare il database per il mirroring.  
  
3.  Fare clic con il pulsante destro del mouse sul database, scegliere **Attività** e quindi fare clic su **Server mirror**. Viene visualizzata la pagina **Mirroring** della finestra di dialogo **Proprietà database** .  
  
4.  In seguito all'avvio del mirroring, nel pannello **Stato** verrà visualizzato lo stato della sessione di mirroring del database nel momento in cui si è selezionata la pagina **Mirroring** o si è fatto clic sul pulsante **Aggiorna**. Gli stati possibili sono indicati di seguito:  
  
    |Stati|Spiegazione|  
    |------------|-----------------|  
    |\< vuoto>|Non esiste alcuna sessione di mirroring del database e non vi sono attività da segnalare nella pagina **Mirroring**.|  
    |In sospeso|Il database principale è in esecuzione, ma non viene inviato alcun log al server mirror. La copia mirror del database non è disponibile.|  
    |Nessuna connessione|L'istanza del server principale non può connettersi ai partner o all'istanza del server di controllo del mirroring (se disponibile).|  
    |Sincronizzazione in corso|La posizione del contenuto del database mirror precede quella del database principale. L'istanza del server principale invia record di log all'istanza del server mirror, che applica le modifiche al database mirror per eseguirne il rollforward.<br /><br /> All'avvio della sessione di mirroring del database, i database mirror e principale sono in stato di sincronizzazione.|  
    |Failover|Nell'istanza del server principale è iniziato un failover manuale (inversione di ruolo), che non è stato ancora accettato dal server mirror.|  
    |Sincronizzato|Il database mirror contiene gli stessi dati del database principale. I failover manuale e automatico sono possibili *solo* in stato sincronizzato.|  
  
## Vedere anche  
 [Stati di mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
  