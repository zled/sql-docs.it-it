---
title: Transazioni (SQL Data Warehouse) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 87e5e593-a121-4428-9d3c-3af876224e35
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8202a0de588bce3a36fc048e68c283b52db7e89d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="transactions-sql-data-warehouse"></a>Transazioni (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Una transazione è un gruppo di uno o più istruzioni di database che sono interamente eseguito il commit o rollback interamente. Ogni transazione è atomico, coerente, isolato e durevole (ACID). Se la transazione ha esito positivo, tutte le istruzioni all'interno di esso vengono eseguito il commit. Se la transazione ha esito negativo, che è almeno una delle istruzioni del gruppo non riesce, viene eseguito il rollback dell'intero gruppo.  
  
 Inizio e alla fine delle transazioni varia a seconda dell'impostazione di AUTOCOMMIT e le istruzioni BEGIN TRANSACTION, COMMIT e ROLLBACK. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]supporta i seguenti tipi di transazioni:  
  
-   *Le transazioni esplicite* iniziano con l'istruzione BEGIN TRANSACTION e la fine con l'istruzione COMMIT o ROLLBACK.  
  
-   *Le transazioni autocommit* avviare automaticamente all'interno di una sessione e non iniziano con l'istruzione BEGIN TRANSACTION. Quando l'impostazione della modalità AUTOCOMMIT è impostata su ON, ogni istruzione viene eseguita in una transazione e non esplicito COMMIT o ROLLBACK è necessario. Quando l'impostazione della modalità AUTOCOMMIT è impostata su OFF, un'istruzione COMMIT o ROLLBACK è necessario per determinare il risultato della transazione. In [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], le transazioni con autocommit iniziano immediatamente dopo un'istruzione COMMIT o ROLLBACK oppure dopo un'istruzione SET AUTOCOMMIT OFF.  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
BEGIN TRANSACTION [;]  
COMMIT [ TRAN | TRANSACTION | WORK ] [;]  
ROLLBACK [ TRAN | TRANSACTION | WORK ] [;]  
SET AUTOCOMMIT { ON | OFF } [;]  
SET IMPLICIT_TRANSACTIONS { ON | OFF } [;]  
```  
  
## <a name="arguments"></a>Argomenti  
 BEGIN TRANSACTION  
 Contrassegna il punto iniziale di una transazione esplicita.  
  
 COMMIT [WORK]  
 Contrassegna la fine di una transazione esplicita o autocommit. Questa istruzione comporta le modifiche apportate nella transazione sottoposte a commit in modo permanente nel database. L'istruzione COMMIT è identico al COMMIT WORK, COMMIT TRAN e COMMIT TRANSACTION.  
  
 RIPRISTINO [WORK]  
 Esegue il rollback di una transazione all'inizio della transazione. Nessuna modifica per la transazione viene eseguito il commit nel database. L'istruzione ROLLBACK è identico al ROLLBACK WORK, ROLLBACK TRAN e ROLLBACK TRANSACTION.  
  
 AUTOCOMMIT SET { **ON** | OFF}  
 Determina come le transazioni possono iniziare e terminare.  
  
 ON  
 Ogni istruzione viene eseguito con la propria transazione e nessuna istruzione esplicita COMMIT o ROLLBACK è necessaria. Le transazioni esplicite sono consentite quando la proprietà modalità AUTOCOMMIT è impostata su ON.  
  
 OFF  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Avvia automaticamente una transazione quando una transazione non è già in corso. Tutte le istruzioni successive vengono eseguite come parte della transazione e un'istruzione COMMIT o ROLLBACK è necessario determinare il risultato della transazione. Non appena viene eseguito il commit o rollback in questa modalità operativa di una transazione, la modalità rimane impostata su OFF, e [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] avvia una nuova transazione. Le transazioni esplicite non sono consentite quando la proprietà modalità AUTOCOMMIT è impostata su OFF.  
  
 Se si modifica l'impostazione di AUTOCOMMIT all'interno di una transazione attiva, l'impostazione influisce sulla transazione corrente e non ha effetto fino al completamento della transazione.  
  
 Se AUTOCOMMIT è impostata su ON, in esecuzione un'altra istruzione SET AUTOCOMMIT ON non ha alcun effetto. Analogamente, se AUTOCOMMIT è impostata su OFF, in esecuzione un altro SET AUTOCOMMIT OFF non ha effetto.  
  
 SET IMPLICIT_TRANSACTIONS {ON | **OFF** }  
 Attiva e disattiva la modalità stesso come impostare AUTOCOMMIT. Quando è impostata su ON, l'opzione SET IMPLICIT_TRANSACTIONS imposta per la connessione la modalità di transazione implicita. Quando impostata su OFF, viene ripristinata la connessione in modalità autocommit.  Per ulteriori informazioni, vedere [SET IMPLICIT_TRANSACTIONS &#40; Transact-SQL &#41; ](../../t-sql/statements/set-implicit-transactions-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Sono richieste autorizzazioni specifiche per eseguire le istruzioni relative alle transazioni. Sono necessarie autorizzazioni per eseguire le istruzioni all'interno della transazione.  
  
## <a name="error-handling"></a>Gestione degli errori  
 Se vengono eseguiti COMMIT o ROLLBACK ed è presente alcuna transazione attiva, viene generato un errore.  
  
 Se un'istruzione BEGIN TRANSACTION viene eseguita quando è già in corso una transazione, viene generato un errore. Ciò può verificarsi se si verifica un'istruzione BEGIN TRANSACTION dopo un'istruzione BEGIN TRANSACTION ha esito positivo o quando la sessione è in modalità AUTOCOMMIT SET OFF.  
  
 Se un errore diverso da un errore in fase di esecuzione istruzione impedisce il completamento di una transazione esplicita, [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] automaticamente il rollback della transazione e libera tutte le risorse utilizzate dalla transazione. Ad esempio, se la connessione di rete del client a un'istanza di [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] viene interrotta o il client si disconnette l'applicazione, vengono eseguito il rollback di tutte le transazioni non salvate per la connessione quando la rete notifica l'istanza dell'interruzione.  
  
 Se si verifica un errore in fase di esecuzione istruzione in un batch, [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] comportamento è coerente con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **XACT_ABORT** impostato su **ON** e viene eseguito il rollback dell'intera transazione. Per ulteriori informazioni sul **XACT_ABORT** impostazione, vedere [SET XACT_ABORT (Transact-SQL)](http://msdn.microsoft.com/library/ms188792.aspx).  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Una sessione può eseguire solo una transazione in un determinato momento; punti di salvataggio e transazioni annidate non sono supportate.  
  
 È responsabilità del [!INCLUDE[DWsql](../../includes/dwsql-md.md)] programmatore eseguire il COMMIT solo in un punto quando tutti i dati a cui fa riferimento la transazione è logicamente corretto.  
  
 Quando una sessione è terminata prima che venga completata una transazione, viene eseguito il rollback della transazione.  
  
 Modalità di transazione vengono gestite a livello di sessione. Ad esempio, se una sessione inizia una transazione esplicita o imposta l'AUTOCOMMIT su OFF o imposta l'opzione IMPLICIT_TRANSACTIONS su ON, non ha alcun effetto sulle modalità di transazione da qualsiasi altra sessione.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 È Impossibile rollback della transazione dopo il rilascio di un'istruzione COMMIT perché le modifiche dei dati sono state apportate a una parte permanente del database.  
  
 Il [crea DATABASE &#40; Azure SQL Data Warehouse &#41; ](../../t-sql/statements/create-database-azure-sql-data-warehouse.md) e [DROP DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/drop-database-transact-sql.md) comandi non possono essere utilizzati all'interno di una transazione esplicita.  
  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]non dispone di una transazione meccanismo di condivisione. Ciò implica che a un certo punto nel tempo, solo una sessione può eseguire le operazioni in qualsiasi transazione nel sistema.  
  
## <a name="locking-behavior"></a>Comportamento di blocco  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]utilizza il blocco per garantire l'integrità delle transazioni e mantenere la coerenza dei database quando più utenti accedono ai dati nello stesso momento. Il blocco viene utilizzato dalle transazioni sia implicite che esplicite. Ogni transazione richiede blocchi di diversi tipi sulle risorse, ad esempio tabelle o database da cui dipende la transazione. Tutti [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] i blocchi sono tabella o a un livello superiore. I blocchi impediscono alle altre transazioni di modificare le risorse in modo tale da creare problemi alla transazione che richiede il blocco. Ogni transazione libera i relativi blocchi quando non sia più associata una dipendenza dalle risorse bloccate; le transazioni esplicite mantengono blocchi finché la transazione viene completata quando viene eseguito il commit o rollback.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-using-an-explicit-transaction"></a>A. Utilizzo di una transazione esplicita  
  
```  
BEGIN TRANSACTION;  
DELETE FROM HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
COMMIT;  
```  
  
### <a name="b-rolling-back-a-transaction"></a>B. Eseguire il rollback di una transazione  
 Nell'esempio seguente viene illustrato l'effetto del rollback di una transazione.  In questo esempio, l'istruzione ROLLBACK viene eseguito il rollback dell'istruzione INSERT, ma sarà ancora presente nella tabella creata.  
  
```  
CREATE TABLE ValueTable (id int);  
BEGIN TRANSACTION;  
       INSERT INTO ValueTable VALUES(1);  
       INSERT INTO ValueTable VALUES(2);  
ROLLBACK;  
```  
  
### <a name="c-setting-autocommit"></a>C. Impostazione modalità AUTOCOMMIT  
 Nell'esempio seguente imposta l'impostazione di AUTOCOMMIT `ON`.  
  
```  
SET AUTOCOMMIT ON;  
```  
  
 Nell'esempio seguente imposta l'impostazione di AUTOCOMMIT `OFF`.  
  
```  
SET AUTOCOMMIT OFF;  
```  
  
### <a name="d-using-an-implicit-multi-statement-transaction"></a>D. Utilizzo di una transazione implicita di multi-istruzione  
  
```  
SET AUTOCOMMIT OFF;  
CREATE TABLE ValueTable (id int);  
INSERT INTO ValueTable VALUES(1);  
INSERT INTO ValueTable VALUES(2);  
COMMIT;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SET IMPLICIT_TRANSACTIONS &#40; Transact-SQL &#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [SET TRANSACTION ISOLATION LEVEL &#40; Transact-SQL &#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  

