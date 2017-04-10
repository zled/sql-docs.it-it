---
title: "Importazione bulk di dati di tipo LOB tramite il provider di set di righe con lettura bulk OPENROWSET (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-bulk-import-export"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SINGLE_NCLOB - opzione"
  - "provider di set di righe con lettura bulk [SQL Server]"
  - "importazione bulk [SQL Server], formati dati"
  - "funzione OPENROWSET, importazione bulk di dati di grandi dimensioni"
  - "SINGLE_CLOB - opzione"
  - "formati di dati [SQL Server], dati per oggetti di grandi dimensioni"
  - "dati di grandi dimensioni, importazione bulk"
  - "SINGLE_BLOB - opzione"
ms.assetid: 171cdd5c-1e47-4bd7-b99a-4f0fd4e10526
caps.latest.revision: 16
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Importazione bulk di dati di tipo LOB tramite il provider di set di righe con lettura bulk OPENROWSET (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Il provider di set di righe con lettura bulk OPENROWSET di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente di eseguire un'importazione bulk di un file di dati come dati di grandi dimensioni (LOB, Large Object).  
  
 I tipi di dati LOB (Large Object) supportati dal provider di tipo bulk per set di righe OPENROWSET sono **varbinary**(max) o **image**, **varchar**(max) o **text** e **nvarchar**(max) o **ntext**.  
  
> [!NOTE]  
>  I tipi di dati **image**, **text** e **ntext** sono deprecati.  
  
 La clausola OPENROWSET BULK supporta tre opzioni per l'importazione del contenuto di un file di dati sotto forma di set di righe caratterizzato da una sola riga e una sola colonna. È possibile specificare una di queste opzioni relative ai dati di tipo LOB, invece di utilizzare un file di formato. Le opzioni disponibili sono le seguenti:  
  
 SINGLE_BLOB  
 Legge il contenuto di *data_file* come un'unica riga e restituisce il contenuto come set di righe di tipo **varbinary(max)** con una sola colonna.  
  
 SINGLE_CLOB  
 Legge il contenuto del file di dati specificato come caratteri e restituisce il contenuto come set di righe di tipo **varchar(max)** con una sola riga e una sola colonna, usando le regole di confronto del database corrente, ad esempio un documento di testo o di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word.  
  
 SINGLE_NCLOB  
 Legge il contenuto del file di dati specificato come Unicode e restituisce il contenuto come set di righe di tipo **nvarchar(max)** con una sola riga e una sola colonna, usando le regole di confronto del database corrente.  
  
## Vedere anche  
 [Importazione di dati per operazioni bulk utilizzando BULK INSERT o OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [Mantenimento dei valori Null o utilizzo dei valori predefiniti durante un'importazione bulk &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)   
 [Utilità bcp](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)  
  
  