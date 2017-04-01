---
title: "Concedere i diritti di amministratore del server a un&#39;istanza di Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "diritti di amministratore [Analysis Services]"
  - "autorizzazioni amministrative valide per l'intero server [Analysis Services]"
ms.assetid: 20d1234b-a457-4a84-ae08-fe356870c466
caps.latest.revision: 37
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 37
---
# Concedere i diritti di amministratore del server a un&#39;istanza di Analysis Services
  I membri del ruolo di amministratore del server in un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dispongono di accesso illimitato a tutti gli oggetti e i dati di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in tale istanza. Per effettuare un'attività a livello di intero server, ad esempio la creazione o l'elaborazione di un database, la modifica delle proprietà del server o l'avvio di una traccia, per finalità diverse dall'elaborazione degli eventi, un utente deve essere membro del ruolo di amministratore del server.  
  
 L'appartenenza al ruolo viene stabilita quando viene installato [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . L'utente che esegue il programma di installazione può aggiungere se stesso al ruolo o aggiungere un altro utente. È necessario specificare almeno un amministratore prima che il programma di installazione possa continuare.  
  
 Per impostazione predefinita, ai membri del gruppo di amministratori locali vengono anche garantiti diritti amministrativi in Analysis Services. Sebbene al gruppo locale non venga garantita esplicitamente l'appartenenza al ruolo di amministratore del server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , gli amministratori locali possono creare database, aggiungere utenti e autorizzazioni ed effettuare qualsiasi altra attività consentita agli amministratori di sistema. La concessione implicita delle autorizzazioni di amministratore è configurabile. infatti è determinato dalla proprietà del server **BuiltinAdminsAreServerAdmins** , che è impostata su **true** per impostazione predefinita. Questa proprietà può essere modificata in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per altre informazioni, vedere [Security Properties](../../analysis-services/server-properties/security-properties.md).  
  
 Dopo l'installazione è possibile modificare l'appartenenza ai ruoli per aggiungere eventuali altri utenti che necessitano di diritti completi per il servizio. È anche possibile gestire i ruoli del server tramite la libreria AMO (Analysis Management Objects). Per altre informazioni, vedere [Sviluppo con AMO &#40;Analysis Management Objects&#41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fornisce una progressione di ruoli sempre più granulari per l'elaborazione e l'esecuzione di query a livello di server, database e oggetti. Per istruzioni su come usare questi ruoli, vedere [Ruoli e autorizzazioni &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md).  
  
## Modificare l'appartenenze al ruolo del server  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] connettersi all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], fare clic con il pulsante destro del mouse sul nome dell'istanza in Esplora oggetti e quindi scegliere **Proprietà**.  
  
2.  Fare clic sulla scheda **Sicurezza** nel riquadro **Selezione pagina** , quindi selezionare **Aggiungi** nella parte inferiore della pagina per aggiungere uno o più utenti o gruppi di Windows al ruolo del server.  
  
     ![Finestra di dialogo Aggiungi utenti in SQL Server Management Studio](../../analysis-services/instances/media/ssas-serveradminadd.png "Finestra di dialogo Aggiungi utenti in SQL Server Management Studio")  
  
### Aggiungere account computer  
 È anche possibile usare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per fare in modo che un account computer sia membro del gruppo Administrators di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
1.  Nella finestra di dialogo **Seleziona utenti o gruppi** fare clic su **percorsi**.  
  
2.  Selezionare il dominio di cui sono membri i computer da aggiungere oppure **Directory completa** e fare clic su **Ok**.  
  
3.  Fare clic su **Tipi di oggetti**.  
  
4.  Fare clic su **Computer** , quindi fare clic su **Ok**.  
  
     ![add computer accounts as ssas administrators](../../analysis-services/instances/media/ssas-in-ssms-computerobjects.png "add computer accounts as ssas administrators")  
  
5.  Nella casella di testo **Immettere i nomi degli oggetti da selezionare** digitare il nome del computer e fare clic su **Controlla nomi** per verificare che l'account del computer sia presente nelle posizioni correnti. Se l'account del computer non viene trovato, verificare il nome del computer e il dominio corretto di cui fa parte il computer.  
  
## Account NT Service\SSASTelemetry  
 **NT Service/SSASTelemetry** è un account computer con privilegi limitati creato durante l'installazione e usato esclusivamente per eseguire l'implementazione [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] del servizio Analisi utilizzo software. Questo servizio richiede i diritti di amministratore nell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per eseguire vari comandi di individuazione. Per ulteriori informazioni, vedere [Customer Experience Improvement Program for SQL Server Data Tools](../../sql-server/customer-experience-improvement-program-for-sql-server-data-tools.md) e [Microsoft SQL Server Privacy Statement](../Topic/Microsoft%20SQL%20Server%20Privacy%20Statement.md) .  
  
## Vedere anche  
 [Autorizzazione dell'accesso a oggetti e operazioni &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)   
 [Ruoli di sicurezza &#40;Analysis Services - Dati multidimensionali&#41;](../../analysis-services/multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
  