---
title: sp_pdw_database_encryption_regenerate_system_keys (SQL Data Warehouse) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: system-stored-procedures
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: bb13e323-a984-4462-8b6d-6019c38ddd9d
caps.latest.revision: "8"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 94f45c520397c608845e9bd07ec4aed173d1fd91
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sppdwdatabaseencryptionregeneratesystemkeys-sql-data-warehouse"></a>sp_pdw_database_encryption_regenerate_system_keys (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Utilizzare **sp_pdw_database_encryption_regenerate_system_keys** per ruotare la chiave di crittografia del database e del certificato per il database interni che vengono crittografati quando TDE è abilitata nel dispositivo. incluso `tempdb`. Questo avrà esito positivo solo se TDE è abilitata.  
  
## <a name="syntax"></a>Sintassi  
  
```tsql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption_regenerate_system_keys  ;  
```  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 La procedura non ha parametri.  
  
 Questa procedura deve essere utilizzata quando il traffico nel dispositivo è insufficiente.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza di **sysadmin** ruolo predefinito del database, o **CONTROL SERVER** autorizzazione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente consente di rigenerare le chiavi di crittografia del database.  
  
```tsql  
EXEC sys.sp_pdw_database_encryption_regenerate_system_keys;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_pdw_database_encryption &#40; SQL Data Warehouse &#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_log_user_data_masking &#40; SQL Data Warehouse &#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
