---
title: managed_backup.fn_is_master_switch_on (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_is_master_switch_on
- fn_is_master_switch_on_TSQL
- smart_admin.fn_is_master_switch_on
- smart_admin.fn_is_master_switch_on_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_is_master_switch_on
- fn_is_master_switch_on
ms.assetid: e8c2108d-b104-46cb-9645-a15f46112c86
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 87e9ad348eabfad30d556a88dfade8417684469a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38038769"
---
# <a name="managedbackupfnismasterswitchon-transact-sql"></a>managed_backup.fn_is_master_switch_on (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Restituisce lo stato delle operazioni del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] nell'istanza di SQL Server.  
  
 Utilizzare questa funzione per ottenere lo stato corrente del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
managed_backup.fn_is_master_switch_on ()  
```  
  
##  <a name="Arguments"></a> Argomenti  
 None  
  
## <a name="return-type"></a>Tipo restituito  
 **BIT**  
  
 1 = [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] è attivo, 0 = [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] è sospeso.  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Autorizzazioni  
 Sono richieste le autorizzazioni SELECT per la funzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Backup gestito di SQL Server in Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
