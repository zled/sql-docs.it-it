---
title: sp_helpmergearticleconflicts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
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
- sp_helpmergearticleconflicts
- sp_helpmergearticleconflicts_TSQL
helpviewer_keywords:
- sp_helpmergearticleconflicts
ms.assetid: 4678a2b9-9a5f-4193-a20d-2e11fc896c3a
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c1e1ff0c3a7706067a1686947a52db08d950c5e7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpmergearticleconflicts-transact-sql"></a>sp_helpmergearticleconflicts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce gli articoli della pubblicazione che presentano conflitti. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione o nel database di sottoscrizione di tipo merge del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpmergearticleconflicts [ [ @publication = ] 'publication' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publsher_db' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 È il nome della pubblicazione di tipo merge. *pubblicazione* è **sysname**, il valore predefinito è **%**, che restituisce tutti gli articoli nel database che presentano conflitti.  
  
 [  **@publisher=**] **'***publisher***'**  
 È il nome del server di pubblicazione. *publisher* è **sysname**, con un valore predefinito è NULL.  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 È il nome del database di pubblicazione. *publisher_db* è **sysname**, con un valore predefinito è NULL.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**article**|**sysname**|Nome dell'articolo.|  
|**source_owner**|**sysname**|Proprietario dell'oggetto di origine.|  
|**source_object**|**nvarchar(386)**|Nome dell'oggetto di origine.|  
|**conflict_table**|**nvarchar(258)**|Nome della tabella in cui sono archiviati i conflitti di inserimento o aggiornamento.|  
|**guidcolname**|**sysname**|Nome del valore RowGuidCol per l'oggetto di origine.|  
|**centralized_conflicts**|**int**|Indica se i record dei conflitti vengono archiviati nel server di pubblicazione specificato.|  
  
 Se l'articolo include solo conflitti di eliminazione e nessuna **conflict_table** righe, il nome del **conflict_table** nel risultato è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpmergearticleconflicts** viene utilizzata nella replica di tipo merge.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server e **db_owner** ruolo predefinito del database possono eseguire **sp_helpmergearticleconflicts**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
