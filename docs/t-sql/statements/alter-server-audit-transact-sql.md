---
title: ALTER SERVER AUDIT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SERVER_AUDIT_TSQL
- ALTER SERVER AUDIT
dev_langs:
- TSQL
helpviewer_keywords:
- server audit [SQL Server]
- audits [SQL Server], specification
- ALTER SERVER AUDIT statement
ms.assetid: 63426d31-7a5c-4378-aa9e-afcf4f64ceb3
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d2522a2876165f8e18222f2268dad091a6ba342
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-server-audit--transact-sql"></a>ALTER SERVER AUDIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Consente di modificare un oggetto Server Audit utilizzando la funzionalità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit. Per altre informazioni, vedere [SQL Server Audit &#40;Motore di database&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
ALTER SERVER AUDIT audit_name  
{  
    [ TO { { FILE ( <file_options> [, ...n] ) } | APPLICATION_LOG | SECURITY_LOG } ]  
    [ WITH ( <audit_options> [ , ...n] ) ]   
    [ WHERE <predicate_expression> ]  
}  
| REMOVE WHERE  
| MODIFY NAME = new_audit_name  
[ ; ]  
  
<file_options>::=  
{  
      FILEPATH = 'os_file_path'   
    | MAXSIZE = { max_size { MB | GB | TB } | UNLIMITED }   
    | MAX_ROLLOVER_FILES = { integer | UNLIMITED }   
    | MAX_FILES = integer   
    | RESERVE_DISK_SPACE = { ON | OFF }   
}  
  
<audit_options>::=  
{  
      QUEUE_DELAY = integer   
    | ON_FAILURE = { CONTINUE | SHUTDOWN | FAIL_OPERATION }   
    | STATE = = { ON | OFF }   
}  
  
<predicate_expression>::=  
{  
    [NOT ] <predicate_factor>   
    [ { AND | OR } [NOT ] { <predicate_factor> } ]   
    [,...n ]  
}  
  
<predicate_factor>::=   
    event_field_name { = | < > | ! = | > | > = | < | < = } { number | ' string ' }  
```  
  
## <a name="arguments"></a>Argomenti  
 TO { FILE | APPLICATION_LOG | SECURITY }  
 Determina la posizione della destinazione del controllo. Le opzioni possibili sono un file binario, il registro applicazioni o il registro di sicurezza di Windows.  
  
 FILEPATH **= '***os_file_path***'**  
 Percorso dell'itinerario di controllo. Il nome del file viene generato in base al nome e al GUID del controllo.  
  
 MAXSIZE  **=**  *max_size*  
 Specifica le dimensioni massime consentite per il file di controllo. Il *max_size* valore deve essere un numero intero seguito da **MB**, **GB**, **TB**, o **UNLIMITED**. La dimensione minima che è possibile specificare per *max_size* è 2 **MB** e il valore massimo è 2.147.483.647 **TB**. Quando **UNLIMITED** viene specificato, il file aumenta fino a quando il disco è pieno. Specifica un valore inferiore a 2 MB genera l'errore MSG_MAXSIZE_TOO_SMALL. Il valore predefinito è **UNLIMITED**.  
  
 MAX_ROLLOVER_FILES  **=**  *intero* | **illimitato**  
 Viene specificato il numero massimo di file da mantenere nel file system. Quando l'impostazione MAX_ROLLOVER_FILES = 0, non vi è alcun limite al numero di file di rollover che vengono creati. Il valore predefinito è 0. Il numero massimo di file specificabili è 2.147.483.647.  
  
 MAX_FILES =*integer*  
 Viene specificato il numero massimo di file di controllo che possono essere creati. Passano al primo file quando viene raggiunto il limite. Quando viene raggiunto il limite MAX_FILES, qualsiasi azione che causa la generazione di eventi controllo aggiuntivi avrà esito negativo con un errore.  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 RESERVE_DISK_SPACE  **=**  {ON | OFF}  
 Questa opzione consente di preallocare il file sul disco in base al valore MAXSIZE. Viene applicata solo se MAXSIZE non è uguale a UNLIMITED. Il valore predefinito è OFF.  
  
 QUEUE_DELAY  **=**  *integer*  
 Specifica la quantità di tempo in millisecondi che può trascorrere prima che venga forzata l'esecuzione delle azioni di controllo. Il valore 0 indica un recapito sincrono. Il valore minimo di ritardo di query che è possibile impostare è 1000 (1 secondo). Tale valore è quello predefinito. Il valore massimo è 2.147.483.647 (2.147.483,647 secondi o 24 giorni, 20 ore, 31 minuti e 23,647 secondi). Specifica un numero non valido, genera l'errore MSG_INVALID_QUEUE_DELAY.  
  
 ON_FAILURE  **=**  {CONTINUA | ARRESTO | FAIL_OPERATION}  
 Viene indicato se l'istanza tramite cui viene effettuata l'operazione di scrittura nella destinazione deve comportare l'esito negativo, la continuazione o l'arresto se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è in grado di scrivere nel log di controllo.  
  
 CONTINUE  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le operazioni di SQL Server continuano. I record di controllo non vengono mantenuti. Il controllo continua a tentare di accedere a eventi e verrà ripreso se viene risolta la condizione di errore. Selezionare l'opzione per continuare, è possibile consentire l'attività non certificata che potrebbe violare i criteri di sicurezza. Utilizzare questa opzione quando il funzionamento del [!INCLUDE[ssDE](../../includes/ssde-md.md)] è più importante della gestione di un controllo completo.  
  
SHUTDOWN  
Forza l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'arresto, se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non riesce a scrivere dati nella destinazione di controllo per qualsiasi motivo. L'account di accesso in esecuzione il `ALTER` istruzione deve includere il `SHUTDOWN` autorizzazione all'interno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il comportamento di arresto persiste anche se il `SHUTDOWN` autorizzazione viene revocata in un secondo momento dall'account di accesso in esecuzione. Se l'utente non ha questa autorizzazione, l'istruzione avrà esito negativo e il controllo non verrà modificato. Utilizzare l'opzione quando un errore a livello di controllo potrebbe compromettere la sicurezza o l'integrità del sistema. Per ulteriori informazioni, vedere [arresto](../../t-sql/language-elements/shutdown-transact-sql.md). 
  
 FAIL_OPERATION  
 Le azioni del database non vengono completate se provocano eventi controllati. Le azioni, che non provocano eventi controllati possono continuare, ma non può verificarsi alcun evento controllato. Il controllo continua a tentare di accedere a eventi e verrà ripreso se viene risolta la condizione di errore. Utilizzare questa opzione quando la gestione di un controllo completo è più importante dell'accesso completo al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].   
  
 STATO  **=**  {ON | OFF}  
 Consente di abilitare o disabilitare la raccolta dei record mediante il controllo. La modifica dello stato di un controllo in esecuzione (da ON a OFF) crea una voce che indica l'arresto del controllo, l'entità che ha arrestato il controllo e l'ora in cui si è verificata l'arresto.  
  
 Modifica nome = *new_audit_name*  
 Consente di modificare il nome del controllo. Questa opzione non può essere utilizzata con altre opzioni.  
  
 predicate_expression  
 Viene specificata l'espressione del predicato utilizzata per determinare se un evento deve essere o meno elaborato. Le espressioni del predicato possono essere composte da un massimo di 3000 caratteri, pertanto gli argomenti di tipo stringa risultano limitati.  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 event_field_name  
 Nome del campo relativo all'evento che consente di identificare l'origine del predicato. I campi del controllo sono descritti in [Sys. fn_get_audit_file &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md). È possibile controllare tutti i campi eccetto `file_name` e `audit_file_offset`.  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 number  
 È qualsiasi tipo numerico incluso **decimale**. Le limitazioni sono la mancanza di memoria fisica disponibile o un numero troppo grande per essere rappresentato come un numero intero a 64 bit.  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ' string '  
 Stringa ANSI o Unicode come richiesto dal paragone del predicato. Non viene eseguita alcuna conversione del tipo di stringa implicita per le funzioni del paragone del predicato. Il passaggio del tipo non corretto comporta un errore.  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="remarks"></a>Osservazioni  
 È necessario specificare almeno una delle clausole TO, WITH o MODIFY NAME quando si chiama ALTER AUDIT.  
  
 Per apportare modifiche a un controllo è necessario impostare lo stato del controllo sull'opzione OFF. Se ALTER AUDIT viene eseguita quando un controllo è abilitato con qualsiasi altra opzione diversa da STATE = OFF, viene visualizzato un messaggio di errore MSG_NEED_AUDIT_DISABLED.  
  
 È possibile aggiungere, modificare e rimuovere specifiche del controllo senza arrestare il controllo stesso.  
  
 Non è possibile modificare il GUID di un controllo dopo che il controllo è stato creato.  
  
## <a name="permissions"></a>Permissions  
 Per creare, modificare o eliminare un'entità del controllo del server, è necessario disporre dell'autorizzazione ALTER ANY SERVER AUDIT o CONTROL SERVER.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-changing-a-server-audit-name"></a>A. Modifica del nome di un controllo del server  
 Nell'esempio seguente il nome del controllo del server `HIPPA_Audit` viene modificato in `HIPAA_Audit_Old`.  
  
```  
USE master  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
WITH (STATE = OFF);  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
MODIFY NAME = HIPAA_Audit_Old;  
GO  
ALTER SERVER AUDIT HIPAA_Audit_Old  
WITH (STATE = ON);  
GO  
```  
  
### <a name="b-changing-a-server-audit-target"></a>B. Modifica della destinazione di un controllo del server  
 Nell'esempio seguente il controllo del server denominato `HIPPA_Audit` viene modificato in una destinazione file.  
  
```  
USE master  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
WITH (STATE = OFF);  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
TO FILE (FILEPATH ='\\SQLPROD_1\Audit\',  
          MAXSIZE = 1000 MB,  
          RESERVE_DISK_SPACE=OFF)  
WITH (QUEUE_DELAY = 1000,  
       ON_FAILURE = CONTINUE);  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
WITH (STATE = ON);  
GO  
```  
  
### <a name="c-changing-a-server-audit-where-clause"></a>C. Modifica di una clausola WHERE del controllo di un server  
 L'esempio seguente modifica where creata nell'esempio C di clausola [CREATE SERVER AUDIT &#40; Transact-SQL &#41; ](../../t-sql/statements/create-server-audit-transact-sql.md). La nuova clausola WHERE Filtra per evento definito dall'utente se pari a 27.  
  
```tsql  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = OFF)  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData]  
WHERE user_defined_event_id = 27;  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = ON);  
GO  
```  
  
### <a name="d-removing-a-where-clause"></a>D. Rimozione di una clausola WHERE  
 Nell'esempio seguente viene rimossa un'espressione del predicato della clausola WHERE.  
  
```tsql  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = OFF)  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData]  
REMOVE WHERE;  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = ON);  
GO  
```  
  
### <a name="e-renaming-a-server-audit"></a>E. Ridenominazione di un controllo del server  
 Nell'esempio seguente il nome del controllo del server viene modificato da `FilterForSensitiveData` a `AuditDataAccess`.  
  
```tsql  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = OFF)  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData]  
MODIFY NAME = AuditDataAccess;  
GO  
ALTER SERVER AUDIT [AuditDataAccess] WITH (STATE = ON);  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DROP SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CREARE DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [AUTORIZZAZIONE ALTER &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [Sys. fn_get_audit_file &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [Sys. server_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [Sys. server_file_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [server_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [Sys. server_audit_specification_details – &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [Sys. database_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [database_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [Sys.dm server_audit_status &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [Sys.dm audit_actions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [Creazione di un controllo del server e di una specifica del controllo del server](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  

