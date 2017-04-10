---
title: "Definizione e modifica di un filtro colonne | Microsoft Docs"
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
  - "filters [SQL Server replication], column"
  - "modifying filters, column"
  - "modifying filters"
  - "filtri colonne [replica di SQL Server]"
ms.assetid: d7c3186a-9a8c-45d8-ab34-05beec4c26dd
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# Definizione e modifica di un filtro colonne
  In questo argomento viene descritto come definire e modificare un filtro colonne in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
-   **Per definire e modificare un filtro colonne, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Alcune colonne non possono essere filtrate; Per ulteriori informazioni, vedere [filtrare i dati pubblicati](../../../relational-databases/replication/publish/filter-published-data.md). Se si modifica un filtro di colonna dopo l'inizializzazione delle sottoscrizioni, dopo la modifica è necessario generare un nuovo snapshot e reinizializzare tutte le sottoscrizioni. Per ulteriori informazioni sui requisiti per le modifiche alle proprietà, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Definire i filtri colonne nella pagina **Articoli** della Creazione guidata nuova pubblicazione. Per ulteriori informazioni sull'utilizzo di creazione guidata nuova pubblicazione, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md).  
  
 Definire e modificare i filtri di colonna nel **articoli** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sulla pubblicazione e le proprietà di articolo, vedere [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Per definire un filtro colonne  
  
1.  Nella pagina **Articoli** della Creazione guidata nuova pubblicazione espandere la tabella da filtrare nel riquadro **Oggetti da pubblicare** .  
  
2.  Deselezionare la casella di controllo accanto a ogni colonna che si desidera filtrare.  
  
#### Per modificare l'applicazione di filtri di colonna  
  
1.  Nel **articoli** pagina della **Proprietà pubblicazione - \< pubblicazione>** finestra di dialogo espandere la tabella da filtrare nel **oggetti da pubblicare** riquadro.  
  
2.  Deselezionare la casella di controllo accanto a ogni colonna che si desidera filtrare e verificare che la casella di controllo sia selezionata per ogni colonna da includere nell'articolo.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 Durante la creazione di articoli di tabella è possibile definire le colonne da includere nell'articolo e modificare le colonne dopo aver definito l'articolo. È possibile creare e modificare a livello di programmazione le colonne filtrate tramite le stored procedure di replica.  
  
> [!NOTE]  
>  Nelle procedure seguenti si presuppone che la tabella sottostante non sia modificata. Per informazioni sulla replica modifiche data definition language (DDL) alle tabelle pubblicate, vedere [apportare le modifiche dello Schema nei database di pubblicazione](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
#### Per definire un filtro di colonna per un articolo pubblicato di una pubblicazione snapshot o transazionale  
  
1.  Definire l'articolo da filtrare. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md). Verranno definite le colonne da includere o rimuovere dall'articolo.  
  
    -   Se la pubblicazione solo alcune colonne da una tabella con molte colonne, eseguire [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) una volta per ogni colonna da aggiungere. Specificare il nome della colonna per **@column** e il valore **add** per **@operation**.  
  
    -   Se pubblicare la maggior parte delle colonne in una tabella con molte colonne, eseguire [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md), specificando il valore **null** per **@column** e il valore **aggiungere** per **@operation** per aggiungere tutte le colonne. Eseguire quindi [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md), una volta per ogni colonna da escludere, specificando un valore di **drop** per **@operation** e il nome della colonna esclusa per **@column**.  
  
3.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). Specificare il nome della pubblicazione per **@publication** e il nome dell'articolo filtrato per **@article**. Verranno creati gli oggetti di sincronizzazione per l'articolo filtrato.  
  
#### Per modificare un filtro colonne in modo da includere colonne aggiuntive per un articolo pubblicato di una pubblicazione snapshot o transazionale  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) una volta per ogni colonna da aggiungere. Specificare il nome della colonna per **@column** e il valore **add** per **@operation**.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). Specificare il nome della pubblicazione per **@publication** e il nome dell'articolo filtrato per **@article**. Se la pubblicazione esistono sottoscrizioni, specificare un valore di **1** per **@change_active**. Verranno creati nuovamente gli oggetti di sincronizzazione per l'articolo filtrato.  
  
3.  Rieseguire il processo dell'agente snapshot per la pubblicazione per generare uno snapshot aggiornato.  
  
4.  Reinizializzazione delle sottoscrizioni. Per ulteriori informazioni, vedere [reinizializzare le sottoscrizioni](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### Per modificare un filtro colonne in modo da rimuovere colonne per un articolo pubblicato di una pubblicazione snapshot o transazionale  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) una volta per ogni colonna da rimuovere. Specificare il nome della colonna per **@column** e il valore **drop** per **@operation**.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). Specificare il nome della pubblicazione per **@publication** e il nome dell'articolo filtrato per **@article**. Se la pubblicazione esistono sottoscrizioni, specificare un valore di **1** per **@change_active**. Verranno creati nuovamente gli oggetti di sincronizzazione per l'articolo filtrato.  
  
3.  Rieseguire il processo dell'agente snapshot per la pubblicazione per generare uno snapshot aggiornato.  
  
4.  Reinizializzazione delle sottoscrizioni. Per ulteriori informazioni, vedere [reinizializzare le sottoscrizioni](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### Per definire un filtro di colonna per un articolo pubblicato di una pubblicazione di tipo merge  
  
1.  Definire l'articolo da filtrare. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md). Verranno definite le colonne da includere o rimuovere dall'articolo.  
  
    -   Se la pubblicazione solo alcune colonne da una tabella con molte colonne, eseguire [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) una volta per ogni colonna da aggiungere. Specificare il nome della colonna per **@column** e il valore **add** per **@operation**.  
  
    -   Se pubblicare la maggior parte delle colonne in una tabella con molte colonne, eseguire [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md), specificando il valore **null** per **@column** e il valore **aggiungere** per **@operation** per aggiungere tutte le colonne. Eseguire quindi [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md), una volta per ogni colonna da escludere, specificando un valore di **drop** per **@operation** e il nome della colonna esclusa per **@column**.  
  
#### Per modificare un filtro colonne in modo da includere colonne aggiuntive per un articolo pubblicato di una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) una volta per ogni colonna da aggiungere. Specificare il nome di colonna per **@column**, un valore di **aggiungere** per **@operation** e il valore **1** per entrambi **@force_invalidate_snapshot** e **@force_reinit_subscription**.  
  
2.  Rieseguire il processo dell'agente snapshot per la pubblicazione per generare uno snapshot aggiornato.  
  
3.  Reinizializzazione delle sottoscrizioni. Per ulteriori informazioni, vedere [reinizializzare le sottoscrizioni](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### Per modificare un filtro colonne in modo da rimuovere colonne per un articolo pubblicato di una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) una volta per ogni colonna da rimuovere. Specificare il nome di colonna per **@column**, un valore di **drop** per **@operation** e il valore **1** per entrambi **@force_invalidate_snapshot** e **@force_reinit_subscription**.  
  
2.  Rieseguire il processo dell'agente snapshot per la pubblicazione per generare uno snapshot aggiornato.  
  
3.  Reinizializzazione delle sottoscrizioni. Per ulteriori informazioni, vedere [reinizializzare le sottoscrizioni](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
###  <a name="TsqlExample"></a> Esempio (Transact-SQL)  
 In questo esempio di replica transazionale la colonna `DaysToManufacture` viene rimossa da un articolo basato sulla tabella `Product` .  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-colu_1.sql)]  
  
 In questo esempio di replica di tipo merge la colonna `CreditCardApprovalCode` viene rimossa da un articolo basato sulla tabella `SalesOrderHeader` .  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-colu_2.sql)]  
  
## Vedere anche  
 [Modifica delle proprietà di pubblicazioni e articoli](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Filtro dei dati pubblicati](../../../relational-databases/replication/publish/filter-published-data.md)   
 [Filtro dei dati pubblicati per la replica di tipo merge](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)  
  
  