---
title: SET SHOWPLAN_XML (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET SHOWPLAN_XML
- SET_SHOWPLAN_XML_TSQL
dev_langs: TSQL
helpviewer_keywords:
- statements [SQL Server], estimates
- SET SHOWPLAN_XML statement
- execution information and estimates [SQL Server]
- statements [SQL Server], information without processing
- XML [SQL Server], statement execution information
- SHOWPLAN_XML option
- estimated execution information [SQL Server]
ms.assetid: a467a1b3-10a5-43c4-9085-13d8aed549c9
caps.latest.revision: "48"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: bd4e6309f65bea4a71cc9e2de7d5bb5b806ab005
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="set-showplanxml-transact-sql"></a>SET SHOWPLAN_XML (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Impedisce l'esecuzione delle istruzioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Microsoft [!INCLUDE[tsql](../../includes/tsql-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce invece informazioni dettagliate sulla modalità di esecuzione delle istruzioni sotto forma di documento XML ben definito.  
 
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET SHOWPLAN_XML { ON | OFF }  
```  
  
## <a name="remarks"></a>Osservazioni  
 L'opzione SET SHOWPLAN_XML viene impostata in fase di esecuzione, non in fase di analisi.  
  
 Quando l'opzione SET SHOWPLAN_XML è impostata su ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce informazioni sul piano di esecuzione per ogni istruzione senza eseguirla, e [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni non vengono eseguite. Quando l'opzione è impostata su ON, vengono restituite informazioni del piano di esecuzione su tutte le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] successive fino a quando l'opzione non viene reimpostata su OFF. Se, ad esempio, si esegue un'istruzione CREATE TABLE quando l'opzione SET SHOWPLAN_XML è impostata su ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un messaggio di errore per una successiva istruzione SELECT che interessa la stessa tabella. La tabella specificata non esiste. I successivi riferimenti a tale tabella pertanto hanno esito negativo. Quando l'opzione SET SHOWPLAN_XML è impostata su OFF, le istruzioni vengono eseguite da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] senza la generazione di alcun report.  
  
 SET SHOWPLAN_XML è progettata per restituire l'output come **nvarchar (max)** per le applicazioni, ad esempio il **sqlcmd** utilità, in cui l'output XML viene successivamente usato da altri strumenti per visualizzare ed elaborare la query informazioni sul piano.  
  
> [!NOTE]  
>  La vista a gestione dinamica **Sys.dm exec_query_plan**, restituisce le stesse informazioni SET SHOWPLAN XML nel **xml** tipo di dati. Queste informazioni vengono restituite dal **query_plan** colonna di **Sys.dm exec_query_plan**. Per ulteriori informazioni, vedere [Sys.dm exec_query_plan &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md).  
  
 Non è possibile specificare SET SHOWPLAN_XML all'interno di una stored procedure. Deve essere l'unica istruzione in un batch.  
  
 SET SHOWPLAN_XML restituisce le informazioni come set di documenti XML. Ogni batch dopo l'istruzione SET SHOWPLAN_XML ON viene restituito nell'output da un unico documento. Ogni documento contiene il testo delle istruzioni nel batch, seguito dai dettagli dei passaggi dell'esecuzione. Nel documento vengono illustrati i costi stimati, il numero di righe, gli indici utilizzati e i tipi di operatori eseguiti, l'ordine di join e ulteriori informazioni sui piani di esecuzione.  
  
 Il documento contenente l'XML Schema per l'output XML di SET SHOWPLAN_XML viene copiato durante l'installazione in una directory locale nel computer in cui è installato Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si trova nell'unità contenente i file di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], nel percorso seguente:  
  
 \Microsoft SQL Server\130\Tools\Binn\schemas\sqlserver\2004\07\showplan\showplanxml.xsd  
  
 Lo Showplan Schema è inoltre reperibile in [questo sito Web](http://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409).  
  
> [!NOTE]  
>  Se **Includi piano di esecuzione effettivo** è selezionata [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], questa opzione SET non produce un output di Showplan XML. Cancella il **Includi piano di esecuzione effettivo** pulsante prima di utilizzare l'opzione SET.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per poter utilizzare SET SHOWPLAN_XML, è necessario disporre delle autorizzazioni sufficienti per eseguire le istruzioni in cui SET SHOWPLAN_XM viene eseguito, nonché l'autorizzazione SHOWPLAN per tutti i database contenenti oggetti di riferimento.  
  
 Per SELECT, INSERT, UPDATE, DELETE, EXEC *stored_procedure*, EXEC e *user_defined_function* istruzioni, per produrre uno Showplan in cui l'utente deve:  
  
-   Autorizzazioni appropriate per l'esecuzione delle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Autorizzazione SHOWPLAN su tutti i database contenenti oggetti a cui fanno riferimento le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)], ad esempio tabelle, viste e così via.  
  
 Per tutte le altre istruzioni, ad esempio DDL, USE *database_name*, SET, DECLARE, SQL, dinamico e così via, solo le autorizzazioni appropriate per eseguire il [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni sono necessarie.  
  
## <a name="examples"></a>Esempi  
 Nelle due istruzioni seguenti vengono utilizzate le impostazioni dell'opzione SET SHOWPLAN_XML per illustrare l'analisi e l'ottimizzazione dell'utilizzo degli indici nelle query in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La prima query utilizza l'operatore di confronto uguale a (=) nella clausola WHERE in una colonna indicizzata. La seconda query utilizza l'operatore LIKE nella clausola WHERE. In tal modo viene imposta l'esecuzione di un'analisi di indice cluster in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per individuare i dati che soddisfano la condizione della clausola WHERE. I valori nel **EstimateRows** e **EstimatedTotalSubtreeCost** gli attributi sono inferiori per la prima query indicizzata, che indica che viene elaborato molto più rapidamente e utilizzerebbe meno risorse rispetto al query non indicizzata.  
  
```  
USE AdventureWorks2012;  
GO  
SET SHOWPLAN_XML ON;  
GO  
-- First query.  
SELECT BusinessEntityID   
FROM HumanResources.Employee  
WHERE NationalIDNumber = '509647174';  
GO  
-- Second query.  
SELECT BusinessEntityID, JobTitle  
FROM HumanResources.Employee  
WHERE JobTitle LIKE 'Production%';  
GO  
SET SHOWPLAN_XML OFF;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
