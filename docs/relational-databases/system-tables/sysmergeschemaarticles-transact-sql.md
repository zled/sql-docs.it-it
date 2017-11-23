---
title: sysmergeschemaarticles (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sysmergeschemaarticles_TSQL
- sysmergeschemaarticles
dev_langs: TSQL
helpviewer_keywords: sysmergeschemaarticles system table
ms.assetid: b5085979-2f76-48e1-bf3b-765a84003dd9
caps.latest.revision: "27"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 13a3104b8f457cf4c9d223630739e3cf6eb76ee8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysmergeschemaarticles-transact-sql"></a>sysmergeschemaarticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Tiene traccia degli articoli solo schema per la replica di tipo merge. Questa tabella è archiviata nei database di pubblicazione e di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome dell'articolo solo schema nella pubblicazione di tipo merge.|  
|**tipo**|**tinyint**|Specifica il tipo dell'articolo solo schema. I possibili valori sono i seguenti:<br /><br /> **0x20** = articolo solo schema procedura archiviato.<br /><br /> **0x40** = articolo solo schema di vista o articolo solo schema di vista indicizzata.|  
|**ObjID**|**int**|Identificatore dell'oggetto di base dell'articolo. Può corrispondere all'identificatore di oggetto di una procedura, una vista, una vista indicizzata o una funzione definita dall'utente.|  
|**artid**|**uniqueidentifier**|ID dell'articolo.|  
|**Descrizione**|**nvarchar(255)**|Descrizione dell'articolo.|  
|**pre_creation_command**|**tinyint**|Azione predefinita da eseguire quando viene creato l'articolo nel database di sottoscrizione:<br /><br /> **0 =** nessuno - se la tabella esiste già nel Sottoscrittore, viene eseguita alcuna azione.<br /><br /> **1** = eliminazione: Elimina la tabella prima di crearne uno nuovo.<br /><br /> **2** = delete-esegue un'operazione di eliminazione in base alla clausola WHERE nel filtro di subset.<br /><br /> **3** = troncamento-uguale a **2**, ma Elimina pagine anziché righe. La clausola WHERE in questo caso non viene utilizzata.|  
|**pubid**|**uniqueidentifier**|Identificatore univoco della pubblicazione.|  
|**status**|**tinyint**|Specifica lo stato dell'articolo solo schema. I possibili valori sono i seguenti:<br /><br /> **1** = non sincronizzato: lo script di elaborazione iniziale per pubblicare la tabella viene eseguito alla successiva esecuzione dell'agente Snapshot.<br /><br /> **2** = attivo: è stato eseguito lo script di elaborazione iniziale per pubblicare la tabella.<br /><br /> **5** = New_inactive: da aggiungere.<br /><br /> **6** = New_active: da aggiungere.|  
|**creation_script**|**nvarchar(255)**|Percorso e nome di uno script pre-snapshot facoltativo dello schema dell'articolo utilizzato per la creazione della tabella di destinazione.|  
|**schema_option**|**Binary (8)**|Mappa di bit dell'opzione di generazione dello schema per l'articolo solo schema specificato. Può essere il risultato di un'operazione con OR logico bit per bit eseguita su uno o più dei valori seguenti:<br /><br /> **0x00** = disable scripting dall'agente Snapshot e utilizza lo script CreationScript fornito.<br /><br /> **0x01** = genera la creazione di oggetti (CREATE TABLE, CREATE PROCEDURE e così via).<br /><br /> **0x10** = genera un indice cluster corrispondente.<br /><br /> **0x20** = convertire i tipi di dati definiti dall'utente per i tipi di dati di base.<br /><br /> **0x40** = indice non cluster corrispondenti genera o gli indici.<br /><br /> **0x80** = Include l'integrità referenziale dichiarata nelle chiavi primarie.<br /><br /> **0x100** = replica i trigger utente su un articolo di tabella, se definito.<br /><br /> **0x200** = replicati vincoli di chiave esterna. Se la tabella con riferimenti non fa parte di una pubblicazione, tutti i vincoli di chiave esterna su una tabella pubblicata non vengono replicati.<br /><br /> **0x400** = replica i vincoli check.<br /><br /> **0x800** = replica i valori predefiniti.<br /><br /> **0x1000** = replica delle regole di confronto a livello di colonna.<br /><br /> **0x2000** = replica le proprietà estese associate oggetto di origine dell'articolo pubblicato.<br /><br /> **0x4000** = replica le chiavi univoche se definite in un articolo di tabella.<br /><br /> **0x8000** = replicare una chiave primaria e le chiavi univoche in una tabella dell'articolo come vincoli tramite istruzioni ALTER TABLE.<br /><br /> Per ulteriori informazioni sui possibili valori di **schema_option**, vedere [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).|  
|**destination_object**|**sysname**|Nome dell'oggetto di destinazione nel database di sottoscrizione. Viene utilizzato solo per articoli solo schema, quali articoli di stored procedure, viste e funzioni definite dall'utente.|  
|**destination_owner**|**sysname**|Il proprietario dell'oggetto nel database di sottoscrizione, in caso contrario **dbo**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
