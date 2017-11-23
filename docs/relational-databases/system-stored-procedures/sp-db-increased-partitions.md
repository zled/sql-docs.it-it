---
title: sp_db_increased_partitions | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_db_increased_partitions_TSQL
- sp_db_increased_partitions
dev_langs: TSQL
helpviewer_keywords: sp_db_increased_partitions
ms.assetid: a8c043ec-b504-4929-ac0e-8babaa99d989
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5266ce8c25465b6fd398111e7fd7e2d6634f5f34
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spdbincreasedpartitions"></a>sp_db_increased_partitions
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente di abilitare e disabilitare il supporto per partizioni fino a 15.000 per il database specificato.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2 tramite [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP1 e versioni successive). Per ulteriori informazioni, vedere [il supporto per 15.000 partizioni in SQL Server 2008 SP2 e SQL Server 2008 R2 SP1](http://go.microsoft.com/fwlink/p/?LinkId=299658),|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_dp_increased_partitions   
[ @dbname ] = 'database_name'   
[ , [ @increased_partitions = ] 'increased_partitions' ] [;]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @dbname=] '*database_name*'  
 Nome del database. *dbname* è **sysname** con un valore predefinito null. Se *dbname* viene omesso, viene utilizzato il database corrente.  
  
 [ @increased_partitions=] '*increased_partitions*'  
 Consente di abilitare e disabilitare il supporto per partizioni fino a 15.000 sul database specificato. *increased_partitions* è **varchar(6)** con un valore predefinito è NULL. I valori accettati per abilitare il supporto sono 'ON' o 'TRUE' e 'OFF' o 'FALSE' per disabilitarlo. Se *increased_partitions* non è specificato, la procedura restituisce 1 per indicare che è abilitato il supporto per il database specificato o 0 per indicare il supporto è disabilitato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER DATABASE per il database specificato.  
  
  
