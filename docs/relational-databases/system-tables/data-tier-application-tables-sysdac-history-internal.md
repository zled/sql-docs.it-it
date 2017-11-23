---
title: sysdac_history_internal (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysdac_history_internal
- sysdac_history_internal_TSQL
dev_langs: TSQL
helpviewer_keywords: sysdac_history_internal
ms.assetid: 774a1678-0b27-42be-8adc-a6d7a4a56510
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 55bf1ae9625c5b27c7078bbba61704eef195b0ca
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="data-tier-application-tables---sysdachistoryinternal"></a>Tabelle di applicazione livello dati - sysdac_history_internal
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene informazioni sulle azioni eseguite per gestire le applicazioni livello dati. Questa tabella è archiviata nel **dbo** dello schema del **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**action_id**|**int**|Identificatore dell'azione|  
|**sequence_id**|**int**|Consente di identificare un passaggio all'interno di un'azione.|  
|**instance_id**|**uniqueidentifier**|Identificatore dell'istanza di applicazione livello dati. Questa colonna può essere unita di **instance_id** colonna [dbo.sysdac_instances &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md).|  
|**action_type**|**tinyint**|Identificatore del tipo di azione:<br /><br /> **0** = distribuire<br /><br /> **1** = creare<br /><br /> **2** = ridenominazione<br /><br /> **3** = scollegamento<br /><br /> **4** = eliminazione|  
|**action_type_name**|**varchar (19)**|Nome del tipo di azione:<br /><br /> **distribuire**<br /><br /> **creare**<br /><br /> **rinominare**<br /><br /> **Disconnetti**<br /><br /> **eliminare**|  
|**dac_object_type**|**tinyint**|Identificatore del tipo di oggetto interessato dall'azione:<br /><br /> **0** = dacpac<br /><br /> **1** = account di accesso<br /><br /> **2** = database|  
|**dac_object_type_name**|**varchar (8)**|Nome del tipo di oggetto interessato dall'azione:<br /><br /> **dacpac** = istanza di applicazione livello dati<br /><br /> **account di accesso**<br /><br /> **database**|  
|**action_status**|**tinyint**|Codice di identificazione dello stato corrente dell'azione:<br /><br /> **0** = in sospeso<br /><br /> **1** = esito positivo<br /><br /> **2** = esito negativo|  
|**action_status_name**|**varchar (11)**|Stato corrente dell'azione:<br /><br /> **in sospeso**<br /><br /> **operazione riuscita**<br /><br /> **esito negativo**|  
|**Obbligatorio**|**bit**|Utilizzato dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] per il rollback di un'operazione dell'applicazione livello dati.|  
|**dac_object_name_pretran**|**sysname**|Nome dell'oggetto prima dell'esecuzione del commit della transazione contenente l'azione. Utilizzato solo per database e account di accesso.|  
|**dac_object_name_posttran**|**sysname**|Nome dell'oggetto dopo l'esecuzione del commit della transazione contenente l'azione. Utilizzato solo per database e account di accesso.|  
|**in SqlScript**|**nvarchar(max)**|Script [!INCLUDE[tsql](../../includes/tsql-md.md)] che implementa un'azione in un database o account di accesso.|  
|**payload**|**varbinary(max)**|Definizione del pacchetto di applicazione livello dati salvata in una stringa codificata binaria.|  
|**Commenti**|**varchar(max)**|Consente di registrare l'accesso di un utente che ha accettato la possibile perdita dei dati in un aggiornamento dell'applicazione livello dati.|  
|**ERROR_STRING**|**nvarchar(max)**|Messaggio di errore generato se l'azione rileva un errore.|  
|**created_by**|**sysname**|Account di accesso che ha avviato l'azione di creazione questa voce.|  
|**Date_Created**|**datetime**|Data e ora di creazione della voce.|  
|**date_modified**|**datetime**|Data e ora dell'ultima modifica della voce.|  
  
## <a name="remarks"></a>Osservazioni  
 Le azioni di gestione di applicazione livello dati, quali ad esempio la distribuzione o l'eliminazione di un'applicazione livello dati, generano più passaggi. A ogni azione viene assegnato un identificatore dell'azione. Ogni passaggio viene assegnato un numero di sequenza e una riga **sysdac_history_internal**, in cui viene registrato lo stato del passaggio. Ogni riga viene creata all'avvio del passaggio dell'azione e aggiornata in base alle necessità per riflettere lo stato dell'operazione. Ad esempio, un'operazione di distribuzione dell'applicazione livello dati può essere assegnata **action_id** 12 e quattro righe **sysdac_history_internal**:  
  
|||||  
|-|-|-|-|  
|**action_id**|**sequence_id**|**action_type_name**|**dac_object_type_name**|  
|12|0|create|dacpac|  
|12|1|create|login|  
|12|2|create|database|  
|12|3|ridenominazione|database|  
  
 Operazioni di applicazione livello dati, ad esempio elimina, non rimuovono le righe da **sysdac_history_internal**. È possibile utilizzare la query seguente per eliminare manualmente le righe per le applicazioni livello dati non più distribuite su un'istanza di [!INCLUDE[ssDE](../../includes/ssde-md.md)]:  
  
```tsql  
DELETE FROM msdb.dbo.sysdac_history_internal  
WHERE instance_id NOT IN  
   (SELECT instance_id  
    FROM msdb.dbo.sysdac_instances_internal);  
```  
  
 L'eliminazione delle righe per le applicazioni livello dati attive non influisce sulle operazioni di applicazione livello dati; l'unico effetto è che non sarà possibile registrare la cronologia completa dell'applicazione livello dati.  
  
> [!NOTE]  
>  Attualmente non è disponibile alcun meccanismo per l'eliminazione di **sysdac_history_internal** le righe sul [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo predefinito del server sysadmin. Accesso in sola lettura a questa vista è disponibile per tutti gli utenti con autorizzazioni per connettersi al database master.  
  
## <a name="see-also"></a>Vedere anche  
 [Applicazioni livello dati](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [dbo.sysdac_instances &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md)   
 [sysdac_instances_internal &#40; Transact-SQL &#41;](../../relational-databases/system-tables/data-tier-application-tables-sysdac-instances-internal.md)  
  
  
