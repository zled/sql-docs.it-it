---
title: dbo.syscategories (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
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
- dbo.syscategories_TSQL
- syscategories
- syscategories_TSQL
- dbo.syscategories
dev_langs:
- TSQL
helpviewer_keywords:
- syscategories system table
ms.assetid: eb2cb75c-dc58-4a5b-b329-664e9fe20ce0
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fb2c9c6f9163ad1c624aff66e6341db4a29dbeb7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="dbosyscategories-transact-sql"></a>dbo.syscategories (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene le categorie utilizzate da [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per organizzare processi, avvisi e operatori. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|ID della categoria.|  
|**category_class**|**int**|Tipo di elemento della categoria:<br /><br /> **1** = Job<br /><br /> **2** = avviso<br /><br /> **3** = (operatore)|  
|**category_type**|**tinyint**|Tipo di categoria:<br /><br /> **1** = locale<br /><br /> **2** = multiserver<br /><br /> **3** = nessuno|  
|**name**|**sysname**|Nome della categoria.|  
  
  
