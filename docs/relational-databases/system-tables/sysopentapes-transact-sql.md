---
title: sysopentapes (Transact-SQL) | Documenti Microsoft
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
- sysopentapes
- sysopentapes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup media [SQL Server], sysopentapes system table
- sysopentapes system table
ms.assetid: c066ca9b-9cfd-46b1-90a3-5c8dc9e7b6ae
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f6b3221df17bdfda65987fe1dfea825868d050c2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysopentapes-transact-sql"></a>sysopentapes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni dispositivo nastro attualmente aperto. Questa vista è archiviata nel **master** database.  
  
> [!IMPORTANT]  
>  Questa tabella di sistema è disponibile come vista per la compatibilità con le versioni precedenti. In alternativa, usare il [DM io_backup_tapes &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md) vista a gestione dinamica.  
  
> [!NOTE]  
>  Non è possibile eliminare il **sysopentapes** visualizzazione.  

  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**openTape**|**nvarchar(64)**|Nome di file fisico del dispositivo nastro aperto. Per ulteriori informazioni sull'apertura e di rilascio di dispositivi nastro, vedere [BACKUP &#40;Transact-SQL&#41; ](../../t-sql/statements/backup-transact-sql.md) e [ripristinare &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md).|  
  
## <a name="permissions"></a>Autorizzazioni  
 L'utente deve disporre dell'autorizzazione VIEW SERVER STATE nel server.  
  
  
