---
title: sp_clean_db_free_space (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_clean_db_free_space_TSQL
- sp_clean_db_free_space
dev_langs:
- TSQL
helpviewer_keywords:
- sp_clean_db_free_space
- ghost records
ms.assetid: faa96f7e-be92-47b1-8bc5-4dbba5331655
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0262cb9928d678b814f39b21cf6e66efb69b494a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810329"
---
# <a name="spcleandbfreespace-transact-sql"></a>sp_clean_db_free_space (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove le informazioni residue lasciate nelle pagine del database a causa delle routine di modifica dei dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. sp_clean_db_free_space pulisce tutte le pagine in tutti i file del database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_clean_db_free_space   
[ @dbname ] = 'database_name'   
[ , [ @cleaning_delay = ] 'delay_in_seconds' ] [;]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @dbname=] '*nome_database*'  
 Nome del database da pulire. *dbname* viene **sysname** e non può essere NULL.  
  
 [ @cleaning_delay=] '*delay_in_seconds*'  
 Specifica un intervallo di ritardo tra le pulizie delle pagine per ridurre l'impatto sul sistema di I/O. *delay_in_seconds* viene **int** con valore predefinito è 0.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Note  
 Le operazioni di aggiornamento o le operazioni di eliminazione da una tabella che provocano lo spostamento di una riga consentono di liberare immediatamente spazio in una pagina poiché rimuovono i riferimenti alla riga specifica. In alcune circostanze, tuttavia, la riga può rimanere fisicamente nella pagina di dati come record fantasma. I record fantasma vengono rimossi periodicamente da un processo in background. Tali dati residui non viene restituiti dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] in risposta alle query. In ambienti in cui la sicurezza fisica dei file di dati o di backup non sia sufficiente, è tuttavia possibile utilizzare sp_clean_db_free_space per eliminare tali record fantasma.  
  
 La quantità di tempo necessaria per eseguire sp_clean_db_free_space dipende dalle dimensioni del file, dallo spazio libero disponibile e dalla capacità del disco. Poiché l'esecuzione di sp_clean_db_free_space può influire in modo significativo sulle attività di I/O, è consigliabile eseguire questa procedura in orario diverso da quello lavorativo.  
  
 Prima di eseguire sp_clean_db_free_space, è opportuno creare un backup completo del database.  
  
 I relativi [sp_clean_db_file_free_space](../../relational-databases/system-stored-procedures/sp-clean-db-file-free-space-transact-sql.md) stored procedure può eliminare un singolo file.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo del database db_owner.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono eliminate tutte le informazioni residue dal database `AdventureWorks2012`.  
  
```  
USE master;  
GO  
EXEC sp_clean_db_free_space   
@dbname = N'AdventureWorks2012' ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di database le Stored procedure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)
 <br>[Guida di processo di pulizia fantasma](../ghost-record-cleanup-process-guide.md) 
  
  
