---
title: sp_helplanguage (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helplanguage
- sp_helplanguage_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sp_helplanguage
- default languages
ms.assetid: 8c4651a5-7dbc-49c5-8691-dc72103c2dfa
caps.latest.revision: "19"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a94f66688ce53aef2dcf575d58e16ed6f2f1672b
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sphelplanguage-transact-sql"></a>sp_helplanguage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni su una lingua alternativa specifica o su tutte le lingue in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helplanguage [ [ @language = ] 'language' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@language=** ] **'***language***'**  
 Nome della lingua alternativa per la quale visualizzare le informazioni. *lingua* è **sysname**, con un valore predefinito è NULL. Se *language* è specificato, vengono restituite informazioni sulla lingua specifica. Se non viene specificato alcun linguaggio, informazioni su tutte le lingue nel **Sys. syslanguages** vista di compatibilità viene restituito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**LangID**|**smallint**|Numero di identificazione della lingua.|  
|**DateFormat**|**nchar(3)**|Formato della data.|  
|**DATEFIRST**|**tinyint**|Primo giorno della settimana: 1 per lunedì, 2 per martedì e così via fino a 7 per domenica.|  
|**aggiornamento**|**int**|Versione dell'ultimo aggiornamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per la lingua specificata.|  
|**name**|**sysname**|Nome della lingua.|  
|**alias**|**sysname**|Nome alternativo per la lingua.|  
|**mesi**|**nvarchar(372)**|Nomi dei mesi.|  
|**shortmonths**|**nvarchar(132)**|Nomi brevi dei mesi.|  
|**giorni**|**nvarchar(217)**|Nomi dei giorni.|  
|**LCID**|**int**|ID delle impostazioni locali di Windows relative alla lingua.|  
|**msglangid**|**smallint**|ID del gruppo di messaggi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-information-about-a-single-language"></a>A. Restituzione di informazioni su una sola lingua  
 Nell'esempio seguente vengono visualizzate informazioni sulla lingua alternativa `French`.  
  
```  
sp_helplanguage French;  
```  
  
### <a name="b-returning-information-about-all-languages"></a>B. Restituzione di informazioni su tutte le lingue  
 Nell'esempio seguente vengono visualizzate informazioni su tutte le lingue alternative installate.  
  
```  
sp_helplanguage;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di database Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [@@LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/functions/language-transact-sql.md)   
 [SET LANGUAGE &#40; Transact-SQL &#41;](../../t-sql/statements/set-language-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
