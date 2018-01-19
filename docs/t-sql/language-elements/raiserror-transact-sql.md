---
title: RAISERROR (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 02/21/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RAISERROR
- RAISERROR_TSQL
- RAISEERROR_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sysmessages system table
- errors [SQL Server], RAISERROR statement
- user-defined error messages [SQL Server]
- system flags
- generating errors [SQL Server]
- TRY block [SQL Server]
- recording errors
- ad hoc messages
- RAISERROR statement
- CATCH block
- messages [SQL Server], RAISERROR statement
ms.assetid: 483588bd-021b-4eae-b4ee-216268003e79
caps.latest.revision: "73"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: de9b90e46c344c4d287d677c9aa17e5d635aca6d
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="raiserror-transact-sql"></a>RAISERROR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Consente di generare un messaggio di errore e di inizializzare l'elaborazione dell'errore per la sessione. RAISERROR può fare riferimento a un messaggio definito dall'utente archiviato nella vista del catalogo sys. Messages oppure compilare un messaggio in modo dinamico. Il messaggio viene restituito come messaggio di errore del server all'applicazione chiamante o a un blocco CATCH associato di un costrutto TRY…CATCH. Nuove applicazioni devono utilizzare [generare](../../t-sql/language-elements/throw-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
RAISERROR ( { msg_id | msg_str | @local_variable }  
    { ,severity ,state }  
    [ ,argument [ ,...n ] ] )  
    [ WITH option [ ,...n ] ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
RAISERROR ( { msg_str | @local_variable }  
    { ,severity ,state }  
    [ ,argument [ ,...n ] ] )  
    [ WITH option [ ,...n ] ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *msg_id*  
 Un numero di messaggio di errore definiti dall'utente viene archiviato nella vista del catalogo sys. Messages mediante sp_addmessage. I numeri di errore per i messaggi di errore definiti dall'utente devono essere maggiori di 50000. Quando *msg_id* viene omesso, RAISERROR genera un messaggio di errore con numero di errore pari a 50000.  
  
 *msg_str*  
 È simile a un messaggio definito dall'utente con la formattazione di **printf** funzione nella libreria standard C. Il messaggio di errore può contenere un massimo di 2.047 caratteri. Se contiene più di 2.048 caratteri, vengono visualizzati solo i primi 2.044 e vengono aggiunti tre punti a indicare che il messaggio è stato troncato. I parametri di sostituzione utilizzano un maggior numero di caratteri rispetto a quanto viene visualizzato nell'output a causa della gestione dell'archiviazione interna. Ad esempio, il parametro di sostituzione *%d* con un valore assegnato di 2 genera effettivamente un carattere nella stringa di messaggio, ma internamente occupa fino a tre caratteri aggiuntivi dell'archiviazione. Questo requisito a livello di archiviazione riduce il numero di caratteri disponibili per l'output del messaggio.  
  
 Quando *argomento msg_str* viene specificato, RAISERROR genera un messaggio di errore con numero di errore pari a 50000.  
  
 *argomento msg_str* è una stringa di caratteri con specifiche di conversione incorporate facoltative. Ogni specifica di conversione definisce come un valore nell'elenco di argomenti viene formattato e inserito in un campo nella posizione della specifica di conversione in *argomento msg_str*. Le specifiche di conversione sono caratterizzate dal formato seguente:  
  
 % [[*flag*] [*larghezza*] [. *precisione*] [{h | l}]] *tipo*  
  
 I parametri che possono essere usati in *argomento msg_str* sono:  
  
 *flag*  
  
 Codice che determina la spaziatura e l'allineamento del valore sostituito.  
  
|Codice|Prefisso o allineamento|Description|  
|----------|-----------------------------|-----------------|  
|- (meno)|Allineamento a sinistra|Allinea a sinistra il valore dell'argomento entro la larghezza dei campi specificata.|  
|+ (più)|Segno (prefisso)|Inserisce il segno più (+) o meno (–) all'inizio del valore dell'argomento se il valore è di tipo con segno.|  
|0 (zero)|Riempimento con zeri|Inserisce nell'output il numero necessario di zero fino al raggiungimento della larghezza minima. Se sono stati specificati 0 e il segno meno (-), 0 viene ignorato.|  
|# (simbolo di cancelletto)|Prefisso 0x per tipi esadecimali di x o di X|Quando viene utilizzato con il formato o, x o X, il simbolo di cancelletto (#) inserisce rispettivamente i caratteri 0, 0x o 0X all'inizio di qualsiasi valore diverso da zero. Il simbolo di cancelletto (#) viene ignorato se utilizzato come prefisso di d, i oppure u.|  
|' ' (spazio)|Riempimento con spazi|Inserisce spazi vuoti all'inizio di un valore con segno positivo. Viene ignorato quando è specificato con il segno più (+).|  
  
 *width*  
  
 Valore intero che definisce la larghezza minima del campo nel quale viene inserito il valore dell'argomento. Se la lunghezza del valore dell'argomento è maggiore o uguale a *larghezza*, il valore viene stampato senza alcun riempimento. Se il valore è inferiore a *larghezza*, il valore viene riempito alla lunghezza specificata *larghezza*.  
  
 Un asterisco (*) indica che la larghezza viene specificata dall'argomento associato nell'elenco di argomenti, che deve essere un valore intero.  
  
 *precisione*  
  
 Numero massimo di caratteri recuperati dal valore dell'argomento per i valori stringa. Se, ad esempio, una stringa include cinque carattere e la precisione è stata impostata su 3, vengono utilizzati solo i primi tre caratteri del valore stringa.  
  
 Per i valori integer *precisione* è il numero minimo di cifre stampate.  
  
 Un asterisco (*) indica che la precisione viene specificata dall'argomento associato nell'elenco di argomenti, che deve essere un valore intero.  
  
 {h | l} *tipo*  
  
 Viene utilizzato con tipi d, i, o, s, x, X o u e crea **shortint** (h) o **longint** valori (l).  
  
|Specifica del tipo|Rappresenta|  
|------------------------|----------------|  
|d o i|Intero con segno|  
|o|Ottale senza segno|  
|s|String|  
|u|Intero senza segno|  
|x o X|Valori esadecimali senza segno|  
  
> [!NOTE]  
>  Queste specifiche del tipo si basano su quelle originariamente definite per il **printf** funzione nella libreria standard C. Le specifiche del tipo utilizzate nella mappa di stringhe di messaggio RAISERROR per [!INCLUDE[tsql](../../includes/tsql-md.md)] tipi di dati, mentre le specifiche utilizzate **printf** mappa per tipi di dati del linguaggio C. Specifiche del tipo utilizzate **printf** non sono supportate da RAISERROR quando [!INCLUDE[tsql](../../includes/tsql-md.md)] non dispone di un tipo di dati simile al tipo di dati C associato. Ad esempio, il *%p* specifica per i puntatori non è supportata in RAISERROR perché [!INCLUDE[tsql](../../includes/tsql-md.md)] non dispone di un tipo di dati puntatore.  
  
> [!NOTE]  
>  Per convertire un valore di [!INCLUDE[tsql](../../includes/tsql-md.md)] **bigint** del tipo di dati, specificare **% I64d**.  
  
 **@** *local_variable*  
 È una variabile di qualsiasi tipo di dati carattere valido contenente una stringa formattata in modo analogo *argomento msg_str*. **@ * * * local_variable* deve essere **char** o **varchar**, o essere in grado di convertire in modo implicito in questi tipi di dati.  
  
 *severity*  
 Livello di gravità definito dall'utente associato al messaggio. Quando si utilizza *msg_id* per generare un messaggio definito dall'utente creato mediante sp_addmessage, la gravità specificata in RAISERROR sostituisce quella specificata in sp_addmessage.  
  
 I livelli di gravità da 0 a 18 possono essere specificati da qualsiasi utente, Livelli di gravità da 19 a 25 possono essere specificati solo dai membri del ruolo predefinito del ruolo del server o gli utenti dispongono dell'autorizzazione ALTER TRACE. I livelli di gravità da 19 a 25 richiedono l'opzione WITH LOG. I livelli di gravità inferiori a 0 vengono interpretati come 0. I livelli di gravità superiori a 25 vengono interpretati come 25.  
  
> [!CAUTION]  
>  I livelli di gravità da 20 a 25 sono considerati irreversibili. Se viene rilevato un livello di gravità irreversibile, la connessione del client viene interrotta dopo la ricezione del messaggio e l'errore viene registrato nel log degli errori e nel registro applicazioni.  
  
 È possibile specificare -1 per restituire il valore di gravità associato all'errore come illustrato nell'esempio seguente.  
  
```  
RAISERROR (15600,-1,-1, 'mysp_CreateCustomer');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Msg 15600, Level 15, State 1, Line 1   
 An invalid parameter or option was specified for procedure 'mysp_CreateCustomer'.
 ```  
  
 *state*  
 Valore intero compreso tra 0 e 255. Per impostazione predefinita i valori negativi su 1. I valori maggiori di 255 non devono essere utilizzati. 
  
 Se in più posizioni viene generato lo stesso errore definito dall'utente, lo stesso numero di stato univoco per ogni posizione può semplificare l'individuazione della sezione di codice in cui si sono verificati gli errori.  
  
 *argument*  
 Parametri utilizzati nella sostituzione delle variabili definite in *argomento msg_str* o il messaggio corrispondente *msg_id*. Possono essere presenti 0 o più parametri di sostituzione, ma il numero complessivo di tali parametri non può essere maggiore di 20. Ogni parametro di sostituzione può essere una variabile locale o uno di questi tipi di dati: **tinyint**, **smallint**, **int**, **char**, **varchar**, **nchar**, **nvarchar**, **binario**, o **varbinary**. Non sono supportati altri tipi di dati.  
  
 *opzione*  
 Opzione personalizzata per l'errore. Può essere uno dei valori riportati nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|LOG|Registra l'errore nel log degli errori e nel registro applicazione per l'istanza del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Gli errori registrati nel log degli errori non possono superare i 440 byte. Solo un membro del ruolo predefinito del server sysadmin o un utente con autorizzazioni ALTER TRACE può specificare WITH LOG.<br /><br /> [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)]|  
|NOWAIT|Invia i messaggi direttamente al client.<br /><br /> [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)]|  
|SETERROR|Imposta il @@ERROR e i valori ERROR_NUMBER *msg_id* o 50000, indipendentemente dal livello di gravità.<br /><br /> [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)]|  
  
## <a name="remarks"></a>Osservazioni  
 Gli errori generati da RAISERROR hanno le stesse caratteristiche degli errori generati dal codice di [!INCLUDE[ssDE](../../includes/ssde-md.md)]. I valori specificati da RAISERROR vengono segnalati da ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY, ERROR_STATE e @@ERROR funzioni di sistema. Se si esegue RAISERROR con un livello di gravità maggiore o uguale a 11 in un blocco TRY, il controllo viene trasferito al blocco CATCH associato. L'errore viene restituito al chiamante se RAISERROR viene eseguito:  
  
-   All'esterno dell'ambito di qualsiasi blocco TRY.  
  
-   Con una gravità minore o uguale a 10 in un blocco TRY.  
  
-   Con una gravità maggiore o uguale a 20; in questo caso la connessione al database viene terminata.  
  
 I blocchi CATCH possono utilizzare RAISERROR per generare nuovamente l'errore che ha richiamato il blocco CATCH mediante l'utilizzo di funzioni di sistema quali ERROR_NUMBER e ERROR_MESSAGE per recuperare le informazioni sull'errore di origine. @@ERROR è impostata su 0 per impostazione predefinita per i messaggi con un livello di gravità compreso tra 1 e 10.  
  
 Quando *msg_id* specifica il messaggio dalla colonna di testo utilizzando le stesse regole applicate al testo di un messaggio definito dall'utente specificato di un messaggio definito dall'utente disponibile nella vista del catalogo sys. Messages, i processi RAISERROR utilizzando *argomento msg_str*. Il testo del messaggio definito dall'utente può contenere specifiche di conversione; RAISERROR eseguirà il mapping dei valori degli argomenti in base a tali specifiche di conversione. Per aggiungere messaggi di errore definiti dall'utente e sp_dropmessage per eliminare i messaggi di errore definiti dall'utente, utilizzare sp_addmessage.  
  
 RAISERROR può essere utilizzato in alternativa a PRINT per restituire i messaggi alle applicazioni di chiamata. RAISERROR supporta la sostituzione di caratteri simile alla funzionalità del **printf** funzione nella libreria C standard, mentre il [!INCLUDE[tsql](../../includes/tsql-md.md)] non istruzione PRINT. L'istruzione PRINT non è interessata dai blocchi TRY, mentre un'istruzione RAISERROR eseguita con un livello di gravità da 11 a 19 in un blocco TRY trasferisce il controllo al blocco CATCH associato. Specificare un livello di gravità minore o uguale a 10 per utilizzare RAISERROR per restituire un messaggio da un blocco TRY senza richiamare il blocco CATCH.  
  
 In genere gli argomenti successivi sostituiscono le specifiche di conversione successive, ovvero il primo argomento sostituisce la prima specifica di conversione, il secondo argomento sostituisce la seconda specifica di conversione e così via. Nell'istruzione `RAISERROR` seguente, ad esempio, il primo argomento `N'number'` sostituisce la prima specifica di conversione `%s`; mentre il secondo argomento `5` sostituisce la seconda specifica di conversione `%d.`  
  
```  
RAISERROR (N'This is message %s %d.', -- Message text.  
           10, -- Severity,  
           1, -- State,  
           N'number', -- First argument.  
           5); -- Second argument.  
-- The message text returned is: This is message number 5.  
GO  
```  
  
 Se per la larghezza o la precisione di una specifica di conversione viene specificato un asterisco (*), il valore da utilizzare per la larghezza o la precisione viene specificato come valore intero dell'argomento. In questo caso, una specifica di conversione può utilizzare fino a tre argomenti, ovvero uno per la larghezza, uno per la precisione e uno per il valore di sostituzione.  
  
 Entrambe le istruzioni `RAISERROR` seguenti, ad esempio, restituiscono la stessa stringa. In una vengono inseriti i valori di larghezza e di precisione nell'elenco degli argomenti, mentre nell'altra tali valori vengono definiti nella specifica di conversione.  
  
```  
RAISERROR (N'<\<%*.*s>>', -- Message text.  
           10, -- Severity,  
           1, -- State,  
           7, -- First argument used for width.  
           3, -- Second argument used for precision.  
           N'abcde'); -- Third argument supplies the string.  
-- The message text returned is: <<    abc>>.  
GO  
RAISERROR (N'<\<%7.3s>>', -- Message text.  
           10, -- Severity,  
           1, -- State,  
           N'abcde'); -- First argument supplies the string.  
-- The message text returned is: <<    abc>>.  
GO  
```  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-error-information-from-a-catch-block"></a>A. Restituzione delle informazioni sull'errore da un blocco CATCH  
 Nell'esempio di codice seguente viene illustrato come utilizzare `RAISERROR` all'interno di un blocco `TRY` per definire il passaggio dell'esecuzione al blocco `CATCH` associato. Viene inoltre illustrato come utilizzare `RAISERROR` per restituire le informazioni sull'errore che ha richiamato il blocco `CATCH`.  
  
> [!NOTE]  
>  RAISERROR genera esclusivamente errori con stato compreso tra 1 e 127. Poiché il [!INCLUDE[ssDE](../../includes/ssde-md.md)] può generare errori con stato 0, è consigliabile verificare lo stato dell'errore restituito da ERROR_STATE prima di passarlo come valore al parametro di stato di RAISERROR.  
  
```  
BEGIN TRY  
    -- RAISERROR with severity 11-19 will cause execution to   
    -- jump to the CATCH block.  
    RAISERROR ('Error raised in TRY block.', -- Message text.  
               16, -- Severity.  
               1 -- State.  
               );  
END TRY  
BEGIN CATCH  
    DECLARE @ErrorMessage NVARCHAR(4000);  
    DECLARE @ErrorSeverity INT;  
    DECLARE @ErrorState INT;  
  
    SELECT   
        @ErrorMessage = ERROR_MESSAGE(),  
        @ErrorSeverity = ERROR_SEVERITY(),  
        @ErrorState = ERROR_STATE();  
  
    -- Use RAISERROR inside the CATCH block to return error  
    -- information about the original error that caused  
    -- execution to jump to the CATCH block.  
    RAISERROR (@ErrorMessage, -- Message text.  
               @ErrorSeverity, -- Severity.  
               @ErrorState -- State.  
               );  
END CATCH;  
```  
  
### <a name="b-creating-an-ad-hoc-message-in-sysmessages"></a>B. Creazione di un messaggio ad hoc in sys.messages  
 Nell'esempio seguente viene illustrato come generare un messaggio archiviato nella vista del catalogo sys. Messages. Il messaggio è stato aggiunto alla vista del catalogo sys. Messages utilizzando il `sp_addmessage` stored procedure di sistema come numero di messaggio `50005`.  
  
```  
sp_addmessage @msgnum = 50005,  
              @severity = 10,  
              @msgtext = N'<\<%7.3s>>';  
GO  
RAISERROR (50005, -- Message id.  
           10, -- Severity,  
           1, -- State,  
           N'abcde'); -- First argument supplies the string.  
-- The message text returned is: <<    abc>>.  
GO  
sp_dropmessage @msgnum = 50005;  
GO  
```  
  
### <a name="c-using-a-local-variable-to-supply-the-message-text"></a>C. Utilizzo di una variabile locale per fornire il testo del messaggio  
 Nell'esempio di codice seguente viene illustrato l'utilizzo di una variabile locale per definire il testo del messaggio per un'istruzione `RAISERROR`.  
  
```  
DECLARE @StringVariable NVARCHAR(50);  
SET @StringVariable = N'<\<%7.3s>>';  
  
RAISERROR (@StringVariable, -- Message text.  
           10, -- Severity,  
           1, -- State,  
           N'abcde'); -- First argument supplies the string.  
-- The message text returned is: <<    abc>>.  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [PRINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/print-transact-sql.md)   
 [sp_addmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [sp_dropmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [xp_logevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-logevent-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40; Transact-SQL &#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)  
  
  

