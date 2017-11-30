---
title: sysmail_unsentitems (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_unsentitems_TSQL
- sysmail_unsentitems
dev_langs: TSQL
helpviewer_keywords: sysmail_unsentitems database mail view
ms.assetid: 993c12da-41e5-4e53-a188-0323feb70c67
caps.latest.revision: "15"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 85b7db39b03913b735ebde53571675fd9235a7e8
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sysmailunsentitems-transact-sql"></a>sysmail_unsentitems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni messaggio di posta elettronica Database il **non inviati** o **ritentare** stato. I messaggi con uno di questi due stati si trovano ancora nella coda della posta e potrebbero essere inviati in qualsiasi momento. I messaggi possono avere il **non inviati** stato per i motivi seguenti:  
  
-   Il messaggio è nuovo e, anche se è stato inserito nella coda della posta, non è ancora stato elaborato da Posta elettronica database che sta inviando altri messaggi.  
  
-   Il programma esterno Posta elettronica database non è in esecuzione e attualmente la posta non viene inviata.  
  
 I messaggi possono avere il **ritentare** stato per i motivi seguenti:  
  
-   Posta elettronica database ha tentato di inviare il messaggio, ma non è stato possibile contattare il server di posta elettronica SMTP. Posta elettronica database continuerà a tentare di inviare il messaggio utilizzando altri account di Posta elettronica database assegnati al profilo che ha inviato il messaggio. Se nessun account può inviare la posta elettronica, posta elettronica Database attenderà l'intervallo di tempo configurato per il **Ritardo tentativi Account** parametro e si tenta quindi di inviare nuovamente il messaggio. Posta elettronica database utilizza il **tentativi Account** parametro per determinare il numero di volte per tentare di inviare il messaggio. Mantengono i messaggi **ritentare** purché la posta elettronica Database sta tentando di inviare il messaggio di stato.  
  
 Utilizzare questa vista quando si desidera controllare il numero di messaggi in attesa di essere inviati e da quanto tempo sono presenti nella coda della posta. In genere il numero di **non inviati** messaggi sarà bassi. Eseguire un test di benchmark durante il normale funzionamento per determinare il numero ragionevole di messaggi che può essere presente nella coda in condizioni di lavoro regolari.  
  
 Per visualizzare tutti i messaggi elaborati da posta elettronica Database, utilizzare [sysmail_allitems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md). Per visualizzare solo i messaggi con lo stato non riuscito, utilizzare [sysmail_faileditems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md). Per visualizzare solo i messaggi che sono stati inviati, utilizzare [sysmail_sentitems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**mailitem_id**|**int**|Identificatore dell'elemento di posta nella coda della posta.|  
|**profile_id**|**int**|Identificatore del profilo utilizzato per l'invio del messaggio.|  
|**destinatari**|**varchar(max)**|Indirizzi di posta elettronica dei destinatari del messaggio.|  
|**copy_recipients**|**varchar(max)**|Indirizzi di posta elettronica degli utenti che ricevono una copia del messaggio.|  
|**blind_copy_recipients**|**varchar(max)**|Indirizzi di posta elettronica degli utenti che ricevono una copia del messaggio, ma i cui nomi non sono indicati nell'intestazione del messaggio.|  
|**Oggetto**|**nvarchar(510)**|Oggetto del messaggio.|  
|**corpo**|**varchar(max)**|Corpo del messaggio.|  
|**body_format**|**varchar (20)**|Formato del corpo del messaggio. I valori possibili sono **testo** e **HTML**.|  
|**importanza**|**varchar(6)**|Il **importanza** parametro del messaggio.|  
|**sensibilità**|**varchar(12)**|Il **sensibilità** parametro del messaggio.|  
|**file_attachments**|**varchar(max)**|Elenco delimitato da punti e virgola dei nomi dei file allegati al messaggio di posta elettronica.|  
|**attachment_encoding**|**varchar (20)**|Tipo di allegato del messaggio di posta elettronica.|  
|**query**|**varchar(max)**|Query eseguita dal programma di posta elettronica.|  
|**execute_query_database**|**sysname**|Contesto di database all'interno del quale il programma di posta elettronica ha eseguito la query.|  
|**attach_query_result_as_file**|**bit**|Quando il valore è 0, i risultati della query sono inclusi nel corpo del messaggio di posta elettronica, dopo il contenuto del corpo. Quando il valore è 1, i risultati sono restituiti come file allegato.|  
|**query_result_header**|**bit**|Quando il valore è 1, i risultati della query includono le intestazioni di colonna. Quando il valore è 0, i risultati della query non includono le intestazioni di colonna.|  
|**query_result_width**|**int**|Il **query_result_width** parametro del messaggio.|  
|**query_result_separator**|**Char (1)**|Carattere utilizzato per separare le colonne nell'output della query.|  
|**exclude_query_output**|**bit**|Il **exclude_query_output** parametro del messaggio. Per ulteriori informazioni, vedere [sp_send_dbmail &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).|  
|**append_query_error**|**bit**|Il **append_query_error** parametro del messaggio. 0 indica che Posta elettronica database non deve inviare il messaggio di posta elettronica se la query contiene un errore.|  
|**send_request_date**|**datetime**|Data e ora di inserimento del messaggio nella coda della posta.|  
|**send_request_user**|**sysname**|Utente che ha inviato il messaggio. Il contesto utente della procedura di posta elettronica database, non si tratta di **da** campo del messaggio.|  
|**sent_account_id**|**int**|Identificatore dell'account di Posta elettronica database utilizzato per l'invio del messaggio. Per questa vista è sempre NULL.|  
|**sent_status**|**varchar (8)**|Sarà **non inviati** se posta elettronica Database non ha tentato di inviare il messaggio. Sarà **ritentare** se non è riuscito a inviare il messaggio di posta elettronica Database ma nuovo tentativo.|  
|**sent_date**|**datetime**|Data e ora dell'ultimo tentativo di invio del messaggio. Se Posta elettronica database non ha tentato di inviare il messaggio, il valore di questo parametro è NULL.|  
|**last_mod_date**|**datetime**|Data e ora dell'ultima modifica della riga.|  
|**last_mod_user**|**sysname**|Autore dell'ultima modifica della riga.|  
  
## <a name="remarks"></a>Osservazioni  
 Quando si risolvono i problemi relativi a Posta elettronica database, questa vista può consentire di identificare la natura del problema in quanto indica il numero di messaggi in attesa di essere inviati e il tempo di attesa nella coda. Se nessun messaggio viene inviato, è possibile che il programma esterno Posta elettronica database non sia in esecuzione oppure che esista un problema di rete che impedisce a Posta elettronica database di contattare i server SMTP. Se molti dei messaggi non inviati hanno lo stesso **profile_id**, potrebbe esserci un problema con il server SMTP. Considerare l'opportunità di aggiungere altri account al profilo. Se i messaggi vengono inviati ma il tempo di attesa nella coda è eccessivo, è possibile che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] necessiti di un maggior numero di risorse per l'elaborazione del volume di messaggi scambiati.  
  
## <a name="permissions"></a>Permissions  
 Concesso a **sysadmin** ruolo predefinito del server e **DatabaseMailUserRole** ruolo del database. Quando eseguito da un membro del **sysadmin** ruolo predefinito del server, questa visualizzazione Mostra tutti i **non inviati** o **ritentare** messaggi. Tutti gli altri utenti vedono solo il **non inviati** o **ritentare** messaggi che hanno inviato personalmente.  
  
  
