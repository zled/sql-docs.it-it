---
title: "Specify the Conflict Tracking and Resolution Level for Merge Articles | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "merge replication conflict resolution [SQL Server replication], levels"
  - "articles [SQL Server replication], conflict resolution"
  - "risoluzione dei conflitti [replica di SQL Server], replica di tipo merge"
ms.assetid: 81e9ecb6-1d31-4a78-b32a-96f7f4d67077
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Specify the Conflict Tracking and Resolution Level for Merge Articles
  In questo argomento viene descritto come specificare il livello di rilevamento e risoluzione dei conflitti per gli articoli di merge in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Quando si sincronizza una sottoscrizione di una pubblicazione di tipo merge, la replica verifica la presenza di conflitti causati dalle modifiche apportate agli stessi dati nel server di pubblicazione e nel Sottoscrittore. È possibile specificare se rilevare i conflitti a livello di riga, ovvero considerare un conflitto qualsiasi modifica apportata alla riga, o a livello di colonna, ovvero considerare un conflitto solo le modifiche apportate alla stessa riga e colonna. La risoluzione dei conflitti relativi agli articoli viene eseguita a livello di riga. Per ulteriori informazioni sul rilevamento e sulla risoluzione dei conflitti in caso di utilizzo dei record logici, vedere [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
-   **Per specificare del livello di rilevamento e risoluzione dei conflitti per gli articoli di merge, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Se si modifica il livello di rilevamento in seguito all'inizializzazione delle sottoscrizioni, sarà necessario reinizializzarle. Per ulteriori informazioni sugli effetti delle modifiche della proprietà, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
-   Con il rilevamento a livello di riga e di colonna, la risoluzione dei conflitti viene sempre eseguita a livello di riga, ovvero la riga che prevale sovrascrive quella perdente. La replica di tipo merge consente inoltre di specificare che i conflitti vengano rilevati e risolti a livello di record logico. Queste opzioni tuttavia non sono disponibili in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]. Per informazioni sulla relativa impostazione dalle stored procedure di replica, vedere [Define a Logical Record Relationship Between Merge Table Articles](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Specificare una colonna a livello di riga o di rilevamento per gli articoli di merge nel **proprietà** scheda della finestra il **Proprietà articolo** la finestra di dialogo, disponibile nella creazione guidata pubblicazione e il **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'utilizzo della procedura guidata e l'accesso nella finestra di dialogo, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Per specificare il rilevamento a livello di riga o di colonna  
  
1.  Nel **articoli** pagina della procedura guidata nuova pubblicazione o **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare una tabella.  
  
2.  Fare clic su **Proprietà articolo**, quindi su **Imposta proprietà dell'articolo di tabella evidenziato** o su **Imposta proprietà di tutti gli articoli di tabelle**.  
  
3.  Nel **proprietà** scheda il **Proprietà articolo \< articolo>** la finestra di dialogo, selezionare uno dei seguenti valori per il **livello rilevamento** proprietà: **rilevamento a livello di riga** o **rilevamento a livello di colonna**.  
  
4.  Se è la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per specificare le opzioni di rilevamento dei conflitti per un nuovo articolo di merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) e specificare uno dei valori seguenti per **@column_tracking**:  
  
    -   **true** -utilizza il rilevamento a livello di colonna per l'articolo.  
  
    -   **false** -rilevamento a livello di riga, utilizzare il valore predefinito.  
  
#### Per modificare le opzioni di rilevamento dei conflitti per un articolo di merge  
  
1.  Per determinare le opzioni per un articolo di merge di rilevamento dei conflitti, eseguire [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md). Prendere nota del valore di **column_tracking** opzione nel set di risultati per l'articolo. Il valore **1** indica che viene utilizzato il rilevamento a livello di colonna, mentre il valore di **0** significa che viene utilizzato il rilevamento a livello di riga.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Specificare un valore di **column_tracking** per **@property** e uno dei seguenti valori per **@value**:  
  
    -   **true** -utilizza il rilevamento a livello di colonna per l'articolo.  
  
    -   **false** -rilevamento a livello di riga, utilizzare il valore predefinito.  
  
     Specificare un valore di **1** per entrambi **@force_invalidate_snapshot** e **@force_reinit_subscription**.  
  
## Vedere anche  
 [Rilevamento e risoluzione avanzati dei conflitti nella replica di tipo merge](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Rilevamento e risoluzione dei conflitti nei record logici](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md)   
 [Definizione di una relazione tra record logici degli articoli di tabelle di merge](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md)   
 [Rilevamento e risoluzione di conflitti tra repliche di tipo merge](../../../relational-databases/replication/merge/detect-and-resolve-merge-replication-conflicts.md)  
  
  