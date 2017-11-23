---
title: sp_addtabletocontents (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
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
- sp_addtabletocontents_TSQL
- sp_addtabletocontents
helpviewer_keywords: sp_addtabletocontents
ms.assetid: 2ea27001-74f4-463e-bf1b-b6b5a86b9219
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a16b89e4d2567a24b8c61fdb5ce6830e2205f824
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spaddtabletocontents-transact-sql"></a>sp_addtabletocontents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Inserisce riferimenti nelle tabelle di rilevamento per le operazioni di merge per tutte le righe di una tabella di origine non incluse nelle tabelle di rilevamento. Utilizzare questa opzione se si hanno il caricamento bulk una grande quantità di dati con **bcp**, cui non vengono attivati i trigger di rilevamento di unione. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addtabletocontents [ @table_name = ] 'table_name'  
    [ , [ @owner_name = ] 'owner_name' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@table_name=**] **'***table_name***'**  
 Nome della tabella. *TABLE_NAME* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@owner_name=**] **'***owner_name***'**  
 Nome del proprietario della tabella. *owner_name* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@filter_clause=** ] **'***filter_clause***'**  
 Specifica una clausola di filtro che controlla quali righe dei dati appena caricati devono essere aggiunte alle tabelle di rilevamento per le operazioni di merge. *filter_clause* è **nvarchar (4000)**, con un valore predefinito null. Se *filter_clause* è **null**, bulk di tutte le righe caricate vengono aggiunti.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_addtabletocontents** viene utilizzata solo nella replica di tipo merge.  
  
 Le righe di *table_name* a cui fa riferimento loro **rowguidcol** e i riferimenti vengono aggiunti per l'unione di tabelle di rilevamento. **sp_addtabletocontents** deve essere utilizzato dopo la copia bulk dei dati in una tabella pubblicata tramite una replica di tipo merge. La stored procedure inizia il rilevamento delle righe copiate e include le nuove righe nella sincronizzazione successiva.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_addtabletocontents**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
