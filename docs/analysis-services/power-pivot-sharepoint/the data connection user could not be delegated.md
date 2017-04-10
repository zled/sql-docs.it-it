---
title: "Per la connessione dati viene utilizzata l&#39;autenticazione di Windows e le credenziali utente non possono essere delegate. Impossibile aggiornare le connessioni seguenti: Dati PowerPivot | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d2006df1-d244-4786-b272-49d8996cc88c
caps.latest.revision: 7
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Per la connessione dati viene utilizzata l&#39;autenticazione di Windows e le credenziali utente non possono essere delegate. Impossibile aggiornare le connessioni seguenti: Dati PowerPivot
  Per le cartelle di lavoro di Excel contenenti dati di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], Excel Services restituisce questo errore se non riesce a connettersi a un'istanza del server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in SharePoint.  
  
## Dettagli  
  
|||  
|-|-|  
|Applicabile a|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint|  
|Versione prodotto|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Causa|Errore di connessione nel tentativo di utilizzare un provider di dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].|  
|Testo del messaggio|Per la connessione dati viene utilizzata l'autenticazione di Windows e le credenziali utente non possono essere delegate. Impossibile aggiornare le connessioni seguenti: Dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
  
## Spiegazione  
 Questo messaggio di errore può avere più cause. Il fattore comune a tutte è che tramite Excel Services non è possibile ottenere un'identità utente di Windows valida da un token di attestazione in SharePoint. Nel caso di cartelle di lavoro di Excel contenenti dati di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], questo errore si verifica in una delle condizioni seguenti:  
  
-   Claims nel Servizio token Windows non è in esecuzione. È possibile confermare la causa di questo errore visualizzando il file registro di SharePoint. Se nei registri di SharePoint è incluso il messaggio "Impossibile trovare l'endpoint di pipe di 'net.pipe://localhost/s 4u/022694f3-9fbd-422b-b4b2-312e25dae2a2' nel computer locale", Claims nel Servizio token Windows non è in esecuzione. Per avviarlo, utilizzare Amministrazione centrale, quindi verificare che il servizio sia in esecuzione nell'applicazione console Servizi.  
  
-   Un controller di dominio non è disponibile per la convalida dell'identità utente. Claims nel Servizio token Windows non utilizza le credenziali memorizzate nella cache. Convalida l'identità utente per ogni connessione. È possibile confermare la causa di questo errore visualizzando il file registro di SharePoint. Se nei registri di SharePoint è incluso il messaggio "Impossibile recuperare WindowsIdentity da IClaimsIdentity", l'identità utente non può essere autenticata.  
  
-   I computer devono essere membri dello stesso dominio o trovarsi in domini in cui è disponibile una relazione di trust bidirezionale.  
  
-   È necessario utilizzare account utente di dominio Windows. Gli account devono disporre di un UPN (Universal Principal Name).  
  
-   L'account servizio di Excel Services deve disporre delle autorizzazioni di Active Directory per eseguire una query sull'oggetto.  
  
## Azione dell'utente  
 Utilizzare le istruzioni seguenti per controllare lo stato di Claims nel Servizio token Windows.  
  
 Per tutti gli altri scenari, controllare con l'amministratore di rete.  
  
#### Abilitare Claims nel Servizio token Windows  
  
1.  In Impostazioni sistema di Amministrazione centrale fare clic su **Gestisci servizi nel server**.  
  
2.  Selezionare **Attestazioni per il servizio token Windows** e quindi fare clic su **Avvia**.  
  
3.  Nella console Servizi verificare che anche il servizio sia in esecuzione:  
  
    1.  In Strumenti di amministrazione fare clic su Servizi.  
  
    2.  Avviare Claims nel Servizio token Windows nel caso non sia in esecuzione.  
  
## Vedere anche  
 [Configurare gli account del servizio PowerPivot](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md)  
  
  