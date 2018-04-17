---
title: sp_helpmergedeleteconflictrows (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_helpmergedeleteconflictrows
- sp_helpmergedeleteconflictrows_TSQL
helpviewer_keywords:
- sp_helpmergedeleteconflictrows
ms.assetid: 222be651-5690-4341-9dfb-f9ec1d80c970
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6af4f2128a2ced993129c4e9b813ecd8d9154716
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpmergedeleteconflictrows-transact-sql"></a>sp_helpmergedeleteconflictrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sulle righe di dati che hanno perso nei conflitti di eliminazione. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione o nel database di sottoscrizione del Sottoscrittore quando si utilizza la registrazione dei conflitti decentralizzata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpmergedeleteconflictrows [ [ @publication = ] 'publication']  
    [ , [ @source_object = ] 'source_object']  
    [ , [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publsher_db'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, il valore predefinito è **%**. Se la pubblicazione viene specificata, vengono restituiti tutti i conflitti risultanti corrispondenti.  
  
 [  **@source_object=**] **'***source_object***'**  
 Nome dell'oggetto di origine. *source_object* viene **nvarchar(386)**, con un valore predefinito è NULL.  
  
 [  **@publisher=**] **'***publisher***'**  
 È il nome del server di pubblicazione. *publisher* è **sysname**, con un valore predefinito è NULL.  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 È il nome del database di pubblicazione. *publisher_db* è **sysname**, con un valore predefinito è NULL.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**source_object**|**nvarchar(386)**|Oggetto di origine per il conflitto di eliminazione.|  
|**rowguid**|**uniqueidentifier**|Identificatore di riga per il conflitto di eliminazione.|  
|**conflict_type**|**int**|Codice che indica il tipo di conflitto:<br /><br /> **1** = UpdateConflict: conflitto viene rilevato a livello di riga.<br /><br /> **2** = ColumnUpdateConflict: conflitto viene rilevato a livello di colonna.<br /><br /> **3** = UpdateDeleteWinsConflict: eliminazione prevale nel conflitto.<br /><br /> **4** = UpdateWinsDeleteConflict: rowguid eliminato che perde nel conflitto viene registrato in questa tabella.<br /><br /> **5** = UploadInsertFailed: Impossibile applicare l'inserimento dal sottoscrittore nel server di pubblicazione.<br /><br /> **6** = DownloadInsertFailed: inserimento dal server di pubblicazione non può essere applicato nel Sottoscrittore.<br /><br /> **7** = UploadDeleteFailed: Delete nel Sottoscrittore non è stato possibile caricare nel server di pubblicazione.<br /><br /> **8** = DownloadDeleteFailed: Impossibile scaricare l'eliminazione nel server di pubblicazione al sottoscrittore.<br /><br /> **9** = UploadUpdateFailed: non è stato possibile applicare l'aggiornamento nel Sottoscrittore nel server di pubblicazione.<br /><br /> **10** = DownloadUpdateFailed: non è stato possibile applicare l'aggiornamento nel server di pubblicazione al sottoscrittore.|  
|**reason_code**|**Int**|Codice di errore che può essere sensibile al contesto.|  
|**reason_text**|**varchar(720)**|Descrizione dell'errore che può essere sensibile al contesto.|  
|**origin_datasource**|**varchar(255)**|Origine del conflitto.|  
|**pubid**|**uniqueidentifier**|Identificatore della pubblicazione.|  
|**MSrepl_create_time**|**datetime**|Ora in cui sono state aggiunte le informazioni sui conflitti.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpmergedeleteconflictrows** viene utilizzata nella replica di tipo merge.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server e **db_owner** ruolo predefinito del database possono eseguire **sp_helpmergedeleteconflictrows**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
