---
title: "Specifica dei mapping tra i tipi di dati di un server di pubblicazione Oracle | Microsoft Docs"
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
  - "pubblicazione Oracle [replica di SQL Server], mapping dei tipi di dati"
  - "tipi di dati [replica di SQL Server], pubblicazione Oracle"
  - "mapping di tipi di dati [replica di SQL Server]"
ms.assetid: f172d631-3b8c-4912-bd0f-568366cd9870
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Specifica dei mapping tra i tipi di dati di un server di pubblicazione Oracle
  In questo argomento viene descritto come specificare i mapping dei tipi di dati per un server di pubblicazione Oracle in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Anche se per i server di pubblicazione Oracle è disponibile un set di mapping predefiniti di tipi di dati, può essere necessario specificare mapping diversi per una determinata pubblicazione.  
  
 **Contenuto dell'argomento**  
  
-   **Per specificare i mapping dei tipi di dati per un server di pubblicazione Oracle, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Specificare i mapping dei tipi di dati nel **Mapping dei dati** scheda il **Proprietà articolo - \< articolo>** la finestra di dialogo. Questo comando è disponibile il **articoli** pagina della creazione guidata pubblicazione e la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'utilizzo della procedura guidata e l'accesso nella finestra di dialogo, vedere [creare una pubblicazione da un Database Oracle](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md) e [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Per specificare un mapping tra i tipi di dati  
  
1.  Nel **articoli** pagina della procedura guidata nuova pubblicazione o **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare una tabella e quindi fare clic su **Proprietà articolo**.  
  
2.  Fare clic su **Imposta proprietà dell'articolo tabella evidenziato**.  
  
3.  Nel **Mapping dei dati** scheda della finestra il **Proprietà articolo - \< articolo>** la finestra di dialogo, selezionare i mapping dal **tipo di dati del sottoscrittore** colonna:  
  
    -   Per alcuni tipi di dati è disponibile un solo tipo di mapping. In questo caso, la colonna nella proprietà è di sola lettura.  
  
    -   Per alcuni tipi è possibile selezionare più tipi di mapping. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] consiglia di utilizzare il mapping predefinito, a meno che l'applicazione utilizzata non richieda un tipo di mapping diverso. Per altre informazioni, vedere [Data Type Mapping for Oracle Publishers](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile specificare mapping personalizzati di tipi di dati a livello di programmazione tramite le stored procedure di replica. È inoltre possibile impostare i mapping predefiniti che vengono utilizzati quando i tipi di dati di mapping tra [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database (DBMS) di sistema di gestione. Per altre informazioni, vedere [Data Type Mapping for Oracle Publishers](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md).  
  
#### Per definire mapping personalizzati di tipi di dati durante la creazione di un articolo appartenente a una pubblicazione Oracle  
  
1.  Se non esiste già, creare una pubblicazione Oracle.  
  
2.  Nel server di distribuzione, eseguire [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Specificare un valore di **0** per **@use_default_datatypes**. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Nel server di distribuzione, eseguire [sp_helparticlecolumns](../../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md) per visualizzare il mapping esistente per una colonna in un articolo pubblicato.  
  
4.  Nel server di distribuzione, eseguire [sp_changearticlecolumndatatype](../../../relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **@publisher**, nonché **@publication**, **@article**e **@column** per definire la colonna pubblicata. Specificare il nome del tipo di dati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] di cui eseguire il mapping per **@type**, nonché **@length**, **@precision**e **@scale**se applicabile.  
  
5.  Nel server di distribuzione, eseguire [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). In questo modo verrà creata la vista utilizzata per generare lo snapshot dalla pubblicazione Oracle.  
  
#### Per specificare un mapping come mapping predefinito per un tipo di dati  
  
1.  (Facoltativo) Nel server di distribuzione in qualsiasi database, eseguire [sp_getdefaultdatatypemapping](../../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md). Specificare **@source_dbms**, **@source_type**, **@destination_dbms**, **@destination_version**, e qualsiasi altro parametro necessario per identificare il DBMS di origine. Le informazioni sui tipi di dati attualmente sottoposti a mapping nel sistema DBMS di destinazione vengono restituite tramite parametri di output.  
  
2.  (Facoltativo) Nel server di distribuzione in qualsiasi database, eseguire [sp_helpdatatypemap](../../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md). Specificare **@source_dbms** e qualsiasi altro parametro necessario per filtrare il set di risultati. Prendere nota del valore di **mapping_id** impostato per il mapping desiderato nel risultato.  
  
3.  Nel server di distribuzione in qualsiasi database, eseguire [sp_setdefaultdatatypemapping](../../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md).  
  
    -   Se si conosce il valore desiderato di **mapping_id** ottenuto nel passaggio 2, specificarlo per **@mapping_id**.  
  
    -   Se non si conosce il **mapping_id**, specificare i parametri **@source_dbms**, **@source_type**, **@destination_dbms**, **@destination_type**, e qualsiasi altro parametro necessario per identificare un mapping esistente.  
  
#### Per trovare tipi di dati validi per un determinato tipo di dati Oracle  
  
1.  Nel server di distribuzione in qualsiasi database, eseguire [sp_helpdatatypemap](../../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md). Specificare un valore di **ORACLE** per **@source_dbms** e qualsiasi altro parametro necessario per filtrare il set di risultati.  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 In questo esempio viene modificata una colonna con tipo di dati Oracle e del numero in modo che venga mappato a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati **numerico**(38,38) anziché il tipo di dati predefinito **float**.  
  
 [!code-sql[HowTo#sp_changecolumndatatype](../../../relational-databases/replication/codesnippet/tsql/specify-data-type-mappin_1.sql)]  
  
 In questo esempio di query vengono restituiti i mapping predefiniti e alternativi per il tipo di dati **CHAR**di Oracle 9.  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_char](../../../relational-databases/replication/codesnippet/tsql/specify-data-type-mappin_2.sql)]  
  
 In questo esempio di query vengono restituiti i mapping predefiniti per il tipo di dati **NUMBER** di Oracle 9 quando viene specificato senza scala o precisione.  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_number](../../../relational-databases/replication/codesnippet/tsql/specify-data-type-mappin_3.sql)]  
  
## Vedere anche  
 [Mapping dei tipi di dati per i server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Replica di database eterogenei](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Configurazione di un server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)  
  
  