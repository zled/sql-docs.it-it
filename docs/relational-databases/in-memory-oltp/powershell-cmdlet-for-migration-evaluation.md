---
title: "Cmdlet di PowerShell per la valutazione della migrazione | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 117250d3-9982-47fe-94fd-6f29f6159940
caps.latest.revision: 5
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 5
---
# Cmdlet di PowerShell per la valutazione della migrazione
  Il cmdlet Save-SqlMigrationReport è uno strumento che valuta l'idoneità per la migrazione di più oggetti in un database di SQL Server. Attualmente è limitato alla valutazione di OLTP in memoria. Il cmdlet può essere eseguito sia in un ambiente Windows PowerShell con privilegi elevati che in sqlps.  
  
## Sintassi  
  
```powershell  
Save-SqlMigrationReport [ -MigrationType OLTP ] [ -Server server -Database database [ -Object object_name ] ]  |  [ -InputObject smo_object ] -FolderPath path  
```  
  
#### Parametri  
 I parametri sono descritti nella tabella riportata di seguito.  
  
|Parametri|Descrizione|  
|----------------|-----------------|  
|MigrationType|Tipo di scenario di migrazione specificato come destinazione dal cmdlet. Attualmente l'unico valore è il valore predefinito OLTP. Facoltativa.|  
|Server|Nome dell'istanza di SQL Server di destinazione. Obbligatorio nell'ambiente Windows Powershell se non viene specificato il parametro -InputObject. Facoltativo in SQLPS.|  
|Database|Nome del database di SQL Server di destinazione. Obbligatorio nell'ambiente Windows Powershell se non viene specificato il parametro -InputObject. Facoltativo in SQLPS.|  
|Object|Nome dell'oggetto di database di destinazione. Può essere una tabella o una stored procedure.|  
|InputObject|Oggetto SMO a cui il cmdlet deve fare riferimento. Obbligatorio nell'ambiente Windows Powershell se non vengono specificati -Server e -Database. Facoltativo in SQLPS.|  
|FolderPath|Cartella in cui il cmdlet deve depositare i report generati. Obbligatorio.|  
  
## Risultati  
 La cartella specificata nel parametro -FolderPath conterrà due nomi di cartella: Tables e Stored procedures. Se l'oggetto di destinazione è una tabella, il report sarà all'interno della cartella Tables. In caso contrario, sarà all'interno della cartella Stored procedures.  
  
  