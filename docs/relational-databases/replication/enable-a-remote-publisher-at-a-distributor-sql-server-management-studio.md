---
title: "Abilitazione di un server di pubblicazione remoto in un database di distribuzione (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "server di distribuzione remoti [replica di SQL Server]"
  - "server di pubblicazione [replica di SQL Server]"
ms.assetid: 6f8e2831-5c45-4e39-8e51-d37e2813cf3d
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# Abilitazione di un server di pubblicazione remoto in un database di distribuzione (SQL Server Management Studio)
  Attivare un server di pubblicazione per l'utilizzo di un server di distribuzione remoto nella pagina **Server di pubblicazione** . Questa pagina è disponibile in Configurazione guidata distribuzione e la **proprietà server di distribuzione - \< distributore>** la finestra di dialogo. Per ulteriori informazioni sull'utilizzo della procedura guidata e l'accesso nella finestra di dialogo, vedere [Configura pubblicazione e distribuzione](../../relational-databases/replication/configure-publishing-and-distribution.md) e [visualizzare e modificare server di distribuzione e le proprietà server di pubblicazione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### Per attivare un server di pubblicazione nella Configurazione guidata distribuzione  
  
1.  Nella pagina **Server di pubblicazione** della Configurazione guidata distribuzione fare clic su **Aggiungi**.  
  
2.  Fare clic su **Aggiungi server di pubblicazione SQL Server**. Per informazioni sull'attivazione di un server di pubblicazione Oracle per l'utilizzo di un server di distribuzione, vedere [Create a Publication from an Oracle Database](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
3.  Nella finestra di dialogo **Connetti al server** specificare le informazioni sulla connessione del server di pubblicazione che utilizzerà il server di distribuzione remoto e fare clic su **Connetti**.  
  
4.  Nel **Password server di distribuzione** nella pagina di **Password** e **Conferma password** caselle di testo, specificare una password complessa per il **distributor_admin** conto, quali la replica utilizza per la connessione dal server di pubblicazione al server di distribuzione per eseguire attività amministrative.  
  
5.  Per visualizzare e modificare le impostazioni per un server di pubblicazione, fare clic sul pulsante delle proprietà (**...**).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Per abilitare un server di pubblicazione nella finestra di dialogo Proprietà database di distribuzione  
  
1.  Nel **editori** pagina della **proprietà server di distribuzione - \< distributore>** nella finestra di dialogo fare clic su **Aggiungi**.  
  
2.  Fare clic su **Aggiungi server di pubblicazione SQL Server**. Per informazioni sull'attivazione di un server di pubblicazione Oracle per l'utilizzo di un server di distribuzione, vedere [Create a Publication from an Oracle Database](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
3.  Nella finestra di dialogo **Connetti al server** specificare le informazioni sulla connessione del server di pubblicazione che utilizzerà il server di distribuzione remoto e fare clic su **Connetti**.  
  
4.  Nel **editori** nella pagina di **Password** e **Conferma password** caselle di testo, specificare una password complessa per il **distributor_admin** account, quali la replica utilizza per la connessione dal server di pubblicazione al server di distribuzione per eseguire attività amministrative.  
  
5.  Per visualizzare e modificare le impostazioni per un server di pubblicazione, fare clic sul pulsante delle proprietà (**...**).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Vedere anche  
 [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Configurazione della distribuzione](../../relational-databases/replication/configure-distribution.md)   
 [Sicurezza del database di distribuzione](../../relational-databases/replication/security/secure-the-distributor.md)  
  
  