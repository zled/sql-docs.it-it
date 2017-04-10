---
title: "Visualizzare o modificare il livello di compatibilit&#224; di un database | Microsoft Docs"
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
  - "livelli di compatibilità [SQL Server], visualizzazione"
  - "compatibilità di database [SQL Server]"
  - "livelli di compatibilità [SQL Server], modifica"
ms.assetid: 579867ec-57cb-4cb8-af35-9688c1e9e15d
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Visualizzare o modificare il livello di compatibilit&#224; di un database
  In questo argomento si illustra come visualizzare o modificare il livello di compatibilità di un database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Prima di modificare il livello di compatibilità di un database, è importante comprendere quale impatto avrà la modifica sulle applicazioni. Per altre informazioni, vedere [Livello di compatibilità di ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Compatibility%20Level%20\(Transact-SQL\).md).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per visualizzare o modificare il livello di compatibilità di un database utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione ALTER per il database.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per visualizzare o modificare il livello di compatibilità di un database  
  
1.  Dopo essersi connessi all'istanza appropriata del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Esplora oggetti fare clic sul nome del server.  
  
2.  Espandere **Database**e, a seconda del database, selezionare un database utente o espandere **Database di sistema** e selezionare un database di sistema.  
  
3.  Fare clic con il pulsante destro del mouse sul database, quindi scegliere **Proprietà**.  
  
     Verrà visualizzata la finestra di dialogo **Proprietà database** .  
  
4.  Nel riquadro **Selezione pagina** fare clic su **Opzioni**.  
  
     Il livello di compatibilità corrente viene visualizzato nella casella di riepilogo **Livello di compatibilità** .  
  
5.  Per modificare il livello di compatibilità, selezionare un'opzione diversa dall'elenco. Scegliere tra **SQL Server 2008 (100)**, **SQL Server 2012 (110)** o **SQL Server 2014 (120)**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per visualizzare il livello di compatibilità di un database  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio viene restituito il livello di compatibilità del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### Per modificare il livello di compatibilità di un database  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio si imposta il livello di compatibilità del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] su `120,` cioè il livello di compatibilità per [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
```tsql  
ALTER DATABASE AdventureWorks2012  
SET COMPATIBILITY_LEVEL = 120;  
GO  
```  
  
  