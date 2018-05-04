---
title: sp_clean_db_file_free_space (Transact-SQL) | Documenti Microsoft
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
- sp_clean_db_file_free_space
- sp_clean_db_file_free_space_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ghost records
- sp_clean_db_file_free_space
ms.assetid: 3eb53a67-969d-4cb8-9681-b1c8e6fd55b6
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 41c242e65df878a0a97d6fce221d3bcf3dcde9e8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spcleandbfilefreespace-transact-sql"></a>sp_clean_db_file_free_space (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove le informazioni residue lasciate nelle pagine del database a causa delle routine di modifica dei dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. sp_clean_db_file_free_space pulisce tutte le pagine in un solo file di un database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_clean_db_file_free_space   
[ @dbname ] = 'database_name'   
, @fileid = 'file_number'   
 [ , [ @cleaning_delay = ] 'delay_in_seconds' ] [;]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @dbname=] '*database_name*'  
 Nome del database da pulire. *dbname* viene **sysname** e non può essere NULL.  
  
 [ @fileid=] '*file_number*'  
 ID del file di dati su cui eseguire la pulizia. *file_number* viene **int** e non può essere NULL.  
  
 [ @cleaning_delay=] '*delay_in_seconds*'  
 Specifica un intervallo di ritardo tra le pulizie delle pagine per ridurre l'impatto sul sistema di I/O. *delay_in_seconds* viene **int** con un valore predefinito è 0.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Le operazioni di aggiornamento o le operazioni di eliminazione da una tabella che provocano lo spostamento di una riga consentono di liberare immediatamente spazio in una pagina poiché rimuovono i riferimenti alla riga specifica. In alcune circostanze, tuttavia, la riga può rimanere fisicamente nella pagina di dati come record fantasma. I record fantasma vengono rimossi periodicamente da un processo in background. Tali dati residui non viene restituiti dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] in risposta alle query. In ambienti in cui la sicurezza fisica dei file di dati o di backup non sia sufficiente, è tuttavia possibile utilizzare sp_clean_db_file_free_space per eliminare tali record fantasma.  
  
 La quantità di tempo necessaria per eseguire sp_clean_db_file_free_space dipende dalle dimensioni del file, dallo spazio libero disponibile e dalla capacità del disco. Poiché l'esecuzione di sp_clean_db_file_free_space può influire in modo significativo sulle attività di I/O, è consigliabile eseguire questa procedura in orario diverso da quello lavorativo.  
  
 Prima di eseguire sp_clean_db_file_free_space, è opportuno creare un backup completo del database.  
  
 Correlata [sp_clean_db_free_space](../../relational-databases/system-stored-procedures/sp-clean-db-free-space-transact-sql.md) stored procedure elimina il contenuto tutti i file nel database.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo del database db_owner.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono eliminate le informazioni residue dal file di dati primario del database `AdventureWorks2012`.  
  
```  
USE master;  
GO  
EXEC sp_clean_db_file_free_space   
@dbname = N'AdventureWorks2012', @fileid = 1 ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure del motore di database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
