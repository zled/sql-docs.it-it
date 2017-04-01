---
title: "Replica delle modifiche dello schema | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "replication [SQL Server], schema changes"
  - "schemi [replica di SQL Server], replica di modifiche"
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
caps.latest.revision: 43
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 43
---
# Replica delle modifiche dello schema
  In questo argomento si illustra come replicare le modifiche dello schema in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Se si apportano le seguenti modifiche dello schema a un articolo pubblicato, per impostazione predefinita vengono propagate ai Sottoscrittori [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
-   **Per replicare le modifiche dello schema, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   L'istruzione ALTER TABLE … DROP COLUMN viene sempre replicata in tutti i Sottoscrittori la cui sottoscrizione contiene le colonne in corso di eliminazione, anche in caso di disabilitazione della replica delle modifiche dello schema.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Se non si desidera replicare le modifiche dello schema per una pubblicazione, disabilitare la replica delle modifiche dello schema nel **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Per disabilitare la replica delle modifiche dello schema  
  
1.  Nel **Opzioni di sottoscrizione** pagina della **Proprietà pubblicazione - \< pubblicazione>** finestra di dialogo, impostare il valore del **Replica modifiche dello schema** proprietà **False**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Per propagare soltanto modifiche dello schema specifiche, impostare la proprietà su **Vero** prima di una modifica dello schema e quindi impostarla su **Falso** al termine della modifica. Al contrario, per propagare la maggior parte delle modifiche dello schema ma non una determinata modifica, impostare la proprietà su **Falso** prima della modifica dello schema e quindi impostarla su **Vero** al termine della modifica.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile utilizzare le stored procedure di replica per specificare se queste modifiche dello schema vengono replicate. La stored procedure utilizzata dipende del tipo di pubblicazione.  
  
#### Per creare una pubblicazione snapshot o transazionale che non replica le modifiche dello schema  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addpublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), specificando il valore **0** per **@replicate_ddl**. Per altre informazioni, vedere [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Per creare una pubblicazione di tipo merge che non replica le modifiche dello schema  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), specificando il valore **0** per **@replicate_ddl**. Per altre informazioni, vedere [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Per disabilitare temporaneamente la replica delle modifiche dello schema per una pubblicazione snapshot o transazionale  
  
1.  Per una pubblicazione con la replica delle modifiche dello schema, eseguire [sp_changepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), specificando il valore **replicate_ddl** per **@property** e il valore **0** per **@value**.  
  
2.  Eseguire il comando DDL sull'oggetto pubblicato.  
  
3.  (Facoltativo) Riattivare la replica delle modifiche dello schema eseguendo [sp_changepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), specificando il valore **replicate_ddl** per **@property** e il valore **1** per **@value**.  
  
#### Per disabilitare temporaneamente la replica delle modifiche dello schema per una pubblicazione di tipo merge  
  
1.  Per una pubblicazione con la replica delle modifiche dello schema, eseguire [sp_changemergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), specificando il valore **replicate_ddl** per **@property** e il valore **0** per **@value**.  
  
2.  Eseguire il comando DDL sull'oggetto pubblicato.  
  
3.  (Facoltativo) Riattivare la replica delle modifiche dello schema eseguendo [sp_changemergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), specificando il valore **replicate_ddl** per **@property** e il valore **1** per **@value**.  
  
## Vedere anche  
 [Modifiche allo schema nei database di pubblicazione](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [Modifiche allo schema nei database di pubblicazione](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  