---
title: sp_pdw_database_encryption (SQL Data Warehouse) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: system-stored-procedures
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f5ccb424-7a95-4557-b774-c69de33c1545
caps.latest.revision: 8
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: adb48589c9ba6268aa229cd21871504392151f8e
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
ms.locfileid: "33703134"
---
# <a name="sppdwdatabaseencryption-sql-data-warehouse"></a>sp_pdw_database_encryption (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Utilizzare **sp_pdw_database_encryption** per abilitare transparent data encryption in per un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] accessorio. Quando **sp_pdw_database_encryption** impostata su 1, utilizzare il **ALTER DATABASE** istruzione per crittografare un database tramite Transparent Data Encryption.  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption [ [ @enabled = ] enabled ] ;  
```  
  
#### <a name="parameters"></a>Parametri  
 [  **@enabled=** ] *abilitato*  
 Determina se transparent data encryption è abilitato. *abilitata* viene **int**, e può essere uno dei valori seguenti:  
  
-   0 = Disabilitato  
  
-   1 = Attivato  
  
 L'esecuzione di **sp_pdw_database_encryption** senza parametri, viene restituito lo stato corrente di TDE nel dispositivo come un set di risultati scalari: 0 per disabilitato o 1 per abilitato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Quando la funzionalità TDE è abilitata utilizzando **sp_pdw_database_encryption**, il database tempdb viene eliminato, ricreato e crittografato. Per questo motivo, di Transparent Data Encryption non è abilitato su un dispositivo mentre sono presenti altre sessioni attive, l'utilizzo di tempdb. Abilitazione o disabilitazione di TDE in un dispositivo è un'azione che modifica lo stato del dispositivo, nella maggior parte dei casi deve essere eseguita una volta nel corso della durata di dispositivo e deve essere eseguita quando non viene rilevato traffico nel dispositivo.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **sysadmin** ruolo predefinito del database, o **CONTROL SERVER** autorizzazione.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente Abilita TDE nel dispositivo.  
  
```sql  
EXEC sys.sp_pdw_database_encryption 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)   
 [sp_pdw_log_user_data_masking &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
