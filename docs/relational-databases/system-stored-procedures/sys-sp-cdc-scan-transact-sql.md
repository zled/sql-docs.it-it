---
title: Sys. sp_cdc_scan (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_scan_TSQL
- sp_cdc_scan
- sys.sp_cdc_scan
- sp_cdc_scan_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_cdc_scan
ms.assetid: 46e4294c-97b8-47d6-9ed9-b436a9929353
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cbde9d47ae848ed52a9feeb81329f68456330c79
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysspcdcscan-transact-sql"></a>sys.sp_cdc_scan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esegue l'operazione di analisi del log di Change Data Capture.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.sp_cdc_scan [ [ @maxtrans = ] max_trans ]   
     [ , [ @maxscans = ] max_scans ]   
     [ , [ @continuous = ] continuous ]   
     [ , [ @pollinginterval = ] polling_interval ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@maxtrans=** ] *max_trans*  
 Numero massimo di transazioni da elaborare in ogni ciclo di analisi. *max_trans* è **int** con valore predefinito è 500.  
  
 [  **@maxscans=** ] *max_scans*  
 Numero massimo di cicli di analisi da eseguire per estrarre tutte le righe dal log. *max_scans* è **int** con valore predefinito è 10.  
  
 [  **@continuous=** ] *continua*  
 Indica se la stored procedure deve terminare dopo l'esecuzione di un singolo ciclo di analisi (0) o eseguire in modo continuo, sospendendo l'esecuzione per il tempo specificato da *polling_interval* prima di rieseguire il ciclo di analisi (1). *Continua* è **tinyint** con un valore predefinito è 0.  
  
 [  **@pollinginterval=** ] *polling_interval*  
 Numero di secondi tra cicli di analisi del log. *polling_interval* è **bigint** con un valore predefinito è 0.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 sys.sp_cdc_scan viene chiamata internamente da sys.sp_MScdc_capture_job se il processo di acquisizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent viene utilizzato da Change Data Capture. La procedura non può essere eseguita in modo esplicito, quando un'operazione di analisi log di change data capture è già attiva o quando il database è abilitato per la replica transazionale. Questa stored procedure deve essere utilizzata dagli amministratori che desiderano personalizzare il comportamento del processo di acquisizione che viene configurato automaticamente.  
  
## <a name="permissions"></a>Permissions  
 Richiede l'appartenenza al ruolo predefinito del database db_owner.  
  
## <a name="see-also"></a>Vedere anche  
 [cdc_jobs &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
  
  
