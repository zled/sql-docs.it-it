---
title: Sys. login_token (Transact-SQL) | Microsoft Docs
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
- login_token_TSQL
- sys.login_token_TSQL
- sys.login_token
- login_token
dev_langs:
- TSQL
helpviewer_keywords:
- sys.login_token catalog view
- logins [SQL Server], security tokens
- tokens [SQL Server]
ms.assetid: 86e06938-9d0a-44e5-99e2-55c8ef5f2f84
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 62cc40af6ebf3df276f2c0aa3a81eb6703f68c39
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43021439"
---
# <a name="syslogintoken-transact-sql"></a>sys.login_token (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni entità server appartenente al token dell'account di accesso.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**principal_id**|**int**|ID dell'entità. Questo valore è univoco all'interno del server.|  
|**sid**|**varbinary(85)**|ID di sicurezza dell'entità. Se si tratta di un'entità di Windows, **sid** = SID di Windows. Se l'account di accesso viene eseguito il mapping a un certificato **sid** = GUID dal certificato.|  
|**name**|**nvarchar(128)**|Nome dell'entità. Questo valore è univoco all'interno del server.|  
|**type**|**nvarchar(128)**|Descrizione del tipo dell'entità. Tutti i tipi vengono mappati ai **sid**. I possibili valori sono i seguenti:<br /><br /> SQL LOGIN<br /><br /> WINDOWS LOGIN<br /><br /> WINDOWS GROUP<br /><br /> SERVER ROLE<br /><br /> LOGIN MAPPED TO CERTIFICATE<br /><br /> LOGIN MAPPED TO ASYMMETRIC KEY<br /><br /> CERTIFICATE<br /><br /> ASYMMETRIC KEY|  
|**Utilizzo**|**nvarchar(128)**|Specifica che l'entità partecipa alla valutazione di autorizzazioni GRANT or DENY o funge da autenticatore.<br /><br /> I valori validi sono i seguenti:<br /><br /> GRANT OR DENY<br /><br /> DENY ONLY<br /><br /> AUTHENTICATOR|  
  
## <a name="see-also"></a>Vedere anche  
 [Sys. user_token &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-user-token-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
