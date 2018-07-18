---
title: sys.sp_rda_reconcile_batch (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_batch
- sys.sp_rda_reconcile_batch_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_batch stored procedure
ms.assetid: 6d21eac3-7b6c-4fe0-8bc4-bf503f3948a6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 190c1ef35e8269cd909bfe6a8c17a7d360ae1041
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409570"
---
# <a name="syssprdareconcilebatch-transact-sql"></a>sys.sp_rda_reconcile_batch (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Risolve le differenze tra l'ID batch archiviato nella tabella abilitata per l'estensione SQL Server con l'ID batch archiviato nella tabella di Azure remota.  
  
 In genere è sufficiente eseguire **sp_rda_reconcile_batch** se è stato eliminato manualmente i dati migrati più recente della tabella remota. Quando si eliminano manualmente i dati remoti che includono il batch più recente, gli ID batch non sono sincronizzati e la migrazione si arresta.  
 
 Per eliminare i dati che sono già stati migrati in Azure, vedere la sezione Osservazioni in questa pagina.
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_rda_reconcile_batch @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Argomenti  
 @objname = '*@objname*'  
 Il nome della tabella abilitata per l'estensione SQL Server.  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede autorizzazioni db_owner.  
  
## <a name="remarks"></a>Note  
 Se si desidera eliminare i dati che sono già stati migrati in Azure, eseguire le operazioni seguenti.  
  
1.  Sospendere la migrazione dei dati. Per altre informazioni, vedere [Sospendere e riprendere la migrazione dei dati &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
2.  Eliminare i dati dalla tabella di staging di SQL Server eseguendo un comando di eliminazione con l'hint STAGE_ONLY. Per altre informazioni, vedi [rendere amministrativi aggiornamenti ed eliminazioni](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md#adminHints).
  
3.  Eliminare gli stessi dati dalla tabella di Azure remota eseguendo un comando di eliminazione con l'hint REMOTE_ONLY.  
  
4.  Eseguire **sp_rda_reconcile_batch**.  
  
5.  Riprendere la migrazione dei dati. Per altre informazioni, vedere [Sospendere e riprendere la migrazione dei dati &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
## <a name="example"></a>Esempio  
 Per risolvere le differenze tra l'ID batch, eseguire l'istruzione seguente.  
  
```sql  
EXEC sp_rda_reconcile_batch @objname = N'StretchEnabledTableName';  
```  
  
  
