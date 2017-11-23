---
title: sp_helpmergefilter (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- sp_helpmergefilter
- sp_helpmergefilter_TSQL
helpviewer_keywords: sp_helpmergefilter
ms.assetid: f133a094-0009-4771-b93b-e86a5c01e40b
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6ec2500e3fc16c2f6c78473fb97a6b1bf757ef52
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpmergefilter-transact-sql"></a>sp_helpmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sui filtri di merge. Questa stored procedure viene eseguita in qualsiasi database del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpmergefilter [ @publication= ] 'publication'   
    [ , [ @article= ] 'article']  
    [ , [ @filtername= ] 'filtername']  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@article=**] **'***articolo***'**  
 Nome dell'articolo. *articolo* è **sysname**, il valore predefinito è  **%** , che restituisce i nomi di tutti gli articoli.  
  
 [  **@filtername=**] **'***filtername***'**  
 Nome del filtro su cui si desidera ottenere informazioni. *FilterName* è **sysname**, il valore predefinito è  **%** , che restituisce informazioni su tutti i filtri definiti per l'articolo o di una pubblicazione.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**join_filterid**|**int**|ID del filtro join.|  
|**FilterName**|**sysname**|Nome del filtro.|  
|**nome di articolo di join**|**sysname**|Nome dell'articolo di join.|  
|**join_filterclause**|**nvarchar(2000)**|Clausola di filtro che qualifica il join.|  
|**join_unique_key**|**int**|Indica se il join è basato su una chiave univoca.|  
|**proprietario della tabella di base**|**sysname**|Nome del proprietario della tabella di base.|  
|**nome della tabella di base**|**sysname**|Nome della tabella di base.|  
|**proprietario della tabella join**|**sysname**|Nome del proprietario della tabella che si desidera unire in join alla tabella di base.|  
|**nome della tabella join**|**sysname**|Nome della tabella che si desidera unire in join alla tabella di base.|  
|**nome dell'articolo**|**sysname**|Nome dell'articolo di tabella che si desidera unire in join alla tabella di base.|  
|**filter_type**|**tinyint**|Tipo di filtro di merge. I possibili valori sono i seguenti:<br /><br /> **1** = solo filtro join<br /><br /> **2** = relazione tra record logici<br /><br /> **3** = entrambi|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpmergefilter** viene utilizzata nella replica di tipo merge.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server e **db_owner** ruolo predefinito del database possono eseguire **sp_helpmergefilter**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_changemergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_dropmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
