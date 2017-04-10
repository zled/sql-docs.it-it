---
title: "Visualizzazione o modifica dei percorsi predefiniti per i file di dati e di log (SQL Server Management Studio) | Microsoft Docs"
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
  - "file di log [SQL Server], modifica del percorso predefinito"
  - "file di dati [SQL Server], modifica del percorso predefinito"
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
caps.latest.revision: 16
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Visualizzazione o modifica dei percorsi predefiniti per i file di dati e di log (SQL Server Management Studio)
  In questo argomento si descrive come visualizzare e modificare i percorsi predefiniti dei nuovi file di dati e di log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Il percorso predefinito viene ottenuto dal Registro di sistema. Dopo la modifica, il percorso viene utilizzato in tutti i nuovi database creati nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , se non è specificato un percorso diverso.  
  
 
##  <a name="Recommendations"></a> Indicazioni  
 La procedura consigliata per la protezione dei file di dati e di log consiste nel verificare che siano protetti da elenchi di controllo di accesso (ACL). Impostare gli elenchi di controllo di accesso a livello della radice in cui vengono creati i file.  
  
  
## Visualizzare o modificare i percorsi predefiniti per i file di database  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse sul server e scegliere **Proprietà**.  
  
2.  Nel riquadro sinistro della pagina Proprietà fare clic sulla scheda **Impostazioni database**.  
  
3.  Nel pannello **Percorsi predefiniti database**è possibile visualizzare i percorsi predefiniti correnti per i nuovi file di dati e di log. Per modificare un percorso predefinito, immettere un nuovo percorso predefinito nel campo **Dati** o **Log** oppure fare clic sul pulsante Sfoglia per individuare e selezionare un percorso.  
  
>**NOTA:** dopo aver modificato i percorsi predefiniti, è necessario arrestare e avviare il servizio SQL Server per completare la modifica.  
  
## Vedere anche  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Creare un database](../../relational-databases/databases/create-a-database.md)  
  
  