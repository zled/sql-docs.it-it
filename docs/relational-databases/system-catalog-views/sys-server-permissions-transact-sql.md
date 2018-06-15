---
title: Sys. server_permissions (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.server_permissions_TSQL
- sys.server_permissions
- server_permissions
- server_permissions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_permissions catalog view
ms.assetid: 7d78bf17-6c64-4166-bd0b-9e9e20992136
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 16200de0c63979912b893fa84e7b36cf93a4ec62
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33221938"
---
# <a name="sysserverpermissions-transact-sql"></a>sys.server_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Restituisce una riga per ogni autorizzazione a livello di server.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**class**|**tinyint**|Identifica la classe dell'elemento per cui esiste l'autorizzazione.<br /><br /> 100 = Server<br /><br /> 101 = Entità server<br /><br /> 105 = Endpoint|  
|**class_desc**|**nvarchar(60)**|Descrizione della classe per cui esiste l'autorizzazione. I valori validi sono:<br /><br /> **SERVER**<br /><br /> **SERVER_PRINCIPAL**<br /><br /> **ENDPOINT**|  
|**major_id**|**int**|ID dell'entità a sicurezza diretta per cui esiste l'autorizzazione, interpretato in base alla classe di appartenenza. Nella maggior parte dei casi, si tratta semplicemente dell'ID che si applica a ciò che la classe rappresenta. Negli altri casi, l'interpretazione dei possibili valori è la seguente:<br /><br /> 100 = sempre 0|  
|**minor_id**|**int**|ID secondario dell'elemento per cui esiste l'autorizzazione, interpretato in base alla classe di appartenenza.|  
|**grantee_principal_id**|**int**|ID dell'entità server alla quale vengono concesse le autorizzazioni.|  
|**grantor_principal_id**|**int**|ID dell'entità server dell'utente che concede queste autorizzazioni.|  
|**type**|**Char(4)**|Tipo di autorizzazione per il server. Per un elenco dei tipi di autorizzazioni, vedere la tabella seguente.|  
|**permission_name**|**nvarchar(128)**|Nome dell'autorizzazione.|  
|**state**|**char(1)**|Stato dell'autorizzazione:<br /><br /> D = Deny<br /><br /> R = Revoke<br /><br /> G = Grant<br /><br /> W = Grant With Grant Option|  
|**state_desc**|**nvarchar(60)**|Descrizione dello stato dell'autorizzazione:<br /><br /> DENY<br /><br /> REVOKE<br /><br /> GRANT<br /><br /> GRANT_WITH_GRANT_OPTION|  
  
|Tipo di autorizzazione|Nome dell'autorizzazione|Entità a protezione diretta a cui si applica|  
|---------------------|---------------------|--------------------------|  
|ADBO|ADMINISTER BULK OPERATIONS|SERVER|  
|AL|ALTER|ENDPOINT, LOGIN|  
|ALCD|ALTER ANY CREDENTIAL|SERVER|  
|ALCO|ALTER ANY CONNECTION|SERVER|  
|ALDB|ALTER ANY DATABASE|SERVER|  
|ALES|ALTER ANY EVENT NOTIFICATION|SERVER|  
|ALHE|ALTER ANY ENDPOINT|SERVER|  
|ALLG|ALTER ANY LOGIN|SERVER|  
|ALLS|ALTER ANY LINKED SERVER|SERVER|  
|ALRS|ALTER RESOURCES|SERVER|  
|ALSS|ALTER SERVER STATE|SERVER|  
|ALST|ALTER SETTINGS|SERVER|  
|ALTR|ALTER TRACE|SERVER|  
|AUTH|AUTHENTICATE SERVER|SERVER|  
|CL|CONTROL|ENDPOINT, LOGIN|  
|CL|CONTROL SERVER|SERVER|  
|CO|CONNECT|ENDPOINT|  
|COSQ|CONNECT SQL|SERVER|  
|CRDB|CREATE ANY DATABASE|SERVER|  
|CRDE|CREATE DDL EVENT NOTIFICATION|SERVER|  
|CRHE|CREATE ENDPOINT|SERVER|  
|CRTE|CREATE TRACE EVENT NOTIFICATION|SERVER|  
|IM|IMPERSONATE|Account di accesso|  
|SHDN|SHUTDOWN|SERVER|  
|TO|TAKE OWNERSHIP|ENDPOINT|  
|VW|VIEW DEFINITION|ENDPOINT, LOGIN|  
|VWAD|VIEW ANY DEFINITION|SERVER|  
|VWDB|VIEW ANY DATABASE|SERVER|  
|VWSS|VIEW SERVER STATE|SERVER|  
|XA|EXTERNAL ACCESS|SERVER|  
  
## <a name="permissions"></a>Autorizzazioni  
 Qualsiasi utente può visualizzare le proprie autorizzazioni. Per visualizzare le autorizzazioni per altri account di accesso, è richiesta VIEW DEFINITION, ALTER ANY LOGIN o qualsiasi autorizzazione per un account di accesso. Per visualizzare i ruoli del server definiti dall'utente, è richiesta l'autorizzazione ALTER ANY SERVER ROLE o l'appartenenza al ruolo.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Esempi  
 Nella query seguente vengono elencate le autorizzazioni concesse o negate in modo esplicito alle entità del server.  
  
> [!IMPORTANT]  
>  Le autorizzazioni dei ruoli predefiniti del server non sono incluse in sys.server_permissions. Pertanto, le entità del server potrebbero contenere ulteriori autorizzazioni non presenti in questo elenco.  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pe.state_desc, pe.permission_name   
FROM sys.server_principals AS pr   
JOIN sys.server_permissions AS pe   
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Gerarchia delle autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
  
  
