---
title: "Salvataggio di un piano di esecuzione in formato XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "piani di query XML [SQL Server]"
  - "apertura di piani di esecuzione"
  - "Showplan XML [SQL Server]"
  - "piani di esecuzione [SQL Server], salvataggio"
  - "salvataggio di piani di esecuzione"
ms.assetid: c439e53b-56f3-4442-97c6-dabd48a203d8
caps.latest.revision: 25
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 25
---
# Salvataggio di un piano di esecuzione in formato XML
  Utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per salvare piani di esecuzione come file XML e per aprirli e visualizzarli.  
  
 Per utilizzare la funzionalità dei piani di esecuzione in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], o per utilizzare le opzioni XML Showplan SET, è necessario che gli utenti dispongano delle autorizzazioni appropriate per eseguire la query [!INCLUDE[tsql](../../includes/tsql-md.md)] per la quale un piano di esecuzione è in fase di generazione ed è necessario inoltre che venga loro concessa l'autorizzazione SHOWPLAN per tutti i database cui fa riferimento la query.  
  
### Per salvare un piano di query utilizzando le opzioni XML Showplan SET  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] aprire un editor di query e connettersi a [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Attivare SHOWPLAN_XML con l'istruzione seguente:  
  
    ```  
    SET SHOWPLAN_XML ON;  
    GO  
    ```  
  
     Per abilitare STATISTICS XML, utilizzare l'istruzione seguente:  
  
    ```  
    SET STATISTICS XML ON;  
    GO  
    ```  
  
     SHOWPLAN_XML genera informazioni di compilazione relative al piano di esecuzione della query, ma non esegue la query. STATISTICS XML genera informazioni di run-time relative al piano di esecuzione della query ed esegue la query.  
  
3.  Eseguire una query. Esempio:  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SET SHOWPLAN_XML ON;  
    GO  
    -- Execute a query.  
    SELECT BusinessEntityID   
    FROM HumanResources.Employee  
    WHERE NationalIDNumber = '509647174';  
    GO  
    SET SHOWPLAN_XML OFF;  
    ```  
  
4.  Nel riquadro **Risultati** fare clic con il pulsante destro del mouse sullo **Showplan XML di Microsoft SQL Server** che contiene il piano di query e quindi fare clic su **Salva risultati con nome**.  
  
5.  Nella finestra di dialogo **Salva** \>risultati** <griglia o testo>**, nella casella **Salva come tipo** fare clic su **Tutti i file (\*.\*)**.  
  
6.  Nella casella **Nome file** immettere un nome nel formato \<nome**>.sqlplan** e quindi fare clic su **Salva**.  
  
### Per salvare un piano di esecuzione utilizzando le opzioni di SQL Server Management Studio  
  
1.  Generare un piano di esecuzione stimato o effettivo utilizzando [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Per altre informazioni, vedere [Visualizzare il piano di esecuzione stimato](../../relational-databases/performance/display-the-estimated-execution-plan.md) o [Visualizzare un piano di esecuzione effettivo](../../relational-databases/performance/display-an-actual-execution-plan.md).  
  
2.  Nella scheda **Piano di esecuzione** del riquadro dei risultati fare clic con il pulsante destro del mouse sul piano di esecuzione grafico e scegliere **Salva piano di esecuzione con nome**.  
  
     In alternativa, scegliere **Salva piano di esecuzione con nome** dal menu **File**.  
  
3.  Nella finestra di dialogo **Salva con nome** assicurarsi che **Salva come** sia impostato su **File piano di esecuzione (\*.sqlplan)**.  
  
4.  Nella casella **Nome file** immettere un nome nel formato \<nome**>.sqlplan** e quindi fare clic su **Salva**.  
  
### Per aprire un piano di query XML salvato in SQL Server Management Studio  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] scegliere **Apri** dal menu **File** e quindi fare clic su **File**.  
  
2.  Nella finestra di dialogo **Apri file** impostare **Tipo file** su **File piano di esecuzione (\*.sqlplan)** per generare un elenco filtrato dei file dei piani di query XML salvati.  
  
3.  Selezionare il file del piano di query XML da visualizzare e fare clic su **Apri**.  
  
     In alternativa, in Esplora risorse fare doppio clic su un file con estensione **.sqlplan**. Il piano viene aperto in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
## Vedere anche  
 [SET SHOWPLAN_XML &#40;Transact-SQL&#41;](../../t-sql/statements/set-showplan-xml-transact-sql.md)   
 [SET STATISTICS XML &#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-xml-transact-sql.md)  
  
  