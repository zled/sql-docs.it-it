---
title: Istruzioni SET (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET
- SET_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ISO SET statements
- queries [SQL Server], executing
- dates [SQL Server], SET statements
- time [SQL Server], SET statements
- SET statement, about SET statement
- SET statement
- statistical information [SQL Server], SET statements
- locking [SQL Server], SET statements
ms.assetid: f7e107f8-0fcf-408b-b30f-da2323eeb714
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f0426730b33f0b70fda11a8cb07242a365d10fae
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-statements-transact-sql"></a>Istruzioni SET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il linguaggio di programmazione [!INCLUDE[tsql](../../includes/tsql-md.md)] offre varie istruzioni SET per la modifica della gestione delle informazioni specifiche della sessione corrente. Le istruzioni SET sono raggruppate in categorie, descritte nella tabella seguente.  
  
 Per informazioni sull'impostazione delle variabili locali mediante l'istruzione SET, vedere [impostare @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/set-local-variable-transact-sql.md).  
  
|Category|Istruzioni|  
|--------------|----------------|  
|Istruzioni relative a data e ora|[SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md)<br /><br /> [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md)|  
|Istruzioni di blocco|[SET DEADLOCK_PRIORITY](../../t-sql/statements/set-deadlock-priority-transact-sql.md)<br /><br /> [SET LOCK_TIMEOUT](../../t-sql/statements/set-lock-timeout-transact-sql.md)|  
|Istruzioni varie|[SET CONCAT_NULL_YIELDS_NULL](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md)<br /><br /> [SET CURSOR_CLOSE_ON_COMMIT](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md)<br /><br /> [SET FIPS_FLAGGER](../../t-sql/statements/set-fips-flagger-transact-sql.md)<br /><br /> [SET IDENTITY_INSERT](../../t-sql/statements/set-identity-insert-transact-sql.md)<br /><br /> [IMPOSTAZIONE DELLA LINGUA](../../t-sql/statements/set-language-transact-sql.md)<br /><br /> [OFFSET SET](../../t-sql/statements/set-offsets-transact-sql.md)<br /><br /> [SET QUOTED_IDENTIFIER](../../t-sql/statements/set-quoted-identifier-transact-sql.md)|  
|Istruzioni per l'esecuzione di query|[SET ARITHABORT](../../t-sql/statements/set-arithabort-transact-sql.md)<br /><br /> [SET ARITHIGNORE](../../t-sql/statements/set-arithignore-transact-sql.md)<br /><br /> [SET FMTONLY](../../t-sql/statements/set-fmtonly-transact-sql.md)<br /><br /> Nota:[!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<br /><br /> [SET NOCOUNT](../../t-sql/statements/set-nocount-transact-sql.md)<br /><br /> [SET NOEXEC](../../t-sql/statements/set-noexec-transact-sql.md)<br /><br /> [SET NUMERIC_ROUNDABORT](../../t-sql/statements/set-numeric-roundabort-transact-sql.md)<br /><br /> [SET PARSEONLY](../../t-sql/statements/set-parseonly-transact-sql.md)<br /><br /> [SET QUERY_GOVERNOR_COST_LIMIT](../../t-sql/statements/set-query-governor-cost-limit-transact-sql.md)<br /><br /> [SET ROWCOUNT](../../t-sql/statements/set-rowcount-transact-sql.md)<br /><br /> [SET TEXTSIZE](../../t-sql/statements/set-textsize-transact-sql.md)|  
|Istruzioni per impostazioni ISO|[SET ANSI_DEFAULTS](../../t-sql/statements/set-ansi-defaults-transact-sql.md)<br /><br /> [SET ANSI_NULL_DFLT_OFF](../../t-sql/statements/set-ansi-null-dflt-off-transact-sql.md)<br /><br /> [SET ANSI_NULL_DFLT_ON](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)<br /><br /> [SET ANSI_NULLS](../../t-sql/statements/set-ansi-nulls-transact-sql.md)<br /><br /> [SET ANSI_PADDING](../../t-sql/statements/set-ansi-padding-transact-sql.md)<br /><br /> [SET ANSI_WARNINGS](../../t-sql/statements/set-ansi-warnings-transact-sql.md)|  
|Istruzioni statistiche|[SET FORCEPLAN](../../t-sql/statements/set-forceplan-transact-sql.md)<br /><br /> [SET SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md)<br /><br /> [SET SHOWPLAN_TEXT](../../t-sql/statements/set-showplan-text-transact-sql.md)<br /><br /> [SET SHOWPLAN_XML](../../t-sql/statements/set-showplan-xml-transact-sql.md)<br /><br /> [SET STATISTICS IO](../../t-sql/statements/set-statistics-io-transact-sql.md)<br /><br /> [SET STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md)<br /><br /> [SET STATISTICS PROFILE](../../t-sql/statements/set-statistics-profile-transact-sql.md)<br /><br /> [SET STATISTICS TIME](../../t-sql/statements/set-statistics-time-transact-sql.md)|  
|Istruzioni per transazioni|[SET IMPLICIT_TRANSACTIONS](../../t-sql/statements/set-implicit-transactions-transact-sql.md)<br /><br /> [SET REMOTE_PROC_TRANSACTIONS](../../t-sql/statements/set-remote-proc-transactions-transact-sql.md)<br /><br /> [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)<br /><br /> [SET XACT_ABORT IMPOSTATA SU](../../t-sql/statements/set-xact-abort-transact-sql.md)|  
  
## <a name="considerations-when-you-use-the-set-statements"></a>Considerazioni sull'utilizzo delle istruzioni SET  
  
-   Tutte le istruzioni SET vengono implementate in fase di esecuzione, ad eccezione di SET FIPS_FLAGGER, SET OFFSETS, SET PARSEONLY e SET QUOTED_IDENTIFIER, che vengono implementate in fase di analisi.  
  
-   Se un'istruzione SET viene eseguita in una stored procedure o in un trigger, il valore dell'opzione SET viene ripristinato al termine della stored procedure o del trigger. Inoltre, se un'istruzione SET viene specificata in una stringa SQL dinamica che viene eseguita utilizzando **sp_executesql** o EXECUTE, il valore dell'opzione SET viene ripristinato al termine del batch specificato nella stringa SQL dinamica.  
  
-   Le stored procedure vengono eseguite con le impostazioni SET specificate in fase di esecuzione, ad eccezione di SET ANSI_NULLS e SET QUOTED_IDENTIFIER. Le stored procedure che specificano SET ANSI_NULLS o SET QUOTED_IDENTIFIER utilizzano l'impostazione specificata in fase di creazione della stored procedure. Se utilizzate all'interno di una stored procedure, le impostazioni SET vengono ignorate.  
  
-   Il **opzioni utente** l'impostazione di **sp_configure** consente per le impostazioni a livello di server e funziona tra più database. Questa impostazione si comporta, inoltre, come un'istruzione SET esplicita, con la sola differenza che viene applicata al momento dell'accesso.  
  
-   Le impostazioni di database impostate tramite ALTER DATABASE sono valide solo a livello di database e hanno effetto solo se impostate in modo esplicito. Le impostazioni del database eseguire l'override delle impostazioni delle opzioni di istanza che vengono impostate utilizzando **sp_configure**.  
  
-   Per qualsiasi istruzione SET con le impostazioni ON e OFF è possibile specificare un'impostazione ON o OFF per più opzioni SET.  
  
    > [!NOTE]  
    >  Ciò non vale per le opzioni SET correlate alle statistiche.  
  
     Ad esempio, `SET QUOTED_IDENTIFIER, ANSI_NULLS ON` imposta sia QUOTED_IDENTIFIER che ANSI_NULLS su ON.  
  
-   Le impostazioni delle istruzioni SET prevalgono sulle equivalenti impostazioni delle opzioni di database che vengono impostate utilizzando ALTER DATABASE. Il valore specificato in un'istruzione SET ANSI_NULLS, ad esempio, prevarrà sull'impostazione di database per ANSI_NULLS. Inoltre, alcune impostazioni di connessione vengono automaticamente impostati su quando un utente si connette a un database in base ai valori realizzano mediante il precedente il **opzioni utente sp_configure** impostazione o i valori che si applicano a tutti di ODBC e Connessioni OLE DB.  
  
-   Le istruzioni ALTER, CREATE e DROP DATABASE non rispettano l'impostazione di SET LOCK_TIMEOUT.  
  
-   Quando un'istruzione SET globale o abbreviata, ad esempio SET ANSI_DEFAULTS, include più impostazioni, l'esecuzione dell'istruzione SET abbreviata ripristina le impostazioni precedenti per tutte le opzioni su cui ha effetto tale istruzione SET. Se una singola opzione SET su cui ha effetto un'istruzione SET abbreviata viene impostata in modo esplicito dopo l'esecuzione dell'istruzione SET abbreviata, la singola istruzione SET prevale sulle corrispondenti impostazioni dell'istruzione abbreviata.  
  
-   Quando si utilizzano batch, il contesto del database è determinato dal batch definito con l'istruzione USE. Le query ad hoc e tutte le altre istruzioni che vengono eseguite all'esterno della stored procedure e che sono incluse in batch ereditano le impostazioni delle opzioni del database e della connessione definiti con l'istruzione USE.  
  
-   Le richieste MARS (Multiple Active Result Set) condividono uno stato globale che contiene le impostazioni delle opzioni SET della sessione più recente. Quando viene eseguita, ogni richiesta può modificare le opzioni SET. Le modifiche sono specifiche del contesto della richiesta in cui sono impostato e non hanno alcun effetto sulle altre richieste MARS contemporanee. Al termine dell'esecuzione della richiesta, tuttavia, le nuove opzioni SET vengono copiate nello stato della sessione globale. Le nuove richieste che vengono eseguite nella stessa sessione dopo questa modifica utilizzeranno queste nuove impostazioni delle opzioni SET.  
  
-   Una stored procedure eseguita da un batch o da un'altra stored procedure viene eseguita in base ai valori delle opzione impostate nel database che contiene la stored procedure. Ad esempio, quando stored procedure **db1.dbo.sp1** chiama stored procedure **db2.dbo.sp2**, stored procedure di **sp1** viene eseguita nel livello di compatibilità corrente impostazione del database **db1**e la stored procedure **sp2** viene eseguito con l'impostazione corrente del livello di compatibilità del database **db2**.  
  
-   Quando un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] fa riferimento a oggetti che si trovano in più database, a tale istruzione si applicano il contesto del database corrente e il contesto della connessione corrente. In questo caso, se l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] si trova in un batch, il contesto della connessione corrente è il database definito dall'istruzione USE. Se l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] si trova in una stored procedure, il contesto della connessione è il database che contiene la stored procedure.  
  
-   Quando si creano e modificano indici in colonne calcolate o viste indicizzate, le opzioni SET ARITHABORT, CONCAT_NULL_YIELDS_NULL, QUOTED_IDENTIFIER, ANSI_NULLS, ANSI_PADDING e ANSI_WARNINGS devono essere impostate su ON. L'opzione NUMERIC_ROUNDABORT deve essere impostata su OFF.  
  
     Se per una di queste opzioni non vengono impostati i valori richiesti, non sarà possibile eseguire in modo corretto le azioni INSERT, UPDATE, DELETE, DBCC CHECKDB e DBCC CHECKTABLE nelle viste indicizzate o nelle tabelle con indici nelle colonne calcolate. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verrà generato un avviso contenente tutte le opzioni impostate in modo errato. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] elaborerà, inoltre, le istruzioni SELECT in tali tabelle o viste indicizzate come se gli indici nelle colonne calcolate o nelle viste non esistessero.  
  
  
