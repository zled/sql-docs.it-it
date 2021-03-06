---
title: Sys. security_predicates (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.SECURITY_PREDICATES
- SECURITY_PREDICATES
- SECURITY_PREDICATES_TSQL
- SYS.SECURITY_PREDICATES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.security_predicates catalog view
- security_predicates catalog view
ms.assetid: c7a2f28c-98da-463d-8b8a-8e5619e2c6a6
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0a3c0ee5cffc362f1442315c50ff738bee99b0cb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670809"
---
# <a name="syssecuritypredicates-transact-sql"></a>Sys. security_predicates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni predicato di sicurezza nel database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|ID del criterio di sicurezza che contiene il predicato.|  
|security_predicate_id|**int**|ID predicato all'interno del criterio di sicurezza.|  
|target_object_id|**int**|ID dell'oggetto a cui è associato il predicato di sicurezza.|  
|predicate_definition|**nvarchar(max)**|Nome completo della funzione che verrà usata come predicato di sicurezza, inclusi gli argomenti. Si noti che il `schema.function` nome può essere normalizzato (vale a dire con caratteri di escape) come qualsiasi altro elemento nel testo per la coerenza. Esempio:<br /><br /> `[dbo].[fn_securitypredicate]([wing], [startTime], [endTime])`|  
|predicate_type|**int**|Tipo di predicato usato dai criteri di sicurezza:<br /><br /> 0 = PREDICATO DEL FILTRO<br /><br /> 1 = PREDICATO DI BLOCCO|  
|predicate_type_desc|**nvarchar(60)**|Tipo di predicato usato dai criteri di sicurezza:<br /><br /> FILTER<br /><br /> BLOCCO|  
|operazione|**int**|Il tipo di operazione specificato per il predicato:<br /><br /> NULL = tutte le operazioni applicabili<br /><br /> 1 = AFTER INSERT<br /><br /> 2 = DOPO L'AGGIORNAMENTO<br /><br /> 3 = PRIMA DELL'AGGIORNAMENTO<br /><br /> 4 = PRIMA DELL'ELIMINAZIONE|  
|operation_desc|**nvarchar(60)**|Il tipo di operazione specificato per il predicato:<br /><br /> NULL<br /><br /> DOPO L'INSERIMENTO<br /><br /> AFTER UPDATE<br /><br /> PRIMA DELL'AGGIORNAMENTO<br /><br /> PRIMA DELL'ELIMINAZIONE|  
  
## <a name="permissions"></a>Permissions  
 Le entità con la **ALTER ANY SECURITY POLICY** autorizzazione ha accesso a tutti gli oggetti in questa vista del catalogo, nonché tutti gli utenti con **VIEW DEFINITION** sull'oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza a livello di riga](../../relational-databases/security/row-level-security.md)   
 [sys.security_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [CREATE SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
