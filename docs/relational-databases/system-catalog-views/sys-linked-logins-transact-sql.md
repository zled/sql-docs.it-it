---
title: linked_logins (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.linked_logins
- sys.linked_logins_TSQL
- linked_logins_TSQL
- linked_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.linked_logins catalog view
ms.assetid: af57bf0c-a265-410f-9bab-63b78569b4a6
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 9b03700e08422b6e6fd585f5612713c95b11115d
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43036788"
---
# <a name="syslinkedlogins-transact-sql"></a>sys.linked_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni mapping dell'account di accesso al server collegato, per l'utilizzo in RPC e query distribuite dal server locale al server collegato corrispondente.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|ID del server nella **Sys. Servers**.|  
|**local_principal_id**|**int**|Entità server a cui viene applicato il mapping.<br /><br /> 0 = carattere jolly o pubblico.|  
|**uses_self_credential**|**bit**|Se è 1, il mapping indica che devono essere utilizzate credenziali specifiche della sessione. Se è 0, significa che nella sessione vengono utilizzati il nome e la password specificati.|  
|**remote_name**|**sysname**|Nome utente remoto da utilizzare per la connessione. La password viene archiviata, ma non è esposta nelle interfacce delle viste del catalogo.|  
|**modify_date**|**datetime**|Data dell'ultima modifica dell'account di accesso collegato.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo di server collegati &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)  
  
  
