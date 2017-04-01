---
title: "Configurare le propriet&#224; delle origini dati per un report (Gestione report) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "origini dati [Reporting Services], incorporate"
ms.assetid: 27af5195-c845-40e0-9a9c-efe569424022
caps.latest.revision: 44
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 44
---
# Configurare le propriet&#224; delle origini dati per un report (Gestione report)
  Quando si esegue un report, il server di report recupera informazioni sulla proprietà per determinare come connettersi a un'origine dati. Il tipo di origine dati, la stringa di connessione e le informazioni sulle credenziali sono specificati nelle pagine delle proprietà dell'origine dati del report pubblicato. È possibile impostare le proprietà per modificare le informazioni sulla connessione all'origine dati rispetto ai valori originali specificati al momento della creazione del report.  
  
 In alternativa, se si dispone di un'origine dati condivisa predefinita che specifica già le informazioni sulla connessione da utilizzare, è possibile specificare tale origine. Per usare un'origine dati condivisa, fare clic su **Origine dati condivisa** nella pagina delle proprietà dell'origine dati del report.  
  
### Per configurare un'origine dati incorporata  
  
1.  Avviare [Gestione report &#40;modalità nativa SSRS&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md).  
  
2.  In Gestione report passare alla pagina **Contenuto**. quindi passare al report per il quale si desidera configurare un'origine dei dati specifica del report e aprirlo.  
  
3.  Fare clic sulla scheda **Proprietà**. Verrà visualizzata la pagina delle proprietà **Generale**.  
  
4.  Fare clic sulla scheda **Origini dati** . Verrà visualizzata la pagina delle proprietà dell'origine dati del report.  
  
5.  Fare clic su **Origine dati personalizzata** per specificare le informazioni sulla connessione all'origine dati all'interno del report.  
  
6.  Nell'elenco **Tipo di connessione** specificare l'estensione per l'elaborazione dati usata per elaborare i dati dall'origine dati.  
  
7.  Per **Stringa di connessione**specificare la stringa utilizzata dal server di report per la connessione all'origine dei dati. È consigliabile evitare di specificare credenziali nella stringa di connessione.  
  
     L'esempio seguente illustra una stringa di connessione usata per connettersi al database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]:  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
8.  Per **Connetti tramite** specificare come verranno ottenute le credenziali quando il report è in esecuzione:  
  
    -   Se si vuole richiedere all'utente un nome di accesso e una password, fare clic su **Credenziali fornite dall'utente che esegue il report**.  
  
    -   Se si prevede di usare l'origine dati con report che supportano le sottoscrizioni o altre operazioni pianificate, ad esempio la generazione della cronologia del report automatica, fare clic su **Credenziali archiviate in modo sicuro nel server di report**.  
  
    -   Se si vuole che le credenziali dell'utente che accede al report vengano passate dal server di report al server che ospita l'origine dati esterna, fare clic su **Sicurezza integrata di Windows**. In questo caso, all'utente non viene richiesto di digitare un nome utente o una password.  
  
    -   Se l'origine dati non usa credenziali (ad esempio, se l'origine dati è un file XML a cui si accede dal file system), fare clic su **Credenziali non necessarie**. È necessario specificare questo tipo di credenziali solo se l'operazione risulta valida per l'origine dati specifica. Se si seleziona questa opzione per un'origine dati che richiede l'autenticazione, la connessione non verrà stabilita. Se si seleziona questa opzione, assicurarsi inoltre di configurare l'account di esecuzione automatica che consente al server di report di connettersi agli altri computer per recuperare dati o file quando le credenziali utente non sono disponibili.  
  
 Per altre informazioni sulla configurazione delle credenziali, vedere [Specificare le credenziali e le informazioni sulla connessione per le origini dati del report](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md). Per altre informazioni sull'account di esecuzione automatica, vedere [Configurare l'account di esecuzione automatica &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
## Vedere anche  
 [Pagina Contenuto &#40;Gestione report&#41;](../Topic/Contents%20Page%20\(Report%20Manager\).md)   
 [Pagina Nuova origine dati &#40;Gestione report&#41;](../Topic/New%20Data%20Source%20Page%20\(Report%20Manager\).md)   
 [Creare, modificare ed eliminare origini dati condivise &#40;SSRS&#41;](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)   
 [Gestire origini dati dei report](../../reporting-services/report-data/manage-report-data-sources.md)   
 [Creare, eliminare o modificare un'origine dei dati condivisa &#40;Gestione report&#41;](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md)   
 [Pagina delle proprietà Origini dati &#40;Gestione report&#41;](../Topic/Data%20Sources%20Properties%20Page%20\(Report%20Manager\).md)  
  
  