---
title: sp_browsesnapshotfolder (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- sp_browsesnapshotfolder
- sp_browsesnapshotfolder_TSQL
helpviewer_keywords:
- sp_browsesnapshotfolder
ms.assetid: 0872edf2-4038-4bc1-a68d-05ebfad434d2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4b31f3bb0e865452fd6f557a4832b04a21c11624
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spbrowsesnapshotfolder-transact-sql"></a>sp_browsesnapshotfolder (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il percorso completo per l'ultimo snapshot generato per una pubblicazione. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_browsesnapshotfolder [@publication= ] 'publication'  
    { [ , [ @subscriber = ] 'subscriber' ]  
 [ , [ @subscriber_db = ] 'subscriber_db' ] }  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione in cui è contenuto l'articolo. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@subscriber=**] **'***sottoscrittore***'**  
 Nome del Sottoscrittore. *Sottoscrittore* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@subscriber_db=**] **'***subscriber_db***'**  
 Nome del database di sottoscrizione. *subscriber_db* è **sysname**, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**snapshot_folder**|**nvarchar(512)**|Percorso completo della directory snapshot.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_browsesnapshotfolder** viene utilizzata nella replica snapshot e transazionale.  
  
 Se il *sottoscrittore* e *subscriber_db* campi sono NULL, la stored procedure restituisce la cartella snapshot dello snapshot più recente disponibile per la pubblicazione. Se il *sottoscrittore* e *subscriber_db* i campi vengono specificati, la stored procedure restituisce la cartella snapshot per la sottoscrizione specificata. Se per la pubblicazione non è stato generato uno snapshot, viene restituito un set di risultati vuoto.  
  
 Se la pubblicazione è configurata per la generazione di file di snapshot sia nella directory di lavoro che nella cartella snapshot del server di pubblicazione, il set dei risultati include due righe. La prima riga contiene la cartella snapshot della pubblicazione e la seconda la directory di lavoro del server di pubblicazione. **sp_browsesnapshotfolder** è utile per determinare la directory in cui vengono generati i file di snapshot.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_browsesnapshotfolder**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
