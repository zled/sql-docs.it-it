---
title: sp_syscollector_upload_collection_set (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_syscollector_upload_collection_set
- sp_syscollector_upload_collection_set_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_upload_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: eed9232c-2b0a-4b6a-8ba0-76b7c99f48dc
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0bb4ba04b346e6931a55d26172f0d34b27166950
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spsyscollectoruploadcollectionset-transact-sql"></a>sp_syscollector_upload_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Avvia un caricamento di dati del set di raccolta se il set di raccolta è abilitato.  
  
> [!IMPORTANT]  
>  Questa stored procedure può essere utilizzata solo per i set di raccolta configurati per la raccolta e il caricamento dei dati in modalità memorizzata nella cache.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_syscollector_upload_collection_set [[ @collection_set_id = ] collection_set_id ]  
          , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@collection_set_id =** ] *collection_set_id*  
 Identificatore univoco locale del set di raccolta. *collection_set_id* viene **int** e deve avere un valore se *nome* è NULL.  
  
 [  **@name =** ] **'***nome***'**  
 Nome del set di raccolta. *nome* viene **sysname** e deve avere un valore se *collection_set_id* è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Entrambi *collection_set_id* o *nome* deve avere un valore; non possono essere entrambi NULL.  
  
 Questa procedura può essere utilizzata per l'avvio di un caricamento su richiesta per un set di raccolta in esecuzione. La procedura può essere utilizzata solo per i set di raccolta configurati per la raccolta e il caricamento dei dati in modalità memorizzata nella cache. Questo consente a un utente di ottenere i dati da analizzare senza dover aspettare un caricamento pianificato.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **dc_operator** (con autorizzazione EXECUTE) ruolo predefinito del database per eseguire questa procedura.  
  
## <a name="example"></a>Esempio  
 Esegue un caricamento su richiesta di un set di raccolta denominato `Simple Collection Set`.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_upload_collection_set @name = 'Simple Collection Set' ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Raccolta dati](../../relational-databases/data-collection/data-collection.md)  
  
  
