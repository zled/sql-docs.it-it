---
title: sp_xtp_flush_temporal_history | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server (starting with 2016 CTP3)
f1_keywords:
- sp_xtp_flush_temporal_history
- sp_xtp_flush_temporal_history_TSQL
- sys.sp_xtp_flush_temporal_history
- sys.sp_xtp_flush_temporal_history_TSQL
helpviewer_keywords:
- sp_xtp_flush_temporal_history
ms.assetid: 322e3170-93f8-468a-a123-104ce7bd7fad
caps.latest.revision: 7
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1e4ea75e11840c91e6fcac81d43a33272d9882bf
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38045909"
---
# <a name="spxtpflushtemporalhistory-transact-sql"></a>sp_xtp_flush_temporal_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Richiama l'attività di scaricamento dei dati per spostare tutti i commit di righe dalla tabella di staging in memoria per la tabella di cronologia basata su disco.  

 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.sp_xtp_flush_temporal_history @schema_name, @object_name  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *@schema_name*  
 Il nome dello schema per la tabella temporale o corrente  
  
 *@object_name*  
 Il nome della tabella temporale o corrente  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o >0 (esito negativo)  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede autorizzazioni db_owner.  
  
## <a name="see-also"></a>Vedere anche  
 [Considerazioni sulle prestazioni con le tabelle temporali con controllo delle versioni di sistema e ottimizzazione per la memoria](../../relational-databases/tables/memory-optimized-system-versioned-temporal-tables-performance.md)  
  
  
