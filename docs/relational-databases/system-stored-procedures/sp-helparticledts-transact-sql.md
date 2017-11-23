---
title: sp_helparticledts (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_helparticledts
- sp_helparticledts_TSQL
helpviewer_keywords: sp_helparticledts
ms.assetid: cd1aed60-e056-4ff3-86ee-62b19433d890
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26fef36faaa73d6e97e2b5cebc5548b8b2e1b8c3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sphelparticledts-transact-sql"></a>sp_helparticledts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente di ottenere informazioni sui nomi delle attività personalizzate da utilizzare per la creazione di una sottoscrizione di trasformazione in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helparticledts [ @publication = ] 'publication', [ @article = ] 'article'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication =**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@article=**] **'***articolo***'**  
 Nome di un articolo della pubblicazione. *articolo* è **sysname**, non prevede alcun valore predefinito.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**pre_script_ignore_error_task_name**|**sysname**|Nome dell'attività di programmazione eseguita prima della copia dei dati dello snapshot. L'esecuzione del programma viene proseguita se viene rilevato un errore di script.|  
|**pre_script_task_name**|**sysname**|Nome dell'attività di programmazione eseguita prima della copia dei dati dello snapshot. L'esecuzione del programma viene interrotta se viene rilevato un errore.|  
|**transformation_task_name**|**sysname**|Nome dell'attività di programmazione quando si utilizza un'attività Query guidata dai dati.|  
|**post_script_ignore_error_task_name**|**sysname**|Nome dell'attività di programmazione eseguita dopo la copia dei dati dello snapshot. L'esecuzione del programma viene proseguita se viene rilevato un errore di script.|  
|**post_script_task_name**|**sysname**|Nome dell'attività di programmazione eseguita dopo la copia dei dati dello snapshot. L'esecuzione del programma viene interrotta se viene rilevato un errore.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helparticledts** viene utilizzata nella replica snapshot e transazionale.  
  
 Per i nomi delle attività di un programma di replica DTS (Data Transformation Services) è necessario seguire determinate convenzioni di denominazione richieste dagli agenti di replica. Per le attività personalizzate, ad esempio Esegui SQL, il nome è una stringa concatenata composta dal nome dell'articolo, da un prefisso e da una terza parte facoltativa. Durante la scrittura del codice, in caso di dubbio sui nomi delle attività, è possibile analizzare il set di risultati che indica i nomi delle attività da utilizzare.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server e **db_owner** ruolo predefinito del database possono eseguire **sp_helparticledts**.  
  
  
