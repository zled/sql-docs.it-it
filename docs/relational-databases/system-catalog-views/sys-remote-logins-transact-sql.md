---
title: remote_logins (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.remote_logins_TSQL
- remote_logins
- remote_logins_TSQL
- sys.remote_logins
dev_langs: TSQL
helpviewer_keywords: sys.remote_logins catalog view
ms.assetid: 38477e91-d084-4df7-b1de-b930c5580189
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 774286d1827591144d50d7f0ad84feea1a463d2a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysremotelogins-transact-sql"></a>sys.remote_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni mapping di account di accesso remoto. Questa vista del catalogo viene utilizzata per eseguire il mapping tra gli account di accesso locali in ingresso che risultano provenire da un server corrispondente e un account di accesso locale effettivo.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|ID del server in **Sys. Servers**. Questo nome viene fornito dalla connessione proveniente dal server "remoto".|  
|**remote_name**|**sysname**|Nome dell'account di accesso fornito dalla connessione per il mapping. Se è NULL, viene utilizzato il nome dell'account di accesso specificato nella connessione.|  
|**local_principal_id**|**int**|ID dell'entità server a cui viene eseguito il mapping dell'account di accesso. Se è 0, sull'account di accesso remoto viene eseguito il mapping all'account di accesso con lo stesso nome.|  
|**modify_date**|**datetime**|Data dell'ultima modifica dell'account di accesso collegato.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo di server collegati &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
