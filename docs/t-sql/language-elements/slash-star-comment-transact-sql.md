---
title: Barre a stella (blocco di commento) (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- /*...*/_TSQL
- Comment
- /*...*/
dev_langs: TSQL
helpviewer_keywords:
- nonexecuting text strings [SQL Server]
- /*...*/ (comment)
- remarks [SQL Server]
- comments [SQL Server]
ms.assetid: 4d9ab1b2-4bbb-4c16-beb1-cafc1af7417c
caps.latest.revision: "30"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 60ae52af725a065a8319a2fde1e87e1b8bb52e02
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="slash-star-block-comment-transact-sql"></a>Barre a stella (blocco di commento) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]


  Evidenzia il testo inserito dall'utente. Il testo compreso tra il / * e \*/ non viene valutato dal server.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
/*  
text_of_comment  
*/  
```  
  
## <a name="arguments"></a>Argomenti  
 *text_of_comment*  
 Testo del commento. Può essere composto da una o più stringhe di caratteri.  
  
## <a name="remarks"></a>Osservazioni  
 I commenti possono essere inseriti in una riga distinta o all'interno di un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)]. Commenti su più righe devono essere contrassegnati da / * e \*/. È una convenzione utilizzata spesso per commenti su più righe per iniziare la prima riga con /\*, le successive righe con \* \*e terminare con \*/.  
  
 I commenti possono essere di qualsiasi lunghezza.  
  
 Non sono supportati i commenti nidificati. Se il / * modello caratteri si verifica in un punto qualsiasi all'interno di un commento esistente, viene considerato l'inizio di un commento nidificato e, pertanto, richiede una chiusura \*/ indicatore di commento. Se il carattere di chiusura del commento non è presente, viene generato un errore.  
  
 Il codice di esempio seguente genera un errore.  
  
```  
DECLARE @comment AS varchar(20);  
GO  
/*  
SELECT @comment = '/*';  
*/   
SELECT @@VERSION;  
GO   
```  
  
 Per risolvere il problema, apportare la modifica seguente.  
  
```  
DECLARE @comment AS varchar(20);  
GO  
/*  
SELECT @comment = '/*';  
*/ */  
SELECT @@VERSION;  
GO  
  
```  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono utilizzati i commenti per descrivere la funzionalità della sezione di codice.  
  
```  
USE AdventureWorks2012;  
GO  
/*  
This section of the code joins the Person table with the Address table,   
by using the Employee and BusinessEntityAddress tables in the middle to   
get a list of all the employees in the AdventureWorks2012 database   
and their contact information.  
*/  
SELECT p.FirstName, p.LastName, a.AddressLine1, a.AddressLine2, a.City, a.PostalCode  
FROM Person.Person AS p  
JOIN HumanResources.Employee AS e ON p.BusinessEntityID = e.BusinessEntityID   
JOIN Person.BusinessEntityAddress AS ea ON e.BusinessEntityID = ea.BusinessEntityID  
JOIN Person.Address AS a ON ea.AddressID = a.AddressID;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [-&#40; Commento &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/comment-transact-sql.md)   
 [Il controllo di flusso Language &#40; Transact-SQL &#41;](~/t-sql/language-elements/control-of-flow.md)  
  
  

