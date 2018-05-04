---
title: sp_trace_create (Transact-SQL) | Documenti Microsoft
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
- sp_trace_create_TSQL
- sp_trace_create
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_create
ms.assetid: f3a43597-4c5a-4520-bcab-becdbbf81d2e
caps.latest.revision: 38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4f01f1bb50323ec68860df15594a4d3688e5aebd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sptracecreate-transact-sql"></a>sp_trace_create (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea la definizione di una nuova traccia nello stato arrestato.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] In alternativa, usare Eventi estesi.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_trace_create [ @traceid = ] trace_id OUTPUT   
          , [ @options = ] option_value   
          , [ @tracefile = ] 'trace_file'   
     [ , [ @maxfilesize = ] max_file_size ]  
     [ , [ @stoptime = ] 'stop_time' ]  
     [ , [ @filecount = ] 'max_rollover_files' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@traceid=** ] *trace_id*  
 È il numero assegnato dal [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alla nuova traccia. Qualsiasi input dell'utente verrà ignorato. *trace_id* viene **int**, con un valore predefinito è NULL. L'utente utilizza il *trace_id* valore per identificare, modificare e controllare la traccia definita dalla stored procedure.  
  
 [  **@options=** ] *option_value*  
 Specifica le opzioni impostate per la traccia. *option_value* viene **int**, non prevede alcun valore predefinito. Gli utenti possono impostare una combinazione di queste opzioni specificando la somma dei valori delle opzioni scelte. Per attivare le opzioni TRACE_FILE_ROLLOVER e SHUTDOWN_ON_ERROR, ad esempio, è consigliabile specificare **6** per *option_value*.  
  
 Nella tabella seguente sono incluse le opzioni e le descrizioni, accompagnate dai relativi valori.  
  
|Nome opzione|Valore opzione|Description|  
|-----------------|------------------|-----------------|  
|TRACE_FILE_ROLLOVER|**2**|Specifica che quando il *max_file_size* viene raggiunto, corrente i file di traccia viene chiuso e viene creato un nuovo file. in cui verranno scritti tutti i nuovi record. Il nome del nuovo file è uguale a quello del file precedente, ma è seguito da un numero intero a indicare la sequenza. Se, ad esempio, il nome del file di traccia originale è nomefile.trc, i successivi file di traccia verranno denominati nomefile_1.trc, nomefile_2.trc e così via.<br /><br /> Man mano che vengono creati nuovi file di traccia di rollover, viene incrementato in modo sequenziale il numero aggiunto nel nome del file.<br /><br /> SQL Server utilizza il valore predefinito di *max_file_size* (5 MB) se questa opzione viene specificata senza specificare un valore per *max_file_size*.|  
|SHUTDOWN_ON_ERROR|**4**|Specifica che se non è possibile scrivere nel file per un qualsiasi motivo, SQL Server viene arrestato. Questa opzione risulta utile quando si eseguono tracce di controllo della sicurezza.|  
|TRACE_PRODUCE_BLACKBOX|**8**|Specifica che il server salverà un record contenente gli ultimi 5 MB di informazioni di traccia generate dal server. TRACE_PRODUCE_BLACKBOX è incompatibile con tutte le altre opzioni.|  
  
 [  **@tracefile=** ] *'**trace_file**'*  
 Specifica il percorso e il nome di file in cui verrà scritta la traccia. *trace_file* viene **nvarchar(245)** non prevede alcun valore predefinito. *trace_file* può essere una directory locale (ad esempio N 'C:\MSSQL\Trace\trace.trc') o un percorso UNC di una condivisione o un percorso (N'\\\\*nomeserver*\\*Sharename* \\ *Directory*\trace.trc').  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verrà aggiunto un **trc** estensione a tutti i nomi di file di traccia. Se l'opzione TRACE_FILE_ROLLOVER e un *max_file_size* vengono specificati, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crea un nuovo file di traccia quando raggiunge la dimensione massima file di traccia originale. Il nuovo file con lo stesso nome di file originale, ma _*n* viene aggiunto per indicare la sequenza, iniziando **1**. Ad esempio, se il primo file di traccia denominato **nomefile.trc**, il secondo file di traccia è denominato **filename_1.trc**.  
  
 Se si utilizza l'opzione TRACE_FILE_ROLLOVER, si consiglia di non utilizzare caratteri di sottolineatura nel nome del file di traccia originale. Se vengono utilizzati caratteri di sottolineatura, si verifica il comportamento seguente:  
  
-   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] non carica automaticamente o richiesta di caricare i file di rollover (se configurata una di queste opzioni di rollover dei file).  
  
-   La funzione fn_trace_gettable non carica i file di rollover (quando è specificato utilizzando il *number_files* argomento) in cui il nome del file originale termina con un carattere di sottolineatura e un valore numerico. Ciò non vale per il carattere di sottolineatura e il numero che vengono aggiunti automaticamente all'esecuzione del rollover di un file.  
  
> [!NOTE]  
>  Come soluzione alternativa a entrambi questi comportamenti, è possibile rinominare i file in modo da rimuovere i caratteri di sottolineatura nel nome del file originale. Ad esempio, se il file originale è denominato **my_trace.trc**, e il file di rollover è denominato **my_trace_1.trc**, è possibile rinominare i file **mytrace.trc** e **mytrace_1.trc** prima di aprire i file in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 *trace_file* non può essere specificato quando viene utilizzata l'opzione TRACE_PRODUCE_BLACKBOX.  
  
 [ **@maxfilesize=** ] *max_file_size*  
 Specifica le dimensioni massime in megabyte (MB) che possono essere raggiunte da un file di traccia. *valore di max_file_size* viene **bigint**, con valore predefinito è **5**.  
  
 Se questo parametro viene specificato senza l'opzione TRACE_FILE_ROLLOVER, la traccia viene arrestata la registrazione al file quando lo spazio su disco utilizzato supera la quantità specificata da *max_file_size*.  
  
 [  **@stoptime=** ] **'***stop_time***'**  
 Specifica la data e l'ora in cui la traccia verrà arrestata. *stop_time* viene **datetime**, con un valore predefinito è NULL. Se il valore è NULL, la traccia viene eseguita fino a quando non viene arrestata in modo manuale o fino all'arresto del server.  
  
 Se entrambi *stop_time* e *max_file_size* vengono specificati, e TRACE_FILE_ROLLOVER, non è specificato, la traccia alto quando viene raggiunta l'ora di arresto specificata o di dimensioni massime del file. Se *stop_time*, *max_file_size*e vengono specificati TRACE_FILE_ROLLOVER, la traccia viene arrestata all'ora specificata, presupponendo che la traccia non venga riempito l'unità.  
  
 [ **@filecount=** ] **'***max_rollover_files***'**  
 Specifica il numero massimo di file di traccia da mantenere con lo stesso nome file di base. *MAX_ROLLOVER_FILES* viene **int**, maggiore di uno. Questo parametro è valido solo se è specificata l'opzione TRACE_FILE_ROLLOVER. Quando *max_rollover_files* è specificato, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tenta di non più di *max_rollover_files* eliminando il file di traccia meno recente prima di aprire un nuovo file di traccia. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene tenuto traccia dell'età dei file di traccia aggiungendo un numero al nome del file di base.  
  
 Ad esempio, quando il *trace_file* parametro è specificato come "c:\mytrace", un file con nome "c:\mytrace_123.trc" è precedente rispetto a un file con il nome "c:\mytrace_124.trc". Se *max_rollover_files* è impostato su 2, il Server SQL elimina il file "c:\mytrace_123.trc" prima di creare il file di traccia "c:\mytrace_125.trc".  
  
 Si noti che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tenta di eliminare un file una sola volta e non può eliminare un file se questo è utilizzato da un altro processo. Se, pertanto, un'altra applicazione sta utilizzando i file di traccia mentre è in esecuzione la traccia, è possibile che tali file vengano lasciati nel file system da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="return-code-values"></a>Valori restituiti  
 Nella tabella seguente vengono descritti i possibili valori di codice visualizzati al completamento della stored procedure.  
  
|Codice restituito|Description|  
|-----------------|-----------------|  
|0|Nessun errore.|  
|1|Errore sconosciuto.|  
|10|Opzioni non valide. Restituito quando le opzioni specificate sono incompatibili.|  
|12|Creazione del file non riuscita.|  
|13|Memoria esaurita. Restituito quando la quantità di memoria disponibile non è sufficiente per eseguire l'azione specificata.|  
|14|Ora di arresto non valida. Restituito quando l'ora specificata è già trascorsa.|  
|15|Parametri non validi. Restituito quando l'utente specifica parametri incompatibili.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_trace_create** è un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedure che esegue molte delle azioni eseguite dalle **xp_trace _\***  extended stored procedure disponibili nelle versioni precedenti di SQL Server. Utilizzare **sp_trace_create** invece di:  
  
-   **xp_trace_addnewqueue**  
  
-   **xp_trace_setqueuecreateinfo**  
  
-   **xp_trace_setqueuedestination**  
  
 **sp_trace_create** crea solo una definizione di traccia. non per avviare o modificare una traccia.  
  
 I parametri di traccia SQL tutte le stored procedure (**sp_trace_xx**) sono fortemente tipizzati. Se questi parametri non vengono chiamati con i tipi di dati corretti per i parametri di input, come indicato nella descrizione dell'argomento, la stored procedure restituirà un errore.  
  
 Per **sp_trace_create**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di servizio deve disporre dell'autorizzazione di scrittura nella cartella di file di traccia. Se l'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è un amministratore nel computer in cui si trova il file di traccia, è necessario concedere esplicitamente l'autorizzazione di scrittura all'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  È possibile caricare automaticamente il file di traccia creato con **sp_trace_create** in una tabella utilizzando il **fn_trace_gettable** funzione di sistema. Per informazioni su come usare questa funzione di sistema, vedere [sys.fn_trace_gettable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md).  
  
 Per un esempio dell'uso di stored procedure relative alla traccia, vedere [Creare una traccia &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
 **TRACE_PRODUCE_BLACKBOX** presenta le caratteristiche seguenti:  
  
-   È costituito da una traccia di rollover. Il valore predefinito *conteggio_file* è 2, ma può essere sottoposto a override dall'utente utilizzando *filecount* opzione.  
  
-   Il valore predefinito *file_size* Analogamente alle altre tracce è 5 MB e può essere modificato.  
  
-   Non è possibile specificare alcun nome di file. Il file verrà salvato come: **N'%SQLDIR%\MSSQL\DATA\blackbox.trc'**  
  
-   Nella traccia saranno contenuti solo gli eventi seguenti e le relative colonne:  
  
    -   **Avvio RPC**  
  
    -   **Avvio batch**  
  
    -   **Eccezione**  
  
    -   **Attenzione**  
  
-   Non è possibile aggiungere o rimuovere eventi o colonne da questa traccia.  
  
-   Non è possibile specificare i filtri per questa traccia.  
  
## <a name="permissions"></a>Autorizzazioni  
 L'utente deve disporre delle autorizzazioni ALTER TRACE.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [Traccia SQL](../../relational-databases/sql-trace/sql-trace.md)  
  
  
