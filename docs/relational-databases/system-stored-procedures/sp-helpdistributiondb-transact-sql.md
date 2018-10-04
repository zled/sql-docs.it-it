---
title: sp_helpdistributiondb (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistributiondb_TSQL
- sp_helpdistributiondb
helpviewer_keywords:
- sp_helpdistributiondb
ms.assetid: a2917020-26d1-4011-99f8-9212d120fd2d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4e6bfddf7a8faa6d19e674b1b73a401b15975c80
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47729359"
---
# <a name="sphelpdistributiondb-transact-sql"></a>sp_helpdistributiondb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le proprietà del database di distribuzione specificato. La stored procedure viene eseguita nel database di distribuzione del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpdistributiondb [ [ @database= ] 'database_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@database=**] **'***database_name***'**  
 Nome del database di cui vengono restituite le proprietà. *database_name* viene **sysname**, il valore predefinito è **%** per tutti i database associati al server di distribuzione e in cui l'utente dispone delle autorizzazioni.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome del database di distribuzione.|  
|**min_distretention**|**int**|Periodo di memorizzazione minimo espresso in ore che deve trascorrere prima dell'eliminazione delle transazioni.|  
|**max_distretention**|**int**|Periodo di memorizzazione massimo espresso in ore trascorso il quale le transazioni vengono eliminate.|  
|**periodo memorizzazione cronologia**|**int**|Numero di ore di memorizzazione della cronologia.|  
|**history_cleanup_agent**|**sysname**|Nome dell'agente di pulizia del contenuto della cronologia.|  
|**distribution_cleanup_agent**|**sysname**|Nome dell'agente di pulizia dei riferimenti alla distribuzione.|  
|**status**|**int**|Solo per uso interno.|  
|**data_folder**|**nvarchar(255)**|Nome della directory utilizzata per archiviare i file di database.|  
|**data_file**|**nvarchar(255)**|Nome del file di database.|  
|**data_file_size**|**int**|Dimensioni iniziali del file di dati in MB.|  
|**log_folder**|**nvarchar(255)**|Nome della directory per il file di log del database.|  
|**file_registro**|**nvarchar(255)**|Nome del file di log.|  
|**log_file_size**|**int**|Dimensioni iniziali del file di log in MB.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 **sp_helpdistributiondb** viene utilizzata in tutti i tipi di replica.  
  
## <a name="permissions"></a>Permissions  
 I membri del **db_owner** ruolo predefinito del database o il **replmonitor** ruolo in un database di distribuzione e gli utenti nell'elenco di accesso alla pubblicazione di una pubblicazione che utilizza il database di distribuzione possono eseguire **sp_helpdistributiondb** per restituire le informazioni relative ai file. I membri del **pubbliche** possono eseguire **sp_helpdistributiondb** per restituire informazioni non correlate a file per i database di distribuzione a cui hanno accesso.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)   
 [sp_changedistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md)   
 [sp_dropdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
