---
title: sp_pdw_log_user_data_masking (SQL Data Warehouse) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-data-warehouse
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 43c63b42-03cb-4fb5-8362-ec3b7e22a590
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: c858d435aef7e86b40d50dc2232dced53adf6c4f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sppdwloguserdatamasking-sql-data-warehouse"></a>sp_pdw_log_user_data_masking (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Utilizzare **sp_pdw_log_user_data_masking** per abilitare la maschera dati utente [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività. La maschera dati utente interessa le istruzioni in tutti i database nel dispositivo.  
  
> [!IMPORTANT]  
>  Il [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività interessati **sp_pdw_log_user_data_masking** sono determinati [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività. **sp_pdw_log_user_data_masking** non influisce sui registri delle transazioni del database o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log degli errori.  
  
 **Sfondo:** nella configurazione predefinita [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività contengono completo [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni e in alcuni casi può includere i dati utente contenuti nelle operazioni, ad esempio **inserire**,  **AGGIORNAMENTO**, e **selezionare** istruzioni. In caso di un problema nel dispositivo, in tal modo l'analisi delle condizioni che ha causato il problema senza la necessità di riprodurre il problema. Per impedire che i dati utente scritti [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività, i clienti possono scegliere di attivare il mascheramento dei dati utente tramite questa stored procedure. Le istruzioni verranno ancora essere scritti [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività, ma tutti i valori letterali nelle istruzioni contenenti dati utente verranno nascosta; sostituita con alcuni valori di costante predefinite.  
  
 Quando transparent data encryption è abilitato nel dispositivo, mascheramento dei dati utente in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività viene automaticamente attivata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_log_user_data_masking [ [ @masking_mode = ] value ] ;  
```  
  
#### <a name="parameters"></a>Parametri  
 [  **@masking_mode=** ] *masking_mode*  
 Determina se sono abilitati transparent data encryption log utente maschera dati. *masking_mode* viene **int**, e può essere uno dei valori seguenti:  
  
-   0 = disabilitato, i dati vengono visualizzati nell'utente il [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività.  
  
-   1 = abilitato, l'utente le istruzioni di dati vengono visualizzate nel [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività, ma i dati dell'utente è nascosta.  
  
-   2 = le istruzioni che contengono i dati utente non vengono scritti i [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività.  
  
 L'esecuzione di **sp_pdw_ log_user_data_masking** senza parametri, viene restituito lo stato corrente della maschera dati utente di log TDE nel dispositivo come un set di risultati scalari.  
  
## <a name="remarks"></a>Osservazioni  
 Dati utente maschera [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] attività registra abilita la sostituzione di valori letterali con valori di costanti predefiniti in **selezionare** e istruzioni DML, poiché possono contenere dati utente. Impostazione *masking_mode* a 1 non esegue il mascheramento dei metadati, ad esempio i nomi di colonna o nomi di tabella. Impostazione *masking_mode* a 2 consente di rimuovere le istruzioni con metadati, ad esempio i nomi di colonna o nomi di tabella.  
  
 Dati utente maschera [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività viene implementata nel modo seguente:  
  
-   Transparent Data Encryption e i dati utente maschera [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività sono disattivati per impostazione predefinita. Le istruzioni non venga automaticamente nascosta se la crittografia del database non è abilitata nel dispositivo.  
  
-   L'abilitazione di Transparent Data Encryption nel dispositivo automaticamente consente di attivare il mascheramento dei dati utente in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività.  
  
-   Disabilitazione di TDE non riguarda i dati utente maschera [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività.  
  
-   È possibile abilitare in modo esplicito i dati utente maschera [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività tramite il **sp_pdw_log_user_data_masking** procedura.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **sysadmin** ruolo predefinito del database, o **CONTROL SERVER** autorizzazione.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente Abilita dati utente di log TDE maschera nel dispositivo.  
  
```  
EXEC sp_pdw_log_user_data_masking 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_pdw_database_encryption &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
  
  
