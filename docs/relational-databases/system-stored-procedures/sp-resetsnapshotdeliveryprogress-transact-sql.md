---
title: sp_resetsnapshotdeliveryprogress (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_resetsnapshotdeliveryprogress
- sp_resetsnapshotdeliveryprogress_TSQL
helpviewer_keywords:
- sp_resetsnapshotdeliveryprogress
ms.assetid: 5df7d86b-d343-4d9b-88b1-74429ed092e6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0aa67918309c5c34bbe3826853c26cf7422c4666
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spresetsnapshotdeliveryprogress-transact-sql"></a>sp_resetsnapshotdeliveryprogress (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Reimposta il processo di recapito degli snapshot per una sottoscrizione pull in modo che il recapito degli snapshot possa essere riavviato. Questa stored procedure viene eseguita nel database di sottoscrizione del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_resetsnapshotdeliveryprogress [ [ @verbose_level = ] verbose_level ]  
    [ , [ @drop_table = ] 'drop_table' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@verbose_level** =] *verbose_level*  
 Specifica la quantità di informazioni restituite. *verbose_level*è **int**, il valore predefinito è **1**. Il valore **1** indica che un errore viene restituito se non è possibile ottenere i blocchi necessari di **MSsnapshotdeliveryprogress** tabella, e **0** significa che viene restituito alcun errore.  
  
 [  **@drop_table** =] **'***drop_table***'**  
 Indica se eliminare o troncare la tabella contenente le informazioni sullo stato di avanzamento dello snapshot. *drop_table* è **nvarchar (5)**, il valore predefinito è **FALSE**. FALSE indica che la tabella viene troncata, mentre TRUE indica che la tabella è stata eliminata.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_resetsnapshotdeliveryprogress** rimuove tutte le righe di **MSsnapshotdeliveryprogress** tabella. Vengono effettivamente rimossi tutti i metadati rimasti nel database di sottoscrizione in seguito alle precedenti fasi dei processi di recapito degli snapshot.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_resetsnapshotdeliveryprogress**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
