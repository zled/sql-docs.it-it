---
title: sysmergepublications (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysmergepublications
- sysmergepublications_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergepublications system table
ms.assetid: 7f82c6c3-22d1-47c0-a92b-4d64b98cc455
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 40763216075a551c244e72b0516e7ff2383ff913
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysmergepublications-transact-sql"></a>sysmergepublications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni pubblicazione di tipo merge definita nel database. Questa tabella è archiviata nei database di pubblicazione e di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Nome del server predefinito.|  
|**publisher_db**|**sysname**|Nome del database del server di pubblicazione predefinito.|  
|**name**|**sysname**|Nome della pubblicazione.|  
|**description**|**nvarchar(255)**|Breve descrizione della pubblicazione.|  
|**Conservazione**|**int**|Il periodo di memorizzazione per il set di intera pubblicazione, in cui l'unità è indicato dal valore della **retention_period_unit** colonna.|  
|**publication_type**|**tinyint**|Indica se la pubblicazione viene filtrata:<br /><br /> **0** = non filtrato.<br /><br /> **1** = filtrati.|  
|**pubid**|**uniqueidentifier**|Numero di identificazione univoco della pubblicazione. Viene generato durante l'aggiunta della pubblicazione.|  
|**DesignMasterID**|**uniqueidentifier**|Riservato per utilizzi futuri.|  
|**parentid**|**uniqueidentifier**|Indica la pubblicazione padre da cui la pubblicazione corrente di pari livello o subset è stata creata (utilizzato per tipologie gerarchiche di pubblicazione).|  
|**sync_mode**|**tinyint**|Modalità di sincronizzazione della pubblicazione:<br /><br /> **0** = nativa.<br /><br /> **1** = carattere.|  
|**allow_push**|**int**|Indica se la pubblicazione consente sottoscrizioni push.<br /><br /> **0** = le sottoscrizioni push non sono consentite.<br /><br /> **1** = sono consentite sottoscrizioni push.|  
|**allow_pull**|**int**|Indica se la pubblicazione consente sottoscrizioni pull.<br /><br /> **0** = le sottoscrizioni pull non consentite.<br /><br /> **1** = sono consentite sottoscrizioni pull.|  
|**allow_anonymous**|**int**|Indica se la pubblicazione consente sottoscrizioni anonime.<br /><br /> **0** = le sottoscrizioni anonime non consentite.<br /><br /> **1** = anonimo è consentito creare sottoscrizioni.|  
|**centralized_conflicts**|**int**|Indica se i record dei conflitti vengono archiviati nel server di pubblicazione:<br /><br /> **0** = i record non vengono archiviati nel server di pubblicazione con conflitti.<br /><br /> **1** = i record dei conflitti vengono archiviati nel server di pubblicazione.|  
|**status**|**tinyint**|Riservato per utilizzi futuri.|  
|**snapshot_ready**|**tinyint**|Indica lo stato dello snapshot della pubblicazione:<br /><br /> **0** = lo snapshot non è pronto per l'utilizzo.<br /><br /> **1** = lo snapshot è pronto per l'utilizzo.<br /><br /> **2** = un nuovo snapshot per la pubblicazione deve essere creata.|  
|**enabled_for_internet**|**bit**|Indica se i file di sincronizzazione per la pubblicazione sono attivati per Internet tramite il servizio FTP e altri servizi.<br /><br /> **0** = sincronizzazione file accessibili da Internet.<br /><br /> **1** = sincronizzazione file non sono accessibili da Internet.|  
|**dynamic_filters**|**bit**|Indica se la pubblicazione viene filtrata utilizzando un filtro di riga con parametri.<br /><br /> **0** = la pubblicazione viene filtrata non riga.<br /><br /> **1** = la pubblicazione viene filtrata di riga.|  
|**snapshot_in_defaultfolder**|**bit**|Specifica se i file di snapshot vengono archiviati nella cartella predefinita:<br /><br /> **0** = i file di snapshot nella cartella predefinita.<br /><br /> **1** = lo snapshot di file vengono archiviati nel percorso specificato da **alt_snapshot_folder**.|  
|**alt_snapshot_folder**|**nvarchar(255)**|Posizione della cartella alternativa per lo snapshot.|  
|**pre_snapshot_script**|**nvarchar(255)**|Puntatore a una. **sql** file che l'agente di Merge viene eseguito prima di qualsiasi oggetto di replica consente di generare script per applicare lo snapshot nel Sottoscrittore.|  
|**post_snapshot_script**|**nvarchar(255)**|Puntatore a una. **sql** file che l'agente di Merge viene eseguito dopo tutte le altre repliche script di oggetti e dati sono stati applicati durante una sincronizzazione iniziale.|  
|**compress_snapshot**|**bit**|Specifica se lo snapshot scritto il **alt_snapshot_folder** percorso viene compresso nel [!INCLUDE[msCoName](../../includes/msconame-md.md)] formato CAB. **0** indica che il file non è compresso.|  
|**ftp_address**|**sysname**|Indirizzo di rete del servizio FTP (File Transfer Protocol) per il server di distribuzione. Specifica se i file di snapshot della pubblicazione si trovano in una posizione in cui possono essere prelevati dall'agente di merge, se FTP è abilitato.|  
|**ftp_port**|**int**|Numero di porta del servizio FTP per il server di distribuzione.|  
|**ftp_subdirectory**|**nvarchar(255)**|Subdirectory della posizione in cui i file di snapshot saranno disponibili per l'agente di merge.|  
|**ftp_login**|**sysname**|Nome utente utilizzato per la connessione al servizio FTP.|  
|**ftp_password**|**nvarchar(524**|Password dell'utente utilizzata per la connessione al servizio FTP.|  
|**conflict_retention**|**int**|Viene specificato il periodo di memorizzazione dei conflitti espresso in giorni. Trascorso questo periodo, la riga con conflitti viene eliminata dalla tabella con conflitti.|  
|**keep_before_values**|**int**|Specifica se alla pubblicazione viene applicata l'ottimizzazione di sincronizzazione:<br /><br /> **0** = la sincronizzazione non è ottimizzata e le partizioni inviate a tutti i sottoscrittori verranno verificate quando si modificano i dati in una partizione.<br /><br /> **1** = la sincronizzazione è ottimizzata e vengono coinvolti solo i sottoscrittori con righe nella partizione modificata.|  
|**allow_subscription_copy**|**bit**|Specifica se la funzione di copia del database di sottoscrizione è abilitata. **0** significa copia non è consentita.|  
|**allow_synctoalternate**|**bit**|Viene specificato se è consentito l'utilizzo di un partner di sincronizzazione alternativo per la sincronizzazione con il server di pubblicazione. **0** indica che un partner di sincronizzazione non è consentito.|  
|**validate_subscriber_info**|**nvarchar(500)**|Viene visualizzato un elenco delle funzioni utilizzate per il recupero delle informazioni sul Sottoscrittore e la convalida dei criteri per i filtri di riga con parametri nel Sottoscrittore.|  
|**ad_guidname**|**sysname**|Specifica se la pubblicazione è pubblicata in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory. Un valore GUID valido indica che la pubblicazione è pubblicata in Active Directory e il GUID è l'oggetto di pubblicazione di Active Directory corrispondente **objectGUID**. Se è NULL, la pubblicazione non è pubblicata in Active Directory.|  
|**backward_comp_level**|**int**|Livello di compatibilità del database. I possibili valori sono i seguenti:<br /><br /> **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].<br /><br /> **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].|  
|**max_concurrent_merge**|**int**|Numero massimo di processi di merge simultanei consentiti. Il valore **0** per questa proprietà indica che non sono previsti limiti al numero di processi di merge simultanei in esecuzione in qualsiasi momento. Questa proprietà consente di impostare un limite al numero di processi di merge simultanei eseguibili contemporaneamente in una pubblicazione di tipo merge. Se è stata pianificata l'esecuzione simultanea di un numero di sessioni maggiore del limite consentito, le sessioni in eccesso vengono inserite in una coda dove rimangono in attesa fino al completamento del processo di merge in esecuzione.|  
|**max_concurrent_dynamic_snapshots**|**int**|Numero massimo di sessioni simultanee di snapshot di dati filtrati eseguibili nella pubblicazione di tipo merge. Se **0**, sussiste alcun limite al numero massimo di sessioni di snapshot di dati filtrati eseguibili contemporaneamente nella pubblicazione in un determinato momento. Questa proprietà consente di impostare un limite al numero di sessioni simultanee di snapshot eseguibili contemporaneamente in una pubblicazione di tipo merge. Se è stata pianificata l'esecuzione simultanea di un numero di sessioni maggiore del limite consentito, le sessioni in eccesso vengono inserite in una coda dove rimangono in attesa fino al completamento del processo di merge in esecuzione.|  
|**use_partition_groups**|**smallint**|Specifica se la pubblicazione utilizza partizioni pre-calcolate.|  
|**dynamic_filters_function_list**|**nvarchar(500)**|Elenco di funzioni delimitate da punto e virgola utilizzate nei filtri di riga con parametri della pubblicazione.|  
|**partition_id_eval_proc**|**sysname**|Specifica il nome della procedura eseguita dall'agente di merge di un Sottoscrittore per determinare il relativo ID partizione assegnato.|  
|**publication_number**|**smallint**|Specifica la colonna di identità che fornisce un mapping a 2 byte a **pubid**. **pubid** è un identificatore univoco globale per una pubblicazione, mentre il numero di pubblicazione è univoco solo in un database specificato.|  
|**replicate_ddl**|**int**|Indica se per la pubblicazione è supportata la replica dello schema.<br /><br /> **0** = DDL istruzioni non vengono replicate.<br /><br /> **1** = DDL istruzioni eseguite nel server di pubblicazione vengono replicate.<br /><br /> Per altre informazioni, vedere [Apportare modifiche allo schema nei database di pubblicazione](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).|  
|**allow_subscriber_initiated_snapshot**|**bit**|Indica che i Sottoscrittori possono inizializzare il processo che genera lo snapshot per una pubblicazione che utilizza filtri con parametri. **1** indica che i sottoscrittori possono avviare il processo di snapshot.|  
|**dynamic_snapshot_queue_timeout**|**int**|Specifica la durata, espressa in minuti, dell'attesa nella coda del processo di generazione dello snapshot da parte di un Sottoscrittore in caso di utilizzo di filtri con parametri.|  
|**dynamic_snapshot_ready_timeout**|**int**|Specifica la durata, espressa in minuti, dell'attesa del completamento del processo di generazione dello snapshot da parte di un Sottoscrittore in caso di utilizzo di filtri con parametri.|  
|**Server di distribuzione**|**sysname**|Nome del server di distribuzione per la pubblicazione.|  
|**snapshot_jobid**|**binary(16)**|Identifica il processo dell'agente che genera lo snapshot quando il Sottoscrittore è in grado di inizializzare il processo di generazione dello snapshot.|  
|**allow_web_synchronization**|**bit**|Specifica se la pubblicazione è abilitata per la sincronizzazione Web, in cui **1** significa che per la pubblicazione è abilitata la sincronizzazione Web.|  
|**web_synchronization_url**|**nvarchar(500)**|Specifica il valore predefinito dell'URL Internet utilizzato per la sincronizzazione tramite il Web.|  
|**allow_partition_realignment**|**bit**|Indica se le eliminazioni vengono inviate al Sottoscrittore quando la modifica della riga nel server di pubblicazione comporta la modifica della partizione corrispondente.<br /><br /> **0** = dati di una vecchia partizione rimangono nel Sottoscrittore, in cui le modifiche apportate a tali dati nel server di pubblicazione non verranno replicate nel Sottoscrittore, ma le modifiche apportate nel Sottoscrittore verranno replicate nel server di pubblicazione.<br /><br /> **1** = le eliminazioni eseguite nel Sottoscrittore in modo da riflettere i risultati di una modifica della partizione rimuovendo i dati che non fa più parte della partizione del sottoscrittore.<br /><br /> Per altre informazioni, vedere [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md).<br /><br /> Nota: I dati che rimangono nel Sottoscrittore quando questo valore è **0** devono essere considerati come se fosse di sola lettura; tuttavia, questo non viene necessariamente applicato dal sistema di replica.|  
|**retention_period_unit**|**tinyint**|Definisce l'unità utilizzata per la definizione *conservazione*, che può essere uno dei valori seguenti:<br /><br /> **0** = giorno.<br /><br /> **1** = settimana.<br /><br /> **2** = mese.<br /><br /> **3** = anno.|  
|**decentralized_conflicts**|**int**|Indica se i record con conflitti vengono archiviati nel Sottoscrittore che ha generato il conflitto:<br /><br /> **0** = conflitti record non vengono archiviati nel Sottoscrittore.<br /><br /> **1** = i record dei conflitti vengono archiviati nel Sottoscrittore.|  
|**generation_leveling_threshold**|**int**|Specifica il numero di modifiche contenute in una generazione. Una generazione è una raccolta di modifiche recapitate a un server di pubblicazione o a un Sottoscrittore.|  
|**automatic_reinitialization_policy**|**bit**|Indica se le modifiche vengono caricate dal Sottoscrittore prima di una reinizializzazione automatica.<br /><br /> **1** = le modifiche vengono caricate dal sottoscrittore prima che si verifichi una reinizializzazione automatica.<br /><br /> **0** = modifiche non vengono caricate prima di una reinizializzazione automatica.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica di &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_helpmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)  
  
  
