---
title: sp_enumeratependingschemachanges (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_enumeratependingschemachanges
- sp_enumeratependingschemachanges_TSQL
helpviewer_keywords:
- sp_enumeratependingschemachanges
ms.assetid: df169b21-d10a-41df-b3a1-654cfb58bc21
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e6f388bbfa451adeef2a30d04160688037b268b9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spenumeratependingschemachanges-transact-sql"></a>sp_enumeratependingschemachanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un elenco di tutte le modifiche dello schema in sospeso. Questa stored procedure può essere utilizzata con [sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md), che consente agli amministratori di ignorare le modifiche dello schema sospeso selezionate in modo che non vengano replicate. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_enumeratependingschemachanges [ @publication = ] 'publication'   
    [ , [ @starting_schemaversion = ] starting_schemaversion ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=** ] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@starting_schemaversion=** ] *starting_schemaversion*  
 Modifica dello schema con il numero più basso da includere nel set di risultati.  
  
## <a name="result-set"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**article_name**|**sysname**|Nome dell'articolo a cui si applica la modifica dello schema, o **pubblicazione** per le modifiche dello schema che si applicano all'intera pubblicazione.|  
|**attributo SchemaVersion**|**int**|Numero della modifica dello schema in sospeso.|  
|**SchemaType**|**sysname**|Valore di testo che rappresenta il tipo di modifica dello schema.|  
|**schematext**|**nvarchar(max)**|[!INCLUDE[tsql](../../includes/tsql-md.md)] che descrive la modifica dello schema.|  
|**schemastatus**|**nvarchar(10)**|Specifica se è in sospeso una modifica dello schema per l'articolo. I possibili valori sono i seguenti:<br /><br /> **Attiva** = modifica dello schema è in sospeso<br /><br /> **inattivo** = modifica dello schema non è attiva<br /><br /> **ignorare** = modifica dello schema non viene replicata|  
|**SchemaGuid**|**uniqueidentifier**|Identifica la modifica dello schema.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_enumeratependingschemachanges** viene utilizzata nella replica di tipo merge.  
  
 **sp_enumeratependingschemachanges**, utilizzato con [sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md), è progettata per il supporto della replica di tipo merge e deve essere utilizzato solo quando altre azioni correttive, ad esempio la reinizializzazione, non è stato possibile risolvere la situazione.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_enumeratependingschemachanges**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sysmergeschemachange &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
