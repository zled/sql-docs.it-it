---
title: dbo. sysschedules (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.sysschedules_TSQL
- sysschedules
- sysschedules_TSQL
- dbo.sysschedules
dev_langs:
- TSQL
helpviewer_keywords:
- sysschedules system table
ms.assetid: 4cac9237-7a69-4035-bb3e-928b76aad698
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 15c683b263b8026503754e137d91d72e5ee7f0ce
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="dbosysschedules-transact-sql"></a>dbo.sysschedules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene informazioni sulle pianificazioni dei processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Questa tabella è archiviata nel **msdb** database.  
  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|ID della pianificazione dei processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.|  
|**schedule_uid**|**uniqueidentifier**|Identificatore univoco della pianificazione dei processi. Questo valore viene utilizzato per identificare una pianificazione per i processi distribuiti.|  
|**originating_server_id**|**int**|ID del server master di provenienza della pianificazione dei processi.|  
|**name**|**sysname (nvarchar(128))**|Nome definito dall'utente per la pianificazione dei processi. Il nome deve essere univoco all'interno di un processo.|  
|**owner_sid**|**varbinary(85)**|Microsoft Windows *identificatore di protezione* dell'utente o gruppo che possiede la pianificazione del processo.|  
|**enabled**|**int**|Stato della pianificazione dei processi:<br /><br /> **0** = non abilitata.<br /><br /> **1** = abilitato.<br /><br /> Quando la pianificazione non è abilitata, non verrà eseguito alcun processo su questa pianificazione.|  
|**freq_type**|**int**|Frequenza di esecuzione di un processo per questa pianificazione.<br /><br /> **1** = una sola volta<br /><br /> **4** = giornaliera<br /><br /> **8** = settimanale<br /><br /> **16** = mensile<br /><br /> **32** = mensile, relativo a **freq_interval**<br /><br /> **64** = viene eseguita all'avvio del servizio SQL Server Agent<br /><br /> **128** = viene eseguita quando il computer è inattivo|  
|**freq_interval**|**int**|Giorni in cui viene eseguito il processo. Dipende dal valore di **freq_type**. Il valore predefinito è **0**, che indica che **freq_interval** è inutilizzato. Vedere la tabella seguente per i valori possibili e i relativi effetti.|  
|**freq_subday_type**|**int**|Unità per il **freq_subday_interval**. Di seguito sono i valori possibili e le relative descrizioni.<br /><br /> <br /><br /> **1** : all'ora specificata<br /><br /> **2** : secondi<br /><br /> **4** : minuti<br /><br /> **8** : ore|  
|**freq_subday_interval**|**int**|Numero di **freq_subday_type** periodi devono intercorrere tra ogni esecuzione del processo.|  
|**freq_relative_interval**|**int**|Quando **freq_interval** si verifica in ogni mese, se **freq_interval** è **32** (frequenza mensile relativa). I possibili valori sono i seguenti:<br /><br /> **0** = **freq_relative_interval** non viene utilizzato<br /><br /> **1** = primo<br /><br /> **2** = secondi<br /><br /> **4** = terzo<br /><br /> **8** = quarto<br /><br /> **16** = ultimo|  
|**freq_recurrence_**<br /><br /> **factor**|**int**|Numero di settimane o mesi tra le esecuzioni pianificate di un processo. **freq_recurrence_factor** viene utilizzata solo se **freq_type** viene **8**, **16**, o **32**. Se questa colonna contiene **0**, **freq_recurrence_factor** è inutilizzato.|  
|**active_start_date**|**int**|Data dalla quale è possibile avviare l'esecuzione del processo. La data è nel formato AAAAMMGG. NULL indica la data odierna.|  
|**active_end_date**|**int**|Data dalla quale è possibile arrestare l'esecuzione del processo. La data è nel formato AAAAMMGG.|  
|**active_start_time**|**int**|Data compresa tra **active_start_date** e **active_end_date** inizia l'esecuzione di tale processo. L'ora è nel formato HHMMSS, a 24 ore.|  
|**active_end_time**|**int**|Data compresa tra **active_start_date** e **active_end_date** interrompe l'esecuzione di tale processo. L'ora è nel formato HHMMSS, a 24 ore.|  
|**date_created**|**datetime**|Data e ora di creazione della pianificazione.|  
|**date_modified**|**datetime**|Data e ora dell'ultima modifica della pianificazione.|  
|**version_number**|**int**|Numero di versione corrente della pianificazione. Ad esempio, se una pianificazione è stata modificata 10 volte, il **version_number** è 10.|  
  
|Valore di freq_type|Effetto su freq_interval|  
|-------------------------|------------------------------|  
|**1** (una volta)|**freq_interval** non viene utilizzato (**0**)|  
|**4** (giornaliera)|Ogni **freq_interval** giorni|  
|**8** (settimanale)|**freq_interval** corrisponde a uno o più dei valori seguenti:<br /><br /> **1** = domenica<br /><br /> **2** = lunedì<br /><br /> **4** = martedì<br /><br /> **8** = mercoledì<br /><br /> **16** = giovedì<br /><br /> **32** = venerdì<br /><br /> **64** = sabato|  
|**16** (mensile)|Nel **freq_interval** giorno del mese|  
|**32** (mensile, relativo)|**freq_interval** è uno dei seguenti:<br /><br /> **1** = domenica<br /><br /> **2** = lunedì<br /><br /> **3** = martedì<br /><br /> **4** = mercoledì<br /><br /> **5** = giovedì<br /><br /> **6** = venerdì<br /><br /> **7** = sabato<br /><br /> **8** = giorno<br /><br /> **9** = giorno feriale<br /><br /> **10** = giorno festivo|  
|**64** (inizia all'avvio del servizio SQL Server Agent)|**freq_interval** non viene utilizzato (**0**)|  
|**128** (viene eseguito quando il computer è inattivo)|**freq_interval** non viene utilizzato (**0**)|  
  
## <a name="see-also"></a>Vedere anche  
 [dbo. sysjobschedules & #40; Transact-SQL & #41;](../../relational-databases/system-tables/dbo-sysjobschedules-transact-sql.md)  
  
  
