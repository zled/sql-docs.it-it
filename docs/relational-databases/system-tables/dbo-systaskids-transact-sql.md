---
title: dbo.systaskids (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- systaskids_TSQL
- dbo.systaskids
- systaskids
- dbo.systaskids_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- systaskids system table
ms.assetid: 45c56d89-4160-4d84-80bf-a7a05488792d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a40bd9acc3961a77cb69bc24fc37f5e89192c34a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47802265"
---
# <a name="dbosystaskids-transact-sql"></a>dbo.systaskids (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene un mapping delle attività create in versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] su processi di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] nella versione corrente. Questa tabella è archiviata nel **msdb** database.  
  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**task_id**|**int**|ID dell'attività|  
|**job_id**|**uniqueidentifier**|ID del processo a cui si esegue il mapping dell'attività|  
  
  
