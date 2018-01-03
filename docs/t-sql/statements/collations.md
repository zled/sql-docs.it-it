---
title: Le regole di confronto | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLLATE
- COLLATE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- collations [SQL Server], COLLATE clause
- COLLATE clause
ms.assetid: 76763ac8-3e0d-4bbb-aa53-f5e7da021daa
caps.latest.revision: "25"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7cc579d5f4c5d84dcec335e69d12334725f60741
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="collations"></a>Regole di confronto
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Clausola che è possibile applicare a una definizione di database o di colonna per definire le regole di confronto oppure a un'espressione stringa di caratteri per applicare il casting delle regole di confronto.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
COLLATE { <collation_name> | database_default }  
<collation_name> :: =   
     { Windows_collation_name } | { SQL_collation_name }  
```  
  
## <a name="arguments"></a>Argomenti  
 *collation_name*  
 Nome delle regole di confronto da applicare all'espressione o alla definizione di colonna o del database. *collation_name* può essere solo un oggetto specificato *Windows_collation_name* o *SQL_collation_name*. *collation_name* deve essere un valore letterale. *collation_name* non può essere rappresentato da una variabile o espressione.  
  
 *Windows_collation_name* è il nome delle regole di confronto per un [windows_collation_name](../../t-sql/statements/windows-collation-name-transact-sql.md).  
  
 *Sql_collation_name* è il nome delle regole di confronto per un [nome regole di confronto di SQL Server](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 In caso di applicazione di regole di confronto al livello di definizione del database, le regole di confronto solo Unicode di Windows non possono essere utilizzate con la clausola COLLATE.  
  
 **database_default**  
 La clausola COLLATE eredita le regole di confronto del database corrente.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile specificare la clausola COLLATE a vari livelli, tra cui:  
  
1.  In fase di creazione o modifica di un database.  
  
     La clausola COLLATE dell'istruzione CREATE DATABASE o ALTER DATABASE consente di specificare le regole di confronto predefinite del database. È inoltre possibile specificare una regola di confronto durante la creazione di un database tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Se non vengono specificate regole di confronto, al database verranno assegnate le regole di confronto predefinite dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  Regole di confronto solo Unicode di Windows sono utilizzabili solo con la clausola COLLATE per applicare le regole di confronto per il **nchar**, **nvarchar**, e **ntext** tipi di dati nel livello di colonna e dati a livello di espressione. non possono essere utilizzate con la clausola COLLATE per modificare le regole di confronto di un'istanza del server o database.  
  
2.  In fase di creazione o modifica di una colonna di tabella.  
  
     È possibile specificare le regole di confronto di ogni colonna contenente stringhe di caratteri tramite la clausola COLLATE dell'istruzione CREATE TABLE o ALTER TABLE. È inoltre possibile specificare una regola di confronto durante la creazione di una tabella tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Se non vengono specificate regole di confronto, alla colonna verranno assegnate le regole di confronto predefinite del database.  
  
     È inoltre possibile utilizzare il `database_default` opzione nella clausola COLLATE per specificare che una colonna in una tabella temporanea utilizza il valore predefinito di regole di confronto del database utente corrente per la connessione anziché **tempdb**.  
  
3.  In fase di casting delle regole di confronto di un'espressione.  
  
     Tramite la clausola COLLATE è possibile applicare un'espressione di caratteri a regole di confronto specifiche. Ai valori letterali e alle variabili di tipo carattere vengono assegnate le regole di confronto predefinite del database corrente. Ai riferimenti di colonna vengono assegnate le regole di confronto di definizione della colonna.  
  
 Le regole di confronto di un identificatore dipendono dal livello nel quale viene definito. Agli identificatori degli oggetti a livello di istanza, quali gli account di accesso e i nomi di database, vengono assegnate le regole di confronto predefinite dell'istanza. Agli identificatori degli oggetti di un database, quali tabelle, viste e nomi di colonna, vengono assegnate le regole di confronto predefinite del database. Ad esempio, due tabelle i cui nomi si differenziano soltanto per l'utilizzo del maiuscolo e del minuscolo possono essere create in un database con regole di confronto in cui l'uso di maiuscole e minuscole è rilevante, ma non in un database con regole di confronto in cui l'uso di maiuscole e minuscole non è rilevante. Per altre informazioni, vedere [Identificatori del database](../../relational-databases/databases/database-identifiers.md).  
  
 È possibile creare variabili, etichette GOTO, stored procedure temporanee e tabelle temporanee se il contesto di connessione è associato a un singolo database, e quindi fare riferimento ad esse quando il contesto passa a un altro database. Gli identificatori di variabili, le etichette GOTO, le stored procedure temporanee e le tabelle temporanee sono inclusi nelle regole di confronto predefinite dell'istanza del server.  
  
 La clausola COLLATE può essere applicata solo per il **char**, **varchar**, **testo**, **nchar**, **nvarchar** , e **ntext** tipi di dati.  
  
 COLLATE utilizza *collate_name* per fare riferimento al nome di regole di confronto di SQL Server o le regole di confronto di Windows da applicare per l'espressione, una definizione di colonna o una definizione di database. *collation_name* può essere solo un oggetto specificato *Windows_collation_name* o *SQL_collation_name* e il parametro deve contenere un valore letterale. *collation_name* non può essere rappresentato da una variabile o espressione.  
  
 Le regole di confronto sono identificate in genere da un nome, ad eccezione che nel programma di installazione. Nel programma di installazione viene invece specificata la designazione delle regole di confronto radice (le impostazioni locali delle regole di confronto) per le regole di confronto di Windows, quindi vengono specificate le opzioni di ordinamento che possono rispettare o meno la distinzione tra maiuscole e minuscole e tra caratteri accentati e non accentati.  
  
 È possibile eseguire la funzione di sistema [fn_helpcollations](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md) per recuperare un elenco di tutti i nomi di regole di confronto valide per le regole di confronto di Windows e le regole di confronto di SQL Server:  
  
```  
SELECT name, description  
FROM fn_helpcollations();  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta solo le tabelle codici supportate dal sistema operativo corrente. Quando si esegue un'azione che dipende dalle regole di confronto, le regole di confronto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzate dall'oggetto a cui si fa riferimento devono utilizzare una tabella codici supportata dal sistema operativo in esecuzione nel computer. Queste azioni includono:  
  
-   Impostazione delle regole di confronto predefinite per un database utilizzate durante la creazione o la modifica del database.  
  
-   Impostazione delle regole di confronto per una colonna utilizzate durante la creazione o la modifica di una tabella.  
  
-   Durante il ripristino o collegamento di un database, le regole di confronto predefinite del database e le regole di confronto di qualsiasi **char**, **varchar**, e **testo** colonne o parametri del database deve essere supportato dal sistema operativo.  
  
     Conversioni di tabella codici sono supportate per **char** e **varchar** tipi di dati, ma non per **testo** tipo di dati. L'eventuale perdita di dati che si verifica durante la conversione tra tabelle codici non viene segnalata.  
  
 Se le regole di confronto specificate o le regole di confronto utilizzate dall'oggetto cui viene fatto riferimento utilizza una tabella codici non supportata da Windows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene visualizzato un errore.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-specifying-collation-during-a-select"></a>A. Specifica delle regole di confronto durante una selezione  
 Nell'esempio seguente viene creata la tabella semplice in cui vengono inserite 4 righe. Quindi vengono applicate due regole di confronto durante la selezione dei dati dalla tabella per dimostrare che `Chiapas` viene ordinato in modo differente.  
  
```sql  
CREATE TABLE Locations  
(Place varchar(15) NOT NULL);  
GO  
INSERT Locations(Place) VALUES ('Chiapas'),('Colima')  
                             , ('Cinco Rios'), ('California');  
GO  
--Apply an typical collation  
SELECT Place FROM Locations  
ORDER BY Place  
COLLATE Latin1_General_CS_AS_KS_WS ASC;  
GO  
-- Apply a Spanish collation  
SELECT Place FROM Locations  
ORDER BY Place  
COLLATE Traditional_Spanish_ci_ai ASC;  
GO  
```  

 Di seguito vengono riportati i risultati dalla prima query.  
  
 ```
 Place 
 ------------- 
 California 
 Chiapas 
 Cinco Rios 
 Colima
 ```  
  
 Di seguito vengono riportati i risultati dalla seconda query.  
  
 ```
 Place 
 ------------- 
 California 
 Cinco Rios 
 Colima 
 Chiapas
 ```  
  
### <a name="b-additional-examples"></a>B. Esempi aggiuntivi  
 Per ulteriori esempi che utilizzano **COLLATE**, vedere [CREATE DATABASE &#40; SQL Server Transact-SQL &#41; ](../../t-sql/statements/create-database-sql-server-transact-sql.md) esempio **g. creazione di un database e specificando un nome di regole di confronto e le opzioni**, e [ALTER TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-transact-sql.md) esempio **v. modifica delle regole di confronto colonna**.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [Regole di confronto e supporto Unicode](../../relational-databases/collations/collation-and-unicode-support.md)   
 [Precedenza delle regole di confronto &#40;Transact-SQL&#41;](../../t-sql/statements/collation-precedence-transact-sql.md)   
 [Costanti &#40; Transact-SQL &#41;](../../t-sql/data-types/constants-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [tabella &#40; Transact-SQL &#41;](../../t-sql/data-types/table-transact-sql.md)  
  
  
