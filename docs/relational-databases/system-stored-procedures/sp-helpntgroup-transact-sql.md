---
title: sp_helpntgroup (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helpntgroup
- sp_helpntgroup_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_helpntgroup
ms.assetid: 02b4f7c1-480a-436c-8bae-7a2488be45d2
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6fb1317e6206c2c4b84341365d3a5589d48048e0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpntgroup-transact-sql"></a>sp_helpntgroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sui gruppi di Windows a cui sono associati account nel database corrente.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpntgroup [ [ @ntname= ] 'name' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@ntname =** ] **'***nome***'**  
 Nome del gruppo di Windows. *nome* è **sysname**, con un valore predefinito è NULL. *nome* deve essere un gruppo di Windows valido con accesso al database corrente. Se *nome* non viene specificato, l'output vengono inclusi tutti i gruppi di Windows con accesso al database corrente.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**NTGroupName**|**sysname**|Nome del gruppo di Windows.|  
|**NTGroupId**|**smallint**|Identificatore (ID) di gruppo.|  
|**SID**|**varbinary (85)**|ID di sicurezza (SID) del **NTGroupName**.|  
|**HasDbAccess**|**int**|1 = Il gruppo di Windows dispone dell'accesso al database.|  
  
## <a name="remarks"></a>Osservazioni  
 Per visualizzare un elenco di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ruoli nel database corrente, utilizzare **sp_helprole**.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito un elenco dei gruppi di Windows con accesso al database corrente.  
  
```  
EXEC sp_helpntgroup;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_helprole &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_revokedbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
