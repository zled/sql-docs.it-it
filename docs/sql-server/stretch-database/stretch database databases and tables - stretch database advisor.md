---
title: "Identificare i database e le tabelle per Estensione database eseguendo Stretch Database Advisor | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-server-stretch-database"
ms.suite: ""
ms.technology: 
  - "dbe-stretch"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Estensione database, identificazione di database"
  - "Estensione database, identificazione di tabelle"
  - "identificazione di database per Estensione database"
  - "identificazione di tabelle per Estensione database"
ms.assetid: 81bd93d8-eef8-4572-88d7-5c37ab5ac2bf
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# Identificare i database e le tabelle per Estensione database eseguendo Stretch Database Advisor
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Per identificare i database e le tabelle candidati per Estensione database, scaricare SQL Server 2016 Upgrade Advisor ed eseguire Stretch Database Advisor. Stretch Database Advisor identifica anche i problemi di blocco.  
  
## Scaricare e installare Upgrade Advisor  
 Scaricare Upgrade Advisor [qui](http://go.microsoft.com/fwlink/?LinkID=613421)e installarlo. Questo strumento non è incluso nel supporto di installazione [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] .  
  
## Eseguire Stretch Database Advisor  
  
1.  Eseguire Upgrade Advisor.  
  
2.  Selezionare **Scenarios**(Scenari) e quindi **RUN STRETCH DATABASE ADVISOR**(ESEGUI STRETCH DATABASE ADVISOR).  
  
3.  Nel pannello **Run Stretch Database Advisor** (Esegui Stretch Database Advisor) fare clic su **SELECT DATABASES TO ANALYZE**(SELEZIONA I DATABASE DA ANALIZZARE).  
  
4.  Nel pannello **Seleziona database** immettere o selezionare il nome del server e le informazioni di autenticazione. Fare clic su **Connetti**.

5.  Viene visualizzato un elenco dei database nel server selezionato. Selezionare i database che si vuole analizzare. Fare clic su **Seleziona**.  
  
6.  Nel pannello **Run Stretch Database Advisor** (Esegui Stretch Database Advisor) fare clic su **Run**(Esegui).  Viene eseguita l'analisi.  
  
## Controllare i risultati  
  
1.  Al termine dell'analisi, nel pannello **Analyzed databases** (Database analizzati) selezionare uno dei database analizzati in modo da visualizzare il pannello **Analysis results** (Risultati analisi).  
  
     Il pannello **Analysis results** (Risultati analisi) elenca le tabelle consigliate nel database selezionato che soddisfano i criteri di raccomandazione predefiniti. 
  
2.  Nell'elenco delle tabelle consigliate nel pannello **Analysis results** (Risultati analisi) selezionare una delle tabelle consigliate in modo da visualizzare il pannello **Table results** (Risultati tabella).  
  
     Se sono presenti problemi di blocco, il pannello **Table results** (Risultati tabella) li elenca per la tabella selezionata. Per informazioni sui problemi di blocco rilevati da Stretch Database Advisor, vedere [Limitazioni per Estensione database](../../sql-server/stretch-database/limitations-for-stretch-database.md).  
  
3.  Nel pannello **Table results** (Tabella risultati) dell'elenco dei problemi di blocco selezionare uno dei problemi per visualizzare altre informazioni sul problema selezionato e le procedure di attenuazione proposte. Se si desidera configurare la tabella selezionata per Estensione database, implementare i passaggi di attenuazione suggeriti.  
  
## Passaggio successivo  
 Abilitare Estensione database.  
  
-   Per abilitare Estensione database in un **database**, vedere [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
-   Per abilitare Estensione database in un'altra **tabella**, quando l'estensione è già abilitata nel database, vedere [Enable Stretch Database for a table](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md).  
  
## Vedere anche  
 [Limitazioni per Estensione database](../../sql-server/stretch-database/limitations-for-stretch-database.md)   
 [Abilitare Estensione database per un database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [Abilitare Estensione database per una tabella](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)  
  
  