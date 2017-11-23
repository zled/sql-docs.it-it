---
title: Sys.sp_add_trusted_assembly (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/14/2017
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
- sp_add_trusted_assembly_TSQL
- sp_add_trusted_assembly
- sys.sp_add_trusted_assembly_TSQL
- sys.sp_add_trusted_assembly
dev_langs: TSQL
helpviewer_keywords: sys.sp_add_trusted_assembly
ms.assetid: 
caps.latest.revision: 
author: tmullaney
ms.author: thmullan;rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 91cedb6c140b9f969d1d33e4878788fa8b9dba92
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysspaddtrustedassembly-transact-sql"></a>Sys.sp_add_trusted_assembly (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Aggiunge un assembly all'elenco degli assembly attendibili per il server.

 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


## <a name="syntax"></a>Sintassi
```  
sp_add_trusted_assembly 
    [ @hash = ] 'value'
    [ , [ @description = ] 'description' ]
```  

## <a name="remarks"></a>Osservazioni  

Questa procedura consente di aggiungere un assembly di [sys.trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md).

## <a name="arguments"></a>Argomenti

[ @hash =] '*valore*'  
Il valore hash SHA2_512 dell'assembly da aggiungere all'elenco degli assembly attendibili per il server. Attendibile possono caricare gli assembly quando [elevata protezione CLR](../../database-engine/configure-windows/clr-strict-security.md) è abilitato, anche se l'assembly è firmato o il database non è contrassegnato come attendibile.

[ @description =] '*descrizione*'  
Descrizione definita dall'utente facoltativa dell'assembly. Si consiglia di utilizzare il nome canonico che consente di codificare il nome semplice, numero di versione, impostazioni cultura, chiave pubblica e l'architettura dell'assembly da considerare attendibile. Questo valore in modo univoco identifica l'assembly relativamente alla common language runtime (CLR) e corrisponde al valore clr_name nella Assemblies. 

## <a name="permissions"></a>Permissions

È richiesta l'appartenenza di `sysadmin` ruolo predefinito del server o `CONTROL SERVER` autorizzazione.

## <a name="examples"></a>Esempi  

L'esempio seguente aggiunge un assembly denominato `pointudt` all'elenco degli assembly attendibili per il server. Questi valori sono disponibili da [Assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md).     

```  
EXEC sp_add_trusted_assembly 0x8893AD6D78D14EE43DF482E2EAD44123E3A0B684A8873C3F7BF3B5E8D8F09503F3E62370CE742BBC96FE3394477214B84C7C1B0F7A04DCC788FA99C2C09DFCCC, 
N'pointudt, version=0.0.0.0, culture=neutral, publickeytoken=null, processorarchitecture=msil';
```  

## <a name="see-also"></a>Vedere anche  
  [Sys.sp_drop_trusted_assembly](sys-sp-drop-trusted-assembly-transact-sql.md)  
  [Sys.trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md)  
  [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)  
  [Sicurezza rigidi CLR](../../database-engine/configure-windows/clr-strict-security.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  

