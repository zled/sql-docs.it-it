---
title: sp_rda_reconcile_columns (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_columns
- sys.sp_rda_reconcile_columns_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.sp_rda_reconcile_columns stored procedure
ms.assetid: 60d9cc4e-1828-450b-9d88-5b8485800d73
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6bae454caa630025bb4470dc69da7fa4a97f6307
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="syssprdareconcilecolumns-transact-sql"></a>sp_rda_reconcile_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Riconcilia le colonne nella tabella di Azure remota per le colonne di tabella di SQL Server abilitata per l'estensione.  
    
  **sp_rda_reconcile_columns** aggiunge colonne alla tabella remota presenti nella tabella di SQL Server abilitata per l'estensione, ma non nella tabella remota. Le colonne possono essere colonne accidentalmente eliminate dalla tabella remota. Tuttavia, **sp_rda_reconcile_columns** non eliminare le colonne della tabella remota presenti nella tabella remota, ma non nella tabella di SQL Server.
  
  > [!IMPORTANT]
  > Quando **sp_rda_reconcile_columns** crea nuovamente le colonne accidentalmente eliminate dalla tabella remota, non ripristina i dati che erano presenti nelle colonne eliminate.
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_rda_reconcile_columns @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Argomenti  
 @objname = '*@objname*'  
 Il nome della tabella abilitata per l'estensione di SQL Server.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o >0 (esito negativo)  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede autorizzazioni db_owner.  
   
## <a name="remarks"></a>Osservazioni  
 Se sono presenti colonne nella tabella remota di Azure che non esistono più nella tabella di SQL Server abilitata per Stretch, queste colonne aggiuntive non impediscono il normale funzionamento di Stretch Database. È possibile rimuovere le colonne aggiuntive manualmente.  
  
## <a name="example"></a>Esempio  
 Per risolvere le differenze tra le colonne nella tabella di Azure remota, eseguire l'istruzione seguente.  
  
```sql  
EXEC sp_rda_reconcile_columns @objname = N'StretchEnabledTableName';  
```  
  
  
