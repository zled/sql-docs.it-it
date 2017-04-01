---
title: "Impostazione del tipo solo download per un articolo di tabella di merge | Microsoft Docs"
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
  - "merge replication [SQL Server replication], download-only articles"
  - "articles [SQL Server replication], download-only"
  - "articoli di solo download"
ms.assetid: 14839cec-6dbf-49c2-aa27-56847b09b4db
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# Impostazione del tipo solo download per un articolo di tabella di merge
  In questo argomento viene descritto come specificare che un articolo di tabella del merge è di solo download in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Gli articoli di solo download sono progettati per le applicazioni i cui dati non vengono aggiornati nei Sottoscrittori. Per ulteriori informazioni, vedere [Ottimizza prestazioni della replica di tipo Merge con gli articoli Download-Only](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
-   **Per specificare che un articolo di tabella di merge è di solo download tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Se si specifica che un articolo è di tipo solo download dopo l'inizializzazione delle sottoscrizioni, tutte le sottoscrizioni client a cui è stato inviato l'articolo devono essere reinizializzate. Non è necessario reinizializzare le sottoscrizioni server. Per ulteriori informazioni sugli effetti delle modifiche della proprietà, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Specificare che un articolo è di solo download nel **articoli** pagina della procedura guidata nuova pubblicazione o **proprietà** scheda il **Proprietà articolo - \< articolo>** la finestra di dialogo. Questa finestra di dialogo è disponibile nella creazione guidata pubblicazione e la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'utilizzo della procedura guidata e l'accesso nella finestra di dialogo, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Per specificare che un articolo è di tipo solo download nella pagina Articoli  
  
-   Nel **articoli** pagina della creazione guidata nuova pubblicazione selezionare una tabella e quindi selezionare la casella di controllo **tabella evidenziata è di solo download**.  
  
#### Per specificare che un articolo è di solo download nella scheda proprietà della proprietà articolo - \< articolo> la finestra di dialogo  
  
1.  Nel **articoli** pagina della procedura guidata nuova pubblicazione o **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare una tabella e quindi fare clic su **Proprietà articolo**.  
  
2.  Fare clic su **Imposta proprietà dell'articolo di tabelle evidenziato** o su **Imposta proprietà di tutti gli articoli di tabelle**.  
  
3.  Nel **oggetto di destinazione** sezione il **proprietà** scheda del **Proprietà articolo - \< articolo>** finestra di dialogo specificare uno dei valori seguenti per **la direzione di sincronizzazione**:  
  
    -   **Solo download sul Sottoscrittore, non consentire modifiche del Sottoscrittore**  
  
    -   **Solo download sul Sottoscrittore, consenti modifiche del Sottoscrittore**  
  
4.  Se è la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per specificare che un nuovo articolo di tabella di merge è di solo download  
  
1.  Eseguire [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), specificando il valore **1** o **2** per il parametro **@subscriber_upload_options**. I numeri corrispondono al comportamento seguente:  
  
    -   **0** -senza restrizioni (impostazione predefinita). Le modifiche eseguite nel Sottoscrittore vengono caricate nel server di pubblicazione.  
  
    -   **1** : sono consentite modifiche nel Sottoscrittore, ma non vengono caricate nel server di pubblicazione.  
  
    -   **2** -non sono consentite modifiche nel Sottoscrittore.  
  
        > [!NOTE]  
        >  Se la tabella di origine per un articolo è già pubblicata in un'altra pubblicazione, il valore di **@subscriber_upload_options** deve essere uguale per entrambi gli articoli.  
  
#### Per impostare il tipo di un articolo di tabella di merge esistente su solo download  
  
1.  Per determinare se un articolo è di solo download, eseguire [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md). Prendere nota del valore di **upload_options** impostato per l'articolo nel risultato.  
  
2.  Se il valore restituito nel passaggio 1 è **0**, eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), specificando il valore **subscriber_upload_options** per **@property**, un valore di **1** per **@force_invalidate_snapshot** e **@force_reinit_subscription**, e il valore **1** o **2** per **@value**, che corrisponde al comportamento seguente:  
  
    -   **1** : sono consentite modifiche nel Sottoscrittore, ma non vengono caricate nel server di pubblicazione.  
  
    -   **2** -non sono consentite modifiche nel Sottoscrittore.  
  
        > [!NOTE]  
        >  Se la tabella di origine di un articolo è già inclusa in un'altra pubblicazione, il comportamento del solo download deve coincidere per entrambi gli articoli.  
  
## Vedere anche  
 [Ottimizzazione delle prestazioni della replica di tipo merge con gli articoli di solo download](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)   
 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)   
 [Visualizzazione e modifica delle proprietà degli articoli](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
  