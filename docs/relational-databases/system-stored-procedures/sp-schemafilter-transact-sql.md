---
title: sp_schemafilter (Transact-SQL) | Documenti Microsoft
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
- sp_schemafilter_TSQL
- sp_schemafilter
helpviewer_keywords: sp_schemafilter
ms.assetid: 199e869b-2cd2-44ee-b2ee-69edb06a1bc4
caps.latest.revision: "24"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 635a9d8fc39ea3621c4ba9b11f54300c19ec1011
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spschemafilter-transact-sql"></a>sp_schemafilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente di visualizzare e modificare le informazioni nello schema che vengono escluse dall'elenco delle tabelle Oracle idonee per la pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_schemafilter [ @publisher = ] 'publisher'   
   [ , [ @schema = ] 'schema' ]   
   [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@publisher**  =] **'***publisher***'**  
 È il nome del non -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione. *server di pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [ **@schema**  =] **'***schema***'**  
 Nome dello schema. *schema* è **sysname**, con un valore predefinito null.  
  
 [ **@operation**  =] **'***operazione***'**  
 Operazione da eseguire nello schema. *operazione* è **nvarchar (4)**, e può essere uno dei valori seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|**aggiungere**|Aggiunge lo schema specificato all'elenco di schemi non idonei per la pubblicazione.|  
|**eliminare**|Elimina lo schema specificato dall'elenco di schemi non idonei per la pubblicazione.|  
|**Guida**|Restituisce l'elenco degli schemi non idonei per la pubblicazione.|  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**NomeSchema**|**sysname**|Nome dello schema non idoneo per la pubblicazione.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_schemafilter** deve essere utilizzato solo per server di pubblicazione eterogenei.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server nel server di distribuzione possono eseguire **sp_schemafilter**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
