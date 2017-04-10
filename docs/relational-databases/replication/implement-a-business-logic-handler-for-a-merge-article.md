---
title: "Implementazione di un gestore della logica di business per un articolo di merge | Microsoft Docs"
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
  - "risoluzione dei conflitti di replica di tipo merge [replica di SQL Server], gestori della logica di business"
  - "gestori della logica di business per la replica di tipo merge [replica di SQL Server]"
  - "risoluzione dei conflitti [replica di SQL Server], replica di tipo merge"
  - "gestori della logica di business [replica di SQL Server]"
  - "classe BusinessLogicModule"
ms.assetid: ed477595-6d46-4fa2-b0d3-a5358903ec05
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Implementazione di un gestore della logica di business per un articolo di merge
  In questo argomento viene descritto come implementare un gestore della logica di business per un articolo di tipo merge in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite la programmazione della replica o RMO (Replication Management Objects).  
  
 Il <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> dello spazio dei nomi implementa un'interfaccia che consente di scrivere la logica di business complessa per gestire gli eventi che si verificano durante il processo di sincronizzazione di replica di tipo merge. I metodi del gestore della logica di business possono essere richiamati dal processo di replica per ogni riga modificata che viene replicata durante la sincronizzazione.  
  
 Il processo generale per l'implementazione di un gestore della logica di business è il seguente:  
  
1.  Creazione dell'assembly del gestore della logica di business.  
  
2.  Registrazione dell'assembly nel server di distribuzione.  
  
3.  Distribuzione dell'assembly nel server in cui viene eseguito l'agente di merge. Per una sottoscrizione pull, l'agente viene eseguito nel Sottoscrittore, mentre per una sottoscrizione push nel server di distribuzione. Quando si utilizza la sincronizzazione tramite il Web, l'agente viene eseguito nel server Web.  
  
4.  Creazione di un articolo che utilizza il gestore della logica di business o modifica di un articolo esistente per l'utilizzo del gestore della logica di business.  
  
 Il gestore della logica di business specificato viene eseguito per ogni riga sincronizzata. La complessità della logica e le chiamate ad altre applicazioni o servizi di rete possono ridurre le prestazioni. Per ulteriori informazioni sui gestori della logica di business, vedere [eseguire logica di Business durante la sincronizzazione di tipo Merge](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
 **Contenuto dell'argomento**  
  
-   **Per implementare un gestore della logica di business per un articolo di merge, utilizzando:**  
  
     [Programmazione della replica](#ReplProg)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="ReplProg"></a> Utilizzo della programmazione della replica  
  
#### Per creare e distribuire un gestore della logica di business  
  
1.  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio creare un nuovo progetto per l'assembly .NET contenente il codice che implementa il gestore della logica di business.  
  
2.  Aggiungere i riferimenti al progetto per gli spazi dei nomi seguenti.  
  
    |Riferimento all'assembly|Percorso|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM (installazione predefinita)|  
    |<xref:System.Data>|GAC (componente di .NET Framework)|  
    |<xref:System.Data.Common>|GAC (componente di .NET Framework)|  
  
3.  Aggiungere una classe che esegue l'override di <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> (classe).  
  
4.  Implementare il <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> proprietà per indicare i tipi di modifiche gestite.  
  
5.  Eseguire l'override di uno o più dei seguenti metodi del <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> classe:  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> -richiamato quando una modifica dei dati viene eseguito il commit durante la sincronizzazione.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> -richiamato quando si verifica un errore quando un'istruzione DELETE viene caricato o scaricato.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> -richiamata quando le istruzioni DELETE vengono caricate o scaricate.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> -richiamato quando si verifica un errore quando un'istruzione INSERT viene caricato o scaricato.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> -richiamata quando le istruzioni INSERT vengono caricate o scaricate.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> -richiamato quando si verificano conflitti di istruzioni UPDATE nel server di pubblicazione e nel Sottoscrittore.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> -richiamata quando le istruzioni UPDATE in conflitto con le istruzioni DELETE nel server di pubblicazione e sottoscrizione.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> -richiamato quando si verifica un errore quando un'istruzione UPDATE viene caricato o scaricato.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> -richiamata quando le istruzioni UPDATE vengono caricate o scaricate.  
  
6.  Compilare il progetto per creare l'assembly del gestore della logica di business.  
  
7.  Distribuire l'assembly nella directory che contiene il file eseguibile dell'agente di merge (replmerg.exe), che per un'installazione predefinita è [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM, o installarlo nella Global Assembly Cache (GAC) .NET. È necessario installare l'assembly nella GAC solo se applicazioni diverse dall'agente di merge richiedono l'accesso all'assembly. L'assembly può essere installato nella GAC tramite lo strumento Global Assembly Cache (**Gacutil.exe)** disponibile in .NET Framework SDK.  
  
    > [!NOTE]  
    >  È necessario distribuire un gestore della logica di business su ogni server in cui viene eseguito l'agente di merge, incluso il server IIS che ospita il file replisapi.dll quando si utilizza la sincronizzazione tramite il Web.  
  
#### Per registrare un gestore della logica di business  
  
1.  Server di pubblicazione, eseguire [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) Per verificare che l'assembly non è già registrato come gestore della logica di business.  
  
2.  Nel server di distribuzione, eseguire [sp_registercustomresolver & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md), specificando un nome descrittivo per il gestore della logica di business per **@article_resolver**, un valore di **true** per **@is_dotnet_assembly**, il nome dell'assembly per **@dotnet_assembly_name**, e il nome completo della classe che esegue l'override <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> per **@dotnet_class_name**.  
  
    > [!NOTE]  
    >  Se l'assembly non viene distribuito nella stessa directory dell'eseguibile dell'agente di Merge, nella stessa directory dell'applicazione che avvia in modo sincrono l'agente di Merge o nella global assembly cache (GAC), è necessario specificare il percorso completo con il nome dell'assembly per **@dotnet_assembly_name**. Quando si utilizza la sincronizzazione tramite il Web, è necessario specificare il percorso dell'assembly nel server Web.  
  
#### Per utilizzare un gestore della logica di business con un nuovo articolo di tabella  
  
1.  Eseguire [sp_addmergearticle & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Per definire un articolo, specificando il nome descrittivo del gestore della logica di business per **@article_resolver**. Per altre informazioni, vedere [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
#### Per utilizzare un gestore della logica di business con un articolo di tabella esistente  
  
1.  Eseguire [sp_changemergearticle & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), specificando **@publication**, **@article**, un valore di **article_resolver** per **@property**, e il nome descrittivo del gestore della logica di business per **@value**.  
  
###  <a name="TsqlExample"></a> Esempi (programmazione della replica)  
 In questo esempio è illustrato un gestore della logica di business che crea un log di controllo.  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../relational-databases/replication/codesnippet/csharp/rmohowto/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 Nell'esempio seguente viene registrato un assembly del gestore della logica di business nel database di distribuzione e viene modificato un articolo di merge esistente per l'utilizzo di questa logica di business personalizzata.  
  
 [!code-sql[HowTo#sp_RegisterBLH_10](../../relational-databases/replication/codesnippet/tsql/implement-a-business-log_3.sql)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
  
#### Per creare un gestore della logica di business  
  
1.  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio creare un nuovo progetto per l'assembly .NET contenente il codice che implementa il gestore della logica di business.  
  
2.  Aggiungere i riferimenti al progetto per gli spazi dei nomi seguenti.  
  
    |Riferimento all'assembly|Percorso|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM (installazione predefinita)|  
    |<xref:System.Data>|GAC (componente di .NET Framework)|  
    |<xref:System.Data.Common>|GAC (componente di .NET Framework)|  
  
3.  Aggiungere una classe che esegue l'override di <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> (classe).  
  
4.  Implementare il <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> proprietà per indicare i tipi di modifiche gestite.  
  
5.  Eseguire l'override di uno o più dei seguenti metodi del <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> classe:  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> -richiamato quando una modifica dei dati viene eseguito il commit durante la sincronizzazione.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> -richiamato se si verifica un errore mentre un'istruzione DELETE viene caricato o scaricato.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> -richiamata quando le istruzioni DELETE vengono caricate o scaricate.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> -richiamato se si verifica un errore quando un'istruzione INSERT viene caricato o scaricato.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> -richiamata quando le istruzioni INSERT vengono caricate o scaricate.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> -richiamato quando si verificano conflitti di istruzioni UPDATE nel server di pubblicazione e nel Sottoscrittore.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> -richiamata quando le istruzioni UPDATE in conflitto con le istruzioni DELETE nel server di pubblicazione e sottoscrizione.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> -richiamato se si verifica un errore quando un'istruzione UPDATE viene caricato o scaricato.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> -richiamata quando le istruzioni UPDATE vengono caricate o scaricate.  
  
    > [!NOTE]  
    >  I conflitti di articoli non gestiti in modo esplicito dalla logica di business personalizzata vengono gestiti dal sistema di risoluzione predefinito per l'articolo.  
  
6.  Compilare il progetto per creare l'assembly del gestore della logica di business.  
  
#### Per registrare un gestore della logica di business  
  
1.  Creare una connessione al server di distribuzione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.ReplicationServer> (classe). Passare il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dal passaggio 1.  
  
3.  Chiamare <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers%2A> e controllare l'oggetto restituito <xref:System.Collections.ArrayList> oggetto per garantire che l'assembly non è già registrato come gestore della logica di business.  
  
4.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler> (classe). Specificare le proprietà seguenti:  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName%2A> -il nome dell'assembly .NET. Se l'assembly non viene distribuito nella stessa directory del file eseguibile dell'agente di merge, nella stessa directory dell'applicazione che avvia in modo sincrono l'agente di merge o nella GAC (Global Assembly Cache), è necessario includere il percorso completo con il nome dell'assembly. È necessario includere il percorso completo con il nome dell'assembly quando si utilizza un gestore della logica di business con la sincronizzazione tramite il Web.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName%2A> -il nome completo della classe che esegue l'override <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> e implementa il gestore della logica di business.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> -un nome descrittivo usato quando si accede a gestore della logica di business.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly%2A> -il valore **true**.  
  
#### Per distribuire un gestore della logica di business  
  
1.  Distribuire l'assembly nel server in cui viene eseguito l'agente merge, nel percorso file specificato durante la registrazione del gestore della logica di business nel server di distribuzione. Per una sottoscrizione pull, l'agente viene eseguito nel Sottoscrittore, mentre per una sottoscrizione push nel server di distribuzione. Quando si utilizza la sincronizzazione tramite il Web, l'agente viene eseguito nel server Web. Se con il nome dell'assembly non è stato incluso il percorso completo durante la registrazione del gestore della logica di business, distribuire l'assembly nella stessa directory del file eseguibile dell'agente di merge o nella stessa directory dell'applicazione che avvia in modo sincrono l'agente di merge. È possibile installare l'assembly nella GAC se più applicazioni utilizzano lo stesso assembly.  
  
#### Per utilizzare un gestore della logica di business con un nuovo articolo di tabella  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergeArticle> (classe). Impostare le proprietà seguenti:  
  
    -   Il nome dell'articolo per <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.  
  
    -   Il nome della pubblicazione per <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.  
  
    -   Il nome del database di pubblicazione per <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A>.  
  
    -   Il nome descrittivo del gestore della logica di business (<xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A>) per <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.Article.Create%2A> metodo. Per altre informazioni, vedere [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
#### Per utilizzare un gestore della logica di business con un articolo di tabella esistente  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergeArticle> (classe).  
  
3.  Impostare il <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, e <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> proprietà.  
  
4.  Impostare la connessione del passaggio 1 per il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà.  
  
5.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà dell'articolo sono state definite in modo non corretto nel passaggio 3 oppure l'articolo non esiste. Per altre informazioni, vedere [View and Modify Article Properties](../../relational-databases/replication/publish/view-and-modify-article-properties.md).  
  
6.  Impostare il nome descrittivo del gestore della logica di business per <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>. Questo è il valore di <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> proprietà specificata quando si registra il gestore della logica di business.  
  
###  <a name="PShellExample"></a> Esempi (RMO)  
 In questo esempio è illustrato un gestore della logica di business che registra informazioni sulle operazioni di inserimento, aggiornamento ed eliminazione nel Sottoscrittore.  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../relational-databases/replication/codesnippet/csharp/rmohowto/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 In questo esempio viene registrato un gestore della logica di business nel server di distribuzione.  
  
 [!code-csharp[HowTo#rmo_RegisterBLH_10](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_registerblh_10)]  
  
 [!code-vb[HowTo#rmo_vb_RegisterBLH_10](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_registerblh_10)]  
  
 In questo esempio viene modificato un articolo esistente per l'utilizzo del gestore della logica di business.  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## Vedere anche  
 [Implement a Custom Conflict Resolver for a Merge Article](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)   
 [Eseguire il debug di un gestore della logica di Business & #40; Programmazione della replica & #41;](../../relational-databases/replication/debug-a-business-logic-handler-replication-programming.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Concetti di base relativi a RMO (Replication Management Objects)](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)  
  
  