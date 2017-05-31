---
title: Specificare il livello di rilevamento e risoluzione dei conflitti per gli articoli di merge | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], levels
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 81e9ecb6-1d31-4a78-b32a-96f7f4d67077
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 18b5650ce77b40deb101a16ebd1379600394dcbf
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="specify-the-conflict-tracking-and-resolution-level-for-merge-articles"></a>Specifica del livello di rilevamento e risoluzione dei conflitti per gli articoli di merge
  In questo argomento viene descritto come specificare il livello di rilevamento e risoluzione dei conflitti per gli articoli di merge in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Quando si sincronizza una sottoscrizione di una pubblicazione di tipo merge, la replica verifica la presenza di conflitti causati dalle modifiche apportate agli stessi dati nel server di pubblicazione e nel Sottoscrittore. È possibile specificare se rilevare i conflitti a livello di riga, ovvero considerare un conflitto qualsiasi modifica apportata alla riga, o a livello di colonna, ovvero considerare un conflitto solo le modifiche apportate alla stessa riga e colonna. La risoluzione dei conflitti relativi agli articoli viene eseguita a livello di riga. Per ulteriori informazioni sul rilevamento e sulla risoluzione dei conflitti in caso di utilizzo dei record logici, vedere [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-resolving-in-logical-record.md).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
-   **Per specificare del livello di rilevamento e risoluzione dei conflitti per gli articoli di merge, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Se si modifica il livello di rilevamento in seguito all'inizializzazione delle sottoscrizioni, sarà necessario reinizializzarle. Per altre informazioni sugli effetti delle modifiche delle proprietà, vedere [Modificare le proprietà di pubblicazioni e articoli](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
-   Con il rilevamento a livello di riga e di colonna, la risoluzione dei conflitti viene sempre eseguita a livello di riga, ovvero la riga che prevale sovrascrive quella perdente. La replica di tipo merge consente inoltre di specificare che i conflitti vengano rilevati e risolti a livello di record logico. Queste opzioni tuttavia non sono disponibili in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]. Per informazioni sulla relativa impostazione dalle stored procedure di replica, vedere [Define a Logical Record Relationship Between Merge Table Articles](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Specificare il rilevamento a livello di riga o colonna per gli articoli di merge nella scheda **Proprietà** della finestra di dialogo **Proprietà articolo**, disponibile nella Creazione guidata nuova pubblicazione e nella finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**. Per altre informazioni sull'uso della creazione guidata e l'accesso alla finestra di dialogo, vedere [Creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [Visualizzare e modificare le proprietà della pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-row--or-column-level-tracking"></a>Per specificare il rilevamento a livello di riga o di colonna  
  
1.  Selezionare una tabella nella pagina **Articoli** della Creazione guidata nuova pubblicazione o nella finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**.  
  
2.  Fare clic su **Proprietà articolo**, quindi su **Imposta proprietà dell'articolo di tabella evidenziato** o su **Imposta proprietà di tutti gli articoli di tabelle**.  
  
3.  Nella scheda **Proprietà** della finestra di dialogo **Proprietà articolo \<Articolo>** selezionare uno dei valori seguenti per la proprietà **Livello rilevamento**: **Rilevamento a livello di riga** o **Rilevamento a livello di colonna**.  
  
4.  Se è visualizzata la finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>** fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### <a name="to-specify-conflict-tracking-options-for-a-new-merge-article"></a>Per specificare le opzioni di rilevamento dei conflitti per un nuovo articolo di merge  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) e specificare uno dei valori seguenti per **@column_tracking**:  
  
    -   **true** : consente di utilizzare il rilevamento a livello di colonna per l'articolo.  
  
    -   **false** : consente di utilizzare il rilevamento a livello di riga, che corrisponde all'impostazione predefinita.  
  
#### <a name="to-change-conflict-tracking-options-for-a-merge-article"></a>Per modificare le opzioni di rilevamento dei conflitti per un articolo di merge  
  
1.  Per determinare le opzioni di rilevamento dei conflitti per un articolo di merge, eseguire [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md). Notare il valore dell'opzione **column_tracking** nel set di risultati relativo l'articolo. Il valore **1** indica che viene utilizzato il rilevamento a livello di colonna, mentre il valore **0** indica che viene utilizzato il rilevamento a livello di riga.  
  
2.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Specificare il valore **column_tracking** per **@property** e uno dei valori seguenti per **@value**:  
  
    -   **true** : consente di utilizzare il rilevamento a livello di colonna per l'articolo.  
  
    -   **false** : consente di utilizzare il rilevamento a livello di riga, che corrisponde all'impostazione predefinita.  
  
     Specificare il valore **1** sia per **@force_invalidate_snapshot** e **@force_reinit_subscription**.  
  
## <a name="see-also"></a>Vedere anche  
 [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-resolving-in-logical-record.md)   
 [Define a Logical Record Relationship Between Merge Table Articles](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md)   
 [Rilevare e risolvere i conflitti tra repliche di tipo merge](../../../relational-databases/replication/merge/advanced-merge-replication-resolve-merge-replication-conflicts.md)  
  
  
