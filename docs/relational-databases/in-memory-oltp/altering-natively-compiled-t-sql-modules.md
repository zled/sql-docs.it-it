---
title: Altering Natively Compiled T-SQL Modules (Modifica dei moduli T-SQL compilati in modo nativo) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 010318a0-6807-47c3-8ecc-bb7cb60513f0
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4696039c56ebf5f1fd6ea440cd27da84721f35b9
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="altering-natively-compiled-t-sql-modules"></a>Altering Natively Compiled T-SQL Modules
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  In [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] e versioni successive e nel [!INCLUDE[ssSDS](../../includes/sssds-md.md)] è possibile eseguire operazioni ALTER in stored procedure compilate in modo nativo e in altri moduli T-SQL compilati in modo nativo, ad esempio UDF scalari e trigger, con l'istruzione ALTER.  
  
 Quando si esegue ALTER in un modulo T-SQL compilato in modo nativo, il modulo viene ricompilato con una nuova definizione. Durante la ricompilazione la versione precedente del modulo continua a essere disponibile per l'esecuzione. Una volta completata la compilazione, le esecuzioni dei moduli vengono svuotate e viene installata la nuova versione del modulo. Quando si modifica un modulo T-SQL compilato in modo nativo, è possibile modificare le opzioni seguenti.  
  
-   Parametri  
  
-   EXECUTE AS  
  
-   TRANSACTION ISOLATION LEVEL  
  
-   LANGUAGE  
  
-   DATEFIRST  
  
-   DATEFORMAT  
  
-   DELAYED_DURABILITY  
  
> [!NOTE]  
>  I moduli T-SQL compilati in modo nativo non possono essere convertiti in moduli compilati in modo non nativo. I moduli T-SQL compilati in modo non nativo non possono essere convertiti in moduli compilati in modo nativo.  
  
 Per altre informazioni sul funzionamento e la sintassi di ALTER PROCEDURE, vedere [ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md)  
  
 È possibile eseguire sp_recompile in moduli T-SQL compilati in modo nativo. Ciò causa la ricompilazione del modulo all'esecuzione successiva.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente crea una tabella con ottimizzazione per la memoria (T1) e una stored procedure compilata in modo nativo (SP1) che seleziona tutte le colonne T1. Quindi, SP1 viene modificata per rimuovere la clausola EXECUTE AS, modificare LANGUAGE e selezionare una sola colonna (C1) da T1.  
  
```  
CREATE TABLE [dbo].[T1]  
(  
[c1] [int] NOT NULL,  
[c2] [float] NOT NULL,  
CONSTRAINT [PK_T1] PRIMARY KEY NONCLUSTERED ([c1])  
)WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
CREATE PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english'  
)  
 SELECT c1, c2 from dbo.T1  
END  
GO  
  
ALTER PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'Dutch'  
)  
 SELECT c1 from dbo.T1  
END  
GO  
  
```  
  
  
