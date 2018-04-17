---
title: sysssispackagefolders (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdtspackagefolders90
- sysdtspackagefolders90_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysssispackagefolders system table
ms.assetid: ddc4833f-27bf-4610-b739-d257961d17ac
caps.latest.revision: 22
author: douglasl
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 179e6c1241ccbe42528eae591696727c9cea541a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysssispackagefolders-transact-sql"></a>sysssispackagefolders (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni cartella logica nella gerarchia di cartelle che [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilizza. Queste cartelle vengono visualizzate in Esplora oggetti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dopo la connessione a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. In una cartella sono visualizzati i pacchetti archiviati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o nel file system.  
  
 Il **parentfolderid** colonna descrive la gerarchia di cartelle. La cartella nella parte superiore della gerarchia di cartelle contiene un valore null in **parentfolderid**.  
  
 Il **foldername** colonna contiene il nome delle cartelle visualizzate in Esplora oggetti.  
  
 Questa tabella è archiviata nel **msdb** database.  

  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**folderid**|**uniqueidentifier**|GUID della cartella.|  
|**parentfolderid**|**uniqueidentifier**|GUID della cartella padre.|  
|**FolderName**|**sysname**|Nome della cartella. Questo nome viene visualizzato nella gerarchia di cartelle in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
  
  
