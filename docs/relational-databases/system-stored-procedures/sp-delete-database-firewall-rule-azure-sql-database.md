---
title: sp_delete_database_firewall_rule (Database SQL di Azure) | Documenti Microsoft
ms.custom: ''
ms.date: 08/04/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_delete_database_firewall_rule
- sp_delete_database_firewall_rule_TSQL
- sys.sp_delete_database_firewall_rule
- sys.sp_delete_database_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_database_firewall_rule procedure
ms.assetid: ed295312-e586-4fc2-9e80-806b490ee7bd
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: a2d8ba7a1b0068b3a5321e530e6b7755aa2c5f87
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spdeletedatabasefirewallrule-azure-sql-database"></a>sp_delete_database_firewall_rule (Database di SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Rimuove l'impostazione del firewall a livello di database dal [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Le regole firewall del database possono essere configurate e per il database master e per i database utente vengono eliminate in [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].   
  
 
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_delete_database_firewall_rule [@name =] [N]'name'
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@name =**] **'***nome***'**  
 Nome dell'impostazione del firewall a livello di database che verrà rimossa. *nome* viene **nvarchar (128)** non prevede alcun valore predefinito. L'identificatore Unicode `N` è facoltativo per [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]. 
  
## <a name="permissions"></a>Autorizzazioni  
 Solo a livello di server principale account di accesso creato dal processo di provisioning o un'entità di Azure Active Directory assegnato come amministratore è possibile eliminare le regole del firewall a livello di database.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente rimuove il database a livello di impostazione del firewall denominata `Example DB Setting 1`.
  
```  
-- Remove database-level firewall setting  
EXECUTE sp_delete_database_firewall_rule N'Example DB Setting 1';  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Firewall del Database SQL di Azure](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Procedura: configurare le impostazioni del Firewall (Database SQL di Azure)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;Database SQL di Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_set_database_firewall_rule &#40;Database SQL di Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)   
 [Sys. database_firewall_rules &#40;Database SQL di Azure&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  


