---
title: Barra asterisco (blocco di commento) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|language-elements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- /*...*/_TSQL
- Comment
- /*...*/
dev_langs:
- TSQL
helpviewer_keywords:
- nonexecuting text strings [SQL Server]
- /*...*/ (comment)
- remarks [SQL Server]
- comments [SQL Server]
ms.assetid: 4d9ab1b2-4bbb-4c16-beb1-cafc1af7417c
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: db614b063ac6b5f92da2f3af53d61ef10755b1d8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="slash-star-block-comment-transact-sql"></a>Barra asterisco (blocco di commento) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]


  Evidenzia il testo inserito dall'utente. Il testo compreso tra /* e \*/ non viene valutato dal server.  
  
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
  
## <a name="remarks"></a>Remarks  
 I commenti possono essere inseriti in una riga distinta o all'interno di un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)]. I commenti su più righe devono essere contrassegnati da /* e \*/. Una convenzione usata spesso per i commenti su più righe consiste nell'iniziare la prima riga di commento con /\* e le righe successive con \*\* e nel terminare quindi il commento con \*/.  
  
 I commenti possono essere di qualsiasi lunghezza.  
  
 Non sono supportati i commenti nidificati. L'eventuale modello di caratteri /* presente in un punto qualsiasi all'interno di un commento esistente viene considerato l'inizio di un commento nidificato e pertanto dovrà essere contrassegnato con il carattere \*/ di chiusura. Se il carattere di chiusura del commento non è presente, viene generato un errore.  
  
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
 [-- &#40;commento&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/comment-transact-sql.md)   
 [Elementi del linguaggio per il controllo di flusso &#40;Transact-SQL&#41;](~/t-sql/language-elements/control-of-flow.md)  
  
  

