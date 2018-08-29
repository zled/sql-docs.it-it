---
title: sp_schemafilter (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_schemafilter_TSQL
- sp_schemafilter
helpviewer_keywords:
- sp_schemafilter
ms.assetid: 199e869b-2cd2-44ee-b2ee-69edb06a1bc4
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4da23d87736d7ad9af4c00c5f4704e9cbbdd5160
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43027035"
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
 [**@publisher** =] **'***publisher***'**  
 È il nome del non -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione. *server di pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [**@schema** =] **'***schema***'**  
 Nome dello schema. *lo schema* viene **sysname**, con un valore predefinito NULL.  
  
 [**@operation** =] **'***operazione***'**  
 Operazione da eseguire nello schema. *operazione* viene **nvarchar(4)**, e può essere uno dei valori seguenti.  
  
|valore|Description|  
|-----------|-----------------|  
|**add**|Aggiunge lo schema specificato all'elenco di schemi non idonei per la pubblicazione.|  
|**drop**|Elimina lo schema specificato dall'elenco di schemi non idonei per la pubblicazione.|  
|**Guida**|Restituisce l'elenco degli schemi non idonei per la pubblicazione.|  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**NomeSchema**|**sysname**|Nome dello schema non idoneo per la pubblicazione.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 **sp_schemafilter** deve essere utilizzato solo per server di pubblicazione eterogenei.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server nel server di distribuzione possono eseguire **sp_schemafilter**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
