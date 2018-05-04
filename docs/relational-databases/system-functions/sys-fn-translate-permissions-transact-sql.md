---
title: sys.fn_translate_permissions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.fn_translate_permissions
- sys.fn_translate_permissions_TSQL
- fn_translate_permissions
- fn_translate_permissions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- permissions bitmask [SQL Server]
- sys.fn_translate_permissions function
- fn_translate_permissions function
ms.assetid: ac97121f-2bd0-4f71-8e45-42c8584edbc5
caps.latest.revision: 18
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 33aa7684e95d2fecdd9f28f497c8ca2d68ce1115
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysfntranslatepermissions-transact-sql"></a>sys.fn_translate_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Converte la maschera di bit delle autorizzazioni restituita da Traccia SQL in una tabella di nomi delle autorizzazioni.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.fn_translate_permissions ( level , perms )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Livello*  
 Tipo di entità a protezione diretta a cui viene applicata l'autorizzazione. *livello* viene **nvarchar(60)**.  
  
 *perms*  
 Maschera di bit restituita nella colonna delle autorizzazioni. *Perms* viene **varbinary(16)**.  
  
## <a name="returns"></a>Valori di codice restituiti  
 **table**  
  
## <a name="remarks"></a>Osservazioni  
 Il valore restituito nel **autorizzazioni** colonna di traccia SQL è una rappresentazione di integer di una maschera di bit utilizzato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per calcolare le autorizzazioni valide. Tutti i 25 tipi di entità a protezione diretta dispongono di un proprio set di autorizzazioni con valori numerici corrispondenti. **Sys. fn_translate_permissions** Converte questa maschera di bit in una tabella di nomi di autorizzazioni.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="example"></a>Esempio  
 La query seguente utilizza `sys.fn_builtin_permissions` per visualizzare le autorizzazioni che si applicano ai certificati e quindi utilizza `sys.fn_translate_permissions` per restituire i risultati della maschera di bit delle autorizzazioni.  
  
```  
SELECT * FROM sys.fn_builtin_permissions('CERTIFICATE');  
SELECT '0001' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0001);  
SELECT '0010' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0010);  
SELECT '0011' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0011);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [sys.server_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)   
 [sys.database_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)  
  
  
