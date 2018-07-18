---
title: sp_send_dbmail (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sendmail_sp_TSQL
- sendmail_sp
- SP_SEND_DBMAIL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_send_dbmail
ms.assetid: f1d7a795-a3fd-4043-ac4b-c781e76dab47
caps.latest.revision: 72
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bb9d8aefaa01061587e0d0ca5d299499b26af6e2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33262964"
---
# <a name="spsenddbmail-transact-sql"></a>sp_send_dbmail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Invia un messaggio di posta elettronica ai destinatari specificati. Il messaggio può includere il set dei risultati di una query, file allegati o entrambi. Quando il messaggio viene inserito correttamente nella coda di posta elettronica Database, **sp_send_dbmail** restituisce il **mailitem_id** del messaggio. Questa stored procedure è nel **msdb** database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_send_dbmail [ [ @profile_name = ] 'profile_name' ]  
    [ , [ @recipients = ] 'recipients [ ; ...n ]' ]  
    [ , [ @copy_recipients = ] 'copy_recipient [ ; ...n ]' ]  
    [ , [ @blind_copy_recipients = ] 'blind_copy_recipient [ ; ...n ]' ]  
    [ , [ @from_address = ] 'from_address' ]  
    [ , [ @reply_to = ] 'reply_to' ]   
    [ , [ @subject = ] 'subject' ]   
    [ , [ @body = ] 'body' ]   
    [ , [ @body_format = ] 'body_format' ]  
    [ , [ @importance = ] 'importance' ]  
    [ , [ @sensitivity = ] 'sensitivity' ]  
    [ , [ @file_attachments = ] 'attachment [ ; ...n ]' ]  
    [ , [ @query = ] 'query' ]  
    [ , [ @execute_query_database = ] 'execute_query_database' ]  
    [ , [ @attach_query_result_as_file = ] attach_query_result_as_file ]  
    [ , [ @query_attachment_filename = ] query_attachment_filename ]  
    [ , [ @query_result_header = ] query_result_header ]  
    [ , [ @query_result_width = ] query_result_width ]  
    [ , [ @query_result_separator = ] 'query_result_separator' ]  
    [ , [ @exclude_query_output = ] exclude_query_output ]  
    [ , [ @append_query_error = ] append_query_error ]  
    [ , [ @query_no_truncate = ] query_no_truncate ]   
    [ , [ @query_result_no_padding = ] @query_result_no_padding ]   
    [ , [ @mailitem_id = ] mailitem_id ] [ OUTPUT ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@profile_name=** ] **'***profile_name***'**  
 Nome del profilo da cui inviare il messaggio. Il *profile_name* è di tipo **sysname**, con un valore predefinito è NULL. Il *profile_name* deve essere il nome di un profilo di posta elettronica Database esistente. Se non si *profile_name* è specificato, **sp_send_dbmail** utilizza il profilo privato predefinito per l'utente corrente. Se l'utente non dispone di un profilo privato predefinito, **sp_send_dbmail** utilizza il profilo pubblico predefinito per il **msdb** database. Se l'utente non dispone di un profilo privato predefinito ed è presente alcun profilo pubblico predefinito per il database, **@profile_name** deve essere specificato.  
  
 [  **@recipients=** ] **'***destinatari***'**  
 Elenco delimitato da punti e virgola degli indirizzi di posta elettronica a cui inviare il messaggio. L'elenco dei destinatari è di tipo **varchar (max)**. Anche se questo parametro è facoltativo, almeno uno dei **@recipients**, **@copy_recipients**, o **@blind_copy_recipients** devono essere specificati, o **sp _ send_dbmail** restituisce un errore.  
  
 [  **@copy_recipients=** ] **'***copy_recipients***'**  
 Elenco delimitato da punti e virgola degli indirizzi di posta elettronica a cui inviare una copia per conoscenza del messaggio. L'elenco di destinatari della copia è di tipo **varchar (max)**. Anche se questo parametro è facoltativo, almeno uno dei **@recipients**, **@copy_recipients**, o **@blind_copy_recipients** devono essere specificati, o **sp _ send_dbmail** restituisce un errore.  
  
 [  **@blind_copy_recipients=** ] **'***blind_copy_recipients***'**  
 Elenco delimitato da punti e virgola degli indirizzi di posta elettronica a cui inviare una copia per conoscenza nascosta del messaggio. L'elenco dei destinatari in copia nascosta è di tipo **varchar (max)**. Anche se questo parametro è facoltativo, almeno uno dei **@recipients**, **@copy_recipients**, o **@blind_copy_recipients** devono essere specificati, o **sp _ send_dbmail** restituisce un errore.  
  
 [  **@from_address=** ] **'***from_address***'**  
 Valore dell'"indirizzo del mittente" del messaggio di posta elettronica. Si tratta di un parametro facoltativo utilizzato per eseguire l'override delle impostazioni nel profilo di posta elettronica. Questo parametro è di tipo **varchar (max)**. Le impostazioni di sicurezza SMTP determinano se questi override vengono accettati. Se non è specificato alcun parametro, il valore predefinito è NULL.  
  
 [  **@reply_to=** ] **'***reply_to***'**  
 Valore dell'"indirizzo del destinatario" del messaggio di posta elettronica. Accetta un solo indirizzo di posta elettronica come valore valido. Si tratta di un parametro facoltativo utilizzato per eseguire l'override delle impostazioni nel profilo di posta elettronica. Questo parametro è di tipo **varchar (max)**. Le impostazioni di sicurezza SMTP determinano se questi override vengono accettati. Se non è specificato alcun parametro, il valore predefinito è NULL.  
  
 [  **@subject=** ] **'***soggetto***'**  
 Oggetto del messaggio di posta elettronica. L'oggetto è di tipo **nvarchar (255)**. Se l'oggetto viene omesso, il valore predefinito è "Messaggio SQL Server".  
  
 [  **@body=** ] **'***corpo***'**  
 Corpo del messaggio di posta elettronica. Il corpo del messaggio è di tipo **nvarchar (max)**, con un valore predefinito è NULL.  
  
 [  **@body_format=** ] **'***body_format***'**  
 Formato del corpo del messaggio. Il parametro è di tipo **varchar (20)**, con un valore predefinito è NULL. Se specificato, le intestazioni del messaggio in uscita vengono impostate in modo da indicare che per il corpo del messaggio è impostato il formato specificato. Il parametro può includere uno dei valori seguenti:  
  
-   TEXT  
  
-   HTML  
  
 Il valore predefinito è TEXT.  
  
 [  **@importance=** ] **'***importanza***'**  
 Priorità del messaggio. Il parametro è di tipo **varchar(6)**. Il parametro può includere uno dei valori seguenti:  
  
-   Basso  
  
-   Normale  
  
-   Alto  
  
 Il valore predefinito è Normal.  
  
 [  **@sensitivity=** ] **'***sensibilità***'**  
 Riservatezza del messaggio. Il parametro è di tipo **varchar(12)**. Il parametro può includere uno dei valori seguenti:  
  
-   Normale  
  
-   Personal  
  
-   Privato  
  
-   Confidential  
  
 Il valore predefinito è Normal.  
  
 [  **@file_attachments=** ] **'***file_attachments***'**  
 Elenco delimitato da punti e virgola dei nomi di file da allegare al messaggio di posta elettronica. I file nell'elenco devono essere specificati come percorsi assoluti. L'elenco degli allegati è di tipo **nvarchar (max)**. Per impostazione predefinita, Posta elettronica database limita le dimensioni degli allegati a 1 MB per file.  
  
 [  **@query=** ] **'***query***'**  
 Query da eseguire. I risultati della query possono essere allegati come file o inclusi nel corpo del messaggio di posta elettronica. La query è di tipo **nvarchar (max)** e può contenere qualsiasi [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni. Si noti che la query viene eseguita in una sessione separata, pertanto le variabili locali nello script che chiama **sp_send_dbmail** non sono disponibili per la query.  
  
 [  **@execute_query_database=** ] **'***execute_query_database***'**  
 Contesto del database in cui la stored procedure esegue la query. Il parametro è di tipo **sysname**, con un valore predefinito del database corrente. Questo parametro è applicabile solo se **@query** specificato.  
  
 [  **@attach_query_result_as_file=** ] *attach_query_result_as_file*  
 Specifica se il set di risultati della query viene restituito come file allegato. *attach_query_result_as_file* è di tipo **bit**, con un valore predefinito è 0.  
  
 Quando il valore è 0, i risultati della query vengono inclusi nel corpo del messaggio di posta elettronica, dopo il contenuto di **@body** parametro. Con il valore 1, i risultati vengono restituiti come allegato. Questo parametro è applicabile solo se **@query** specificato.  
  
 [  **@query_attachment_filename=** ] *query_attachment_filename*  
 Specifica il nome di file da utilizzare per il set di risultati dell'allegato query. *query_attachment_filename* è di tipo **nvarchar(255**, con un valore predefinito è NULL. Questo parametro viene ignorato quando *attach_query_result* è 0. Quando *attach_query_result* è 1 e questo parametro è NULL, posta elettronica Database crea un nome file arbitrario.  
  
 [  **@query_result_header=** ] *query_result_header*  
 Specifica se includere le intestazioni di colonna nei risultati della query. Il valore di query_result_header è di tipo **bit**. Quando il valore è 1, i risultati della query contengono le intestazioni di colonna. Quando il valore è 0, i risultati della query non includono le intestazioni di colonna. Per impostazione predefinita questo parametro per **1**. Questo parametro è applicabile solo se **@query** specificato.  
  
 [ **@query_result_width** =] *query_result_width*  
 Lunghezza della riga, in caratteri, per la formattazione dei risultati della query. Il *query_result_width* è di tipo **int**, con valore predefinito è 256. Il valore fornito deve essere compreso tra 10 e 32767. Questo parametro è applicabile solo se **@query** specificato.  
  
 [  **@query_result_separator=** ] **'***query_result_separator***'**  
 Carattere utilizzato per separare le colonne nell'output della query. Il separatore è di tipo **char (1)**. Il valore predefinito è ' ' (spazio).  
  
 [ **@exclude_query_output=** ] *exclude_query_output*  
 Specifica se restituire l'output dell'esecuzione della query nel messaggio di posta elettronica. **exclude_query_output** è di tipo bit e un valore predefinito è 0. Quando questo parametro è 0, l'esecuzione del **sp_send_dbmail** stored procedure stampa il messaggio restituito come risultato dell'esecuzione della query nella console. Quando questo parametro è 1, l'esecuzione del **sp_send_dbmail** stored procedure non viene stampato alcun dei messaggi di esecuzione di query nella console.  
  
 [  **@append_query_error=** ] *append_query_error*  
 Specifica se inviare il messaggio di posta elettronica quando la query specificata in restituisce un errore di **@query** argomento. **append_query_error** viene **bit**, con un valore predefinito è 0. Quando questo parametro è 1, Posta elettronica database invia il messaggio di posta elettronica e include il messaggio di errore della query nel corpo del messaggio di posta elettronica. Quando questo parametro è 0, posta elettronica Database non invia il messaggio di posta elettronica e **sp_send_dbmail** termina con codice restituito 1, che indica un errore.  
  
 [  **@query_no_truncate=** ] *query_no_truncate*  
 Specifica se eseguire la query con l'opzione che consente di evitare il troncamento dei tipi di dati di grandi dimensioni di lunghezza variabile (**varchar (max)**, **nvarchar (max)**, **varbinary (max)** **xml**, **testo**, **ntext**, **immagine**e tipi di dati definito dall'utente). Quando il parametro è impostato, i risultati della query non includono le intestazioni di colonna. Il *query_no_truncate* valore è di tipo **bit**. Quando il valore è 0 o viene omesso, la lunghezza delle colonne della query viene troncata a 256 caratteri. Quando il valore è 1, le colonne della query non vengono troncate. Il valore predefinito del parametro è 0.  
  
> [!NOTE]  
>  Se utilizzata con grandi quantità di dati, il @**query_no_truncate** opzione utilizza risorse aggiuntive e può rallentare le prestazioni del server.  
  
 [ **@query_result_no_padding** ] *@query_result_no_padding*  
 Il tipo è bit. Il valore predefinito è 0. Quando si imposta su 1, i risultati della query non sono applicato un riempimento, riducendo possibilmente le dimensioni del file. Se si imposta @query_result_no_padding su 1 e si imposta la @query_result_width parametro, il @query_result_no_padding parametro sovrascrive il @query_result_width parametro.  
  
 In questo caso, non si verifica alcun errore.  
  
 Se si imposta la @query_result_no_padding su 1 e si imposta la @query_no_truncate viene generato un errore di parametro.  
  
 [  **@mailitem_id=** ] *mailitem_id* [OUTPUT]  
 Parametro di output facoltativo restituisce il *mailitem_id* del messaggio. Il *mailitem_id* è di tipo **int**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 In caso di esito positivo viene restituito il codice 0. Qualsiasi altro valore indica esito negativo. Il codice di errore per l'istruzione non riuscita viene archiviato nel @@ERROR variabile.  
  
## <a name="result-sets"></a>Set di risultati  
 In caso di esito positivo, viene restituito il messaggio "Posta elettronica accodata".  
  
## <a name="remarks"></a>Osservazioni  
 Prima di utilizzare, è necessario abilitare posta elettronica Database utilizzando la configurazione guidata posta elettronica Database, o **sp_configure**.  
  
 **sysmail_stop_sp** arresta posta elettronica Database arrestando gli oggetti Service Broker utilizzati dal programma esterno. **sp_send_dbmail** continua ad accettare posta elettronica quando posta elettronica Database è in esecuzione usando **sysmail_stop_sp**. Per avviare posta elettronica Database, utilizzare **sysmail_start_sp**.  
  
 Quando **@profile** non viene specificato, **sp_send_dbmail** utilizza un profilo predefinito. Se l'utente che invia il messaggio di posta elettronica dispone di un profilo privato predefinito, Posta elettronica database utilizzerà tale profilo. Se l'utente non dispone di alcun profilo privato predefinito, **sp_send_dbmail** utilizza il profilo pubblico predefinito. Se è presente alcun profilo privato predefinito per l'utente e alcun profilo pubblico predefinito, **sp_send_dbmail** restituisce un errore.  
  
 **sp_send_dbmail** non supporta i messaggi di posta elettronica senza contenuto. Per inviare un messaggio di posta elettronica, è necessario specificare almeno uno dei **@body**, **@query**, **@file_attachments**, o **@subject**. In caso contrario, **sp_send_dbmail** restituisce un errore.  
  
 Per controllare l'accesso ai file, Posta elettronica database utilizza il contesto di sicurezza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows dell'utente corrente. Di conseguenza, gli utenti autenticati con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione non è possibile collegare i file usando **@file_attachments**. Windows non consente a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di passare credenziali da un computer remoto a un altro computer remoto. Per questo motivo, Posta elettronica database potrebbe non essere in grado di allegare file da una condivisione di rete nei casi in cui il comando viene eseguito da un computer diverso dal computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Se entrambi **@query** e **@file_attachments** vengono specificati e non è possibile trovare il file, la query viene comunque eseguita ma non viene inviato il messaggio di posta elettronica.  
  
 Se si specifica una query, il set dei risultati viene formattato come testo incorporato. I dati binari nel risultato vengono inviati in formato esadecimale.  
  
 I parametri **@recipients**, **@copy_recipients**, e **@blind_copy_recipients** sono elenchi delimitati da punto e virgola di indirizzi di posta elettronica. È necessario specificare almeno uno di questi parametri, o **sp_send_dbmail** restituisce un errore.  
  
 Quando si esegue **sp_send_dbmail** senza un contesto di transazione, posta elettronica Database viene avviato e viene eseguito il commit di una transazione implicita. Quando si esegue **sp_send_dbmail** all'interno di una transazione esistente, posta elettronica Database si basa su all'utente di eseguire il commit o il rollback delle modifiche. Posta elettronica database non avvia una transazione interna.  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni di esecuzione **sp_send_dbmail** per impostazione predefinita a tutti i membri del **DatabaseMailUser** nel ruolo del database il **msdb** database. Tuttavia, quando l'utente che invia il messaggio non dispone dell'autorizzazione per utilizzare il profilo per la richiesta, **sp_send_dbmail** restituisce un errore e non invia il messaggio.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-sending-an-e-mail-message"></a>A. Invio di un messaggio di posta elettronica  
 Questo esempio viene inviato un messaggio di posta elettronica a un amico utilizzando l'indirizzo di posta elettronica `myfriend@Adventure-Works.com`. L'oggetto del messaggio è `Automated Success Message`. Il corpo del messaggio contiene la frase `'The stored procedure finished successfully'`.  
  
```  
EXEC msdb.dbo.sp_send_dbmail  
    @profile_name = 'Adventure Works Administrator',  
    @recipients = 'yourfriend@Adventure-Works.com',  
    @body = 'The stored procedure finished successfully.',  
    @subject = 'Automated Success Message' ;  
```  
  
### <a name="b-sending-an-e-mail-message-with-the-results-of-a-query"></a>B. Invio di un messaggio di posta elettronica con i risultati di una query  
 Questo esempio viene inviato un messaggio di posta elettronica a un amico utilizzando l'indirizzo di posta elettronica `yourfriend@Adventure-Works.com`. L'oggetto del messaggio è `Work Order Count` e il messaggio esegue una query che visualizza il numero degli ordini di lavoro con una data di scadenza `DueDate` minore di due giorni dopo il 30 aprile 2004. I risultati vengono allegati come file di testo.  
  
```  
EXEC msdb.dbo.sp_send_dbmail  
    @profile_name = 'Adventure Works Administrator',  
    @recipients = 'yourfriend@Adventure-Works.com',  
    @query = 'SELECT COUNT(*) FROM AdventureWorks2012.Production.WorkOrder  
                  WHERE DueDate > ''2004-04-30''  
                  AND  DATEDIFF(dd, ''2004-04-30'', DueDate) < 2' ,  
    @subject = 'Work Order Count',  
    @attach_query_result_as_file = 1 ;  
```  
  
### <a name="c-sending-an-html-e-mail-message"></a>C. Invio di un messaggio di posta elettronica HTML  
 Questo esempio viene inviato un messaggio di posta elettronica a un amico utilizzando l'indirizzo di posta elettronica `yourfriend@Adventure-Works.com`. L'oggetto del messaggio è `Work Order List` e il messaggio contiene un documento HTML che visualizza gli ordini di lavoro con una data di scadenza `DueDate` minore di due giorni dopo il 30 aprile 2004. Il messaggio viene inviato in formato HTML.  
  
```  
DECLARE @tableHTML  NVARCHAR(MAX) ;  
  
SET @tableHTML =  
    N'<H1>Work Order Report</H1>' +  
    N'<table border="1">' +  
    N'<tr><th>Work Order ID</th><th>Product ID</th>' +  
    N'<th>Name</th><th>Order Qty</th><th>Due Date</th>' +  
    N'<th>Expected Revenue</th></tr>' +  
    CAST ( ( SELECT td = wo.WorkOrderID,       '',  
                    td = p.ProductID, '',  
                    td = p.Name, '',  
                    td = wo.OrderQty, '',  
                    td = wo.DueDate, '',  
                    td = (p.ListPrice - p.StandardCost) * wo.OrderQty  
              FROM AdventureWorks.Production.WorkOrder as wo  
              JOIN AdventureWorks.Production.Product AS p  
              ON wo.ProductID = p.ProductID  
              WHERE DueDate > '2004-04-30'  
                AND DATEDIFF(dd, '2004-04-30', DueDate) < 2   
              ORDER BY DueDate ASC,  
                       (p.ListPrice - p.StandardCost) * wo.OrderQty DESC  
              FOR XML PATH('tr'), TYPE   
    ) AS NVARCHAR(MAX) ) +  
    N'</table>' ;  
  
EXEC msdb.dbo.sp_send_dbmail @recipients='yourfriend@Adventure-Works.com',  
    @subject = 'Work Order List',  
    @body = @tableHTML,  
    @body_format = 'HTML' ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [Oggetti di configurazione di posta elettronica database](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Stored procedure di posta elettronica database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)  
  
  
