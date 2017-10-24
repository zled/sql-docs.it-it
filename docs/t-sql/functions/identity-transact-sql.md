---
title: '@@IDENTITY (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 08/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@IDENTITY_TSQL'
- '@@IDENTITY'
dev_langs:
- TSQL
helpviewer_keywords:
- last-inserted identity values
- identity values [SQL Server], last-inserted
- '@@IDENTITY function'
ms.assetid: 912e4485-683c-41c2-97b3-8831c0289ee4
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 88cdaa1362e5d60b0f880c66c7fb7038ddb9f126
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="x40x40identity-transact-sql"></a>& #x 40; & #x 40; l'identità (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Funzione di sistema che restituisce l'ultimo valore Identity immesso.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
@@IDENTITY  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **Numeric(38,0)**  
  
## <a name="remarks"></a>Osservazioni  
 Dopo aver INSERT, SELECT INTO o bulk copia istruzione viene completata, @@IDENTITY contiene l'ultimo valore identity generato dall'istruzione. Se l'istruzione non ha influito tutte le tabelle con colonne identity, @@IDENTITY restituisce NULL. Se vengono inserite più righe, la generazione di più valori identity, @@IDENTITY restituisce l'ultimo valore identity generato. Se l'istruzione attiva uno o più trigger per l'esecuzione di inserimenti che generano valori identity, la chiamata@IDENTITY subito dopo l'istruzione restituisce l'ultimo valore identity generato dai trigger. Se un trigger viene attivato dopo un'operazione di inserimento in una tabella che include una colonna identity e il trigger inserisce in un'altra tabella che non dispone di una colonna identity, @@IDENTITY restituisce il valore di identità del primo inserimento. Il @@IDENTITY valore non viene ripristinato un valore precedente, se la copia di istruzione o bulk INSERT o SELECT INTO non riesce o se viene eseguito il rollback della transazione.  
  
 Le istruzioni e le transazioni con esito negativo sono in grado di modificare i dati Identity correnti di una tabella e creare gap nei valori della colonna Identity. Non viene mai eseguito il rollback del valore Identity, anche se non si esegue il commit della transazione che ha tentato l'inserimento del valore nella tabella. Se, ad esempio, un'istruzione INSERT ha esito negativo a causa di una violazione di IGNORE_DUP_KEY, il valore Identity corrente per la tabella viene comunque incrementato.  
  
 @@IDENTITY, SCOPE_IDENTITY e IDENT_CURRENT sono funzioni simili perché restituiscono l'ultimo valore inserito nella colonna IDENTITY di una tabella.  
  
 @@IDENTITY e SCOPE_IDENTITY restituiscono l'ultimo valore identity generato in qualsiasi tabella nella sessione corrente. Tuttavia, la funzione SCOPE_IDENTITY restituisce il valore solo nell'ambito corrente; @@IDENTITY non è limitato a un ambito specifico.  
  
 Per la funzione IDENT_CURRENT non esiste alcuna restrizione di ambito o di sessione. La funzione è limitata tuttavia a una tabella specifica. La funzione IDENT_CURRENT restituisce il valore Identity generato per una tabella specifica in qualsiasi sessione e in qualsiasi ambito. Per ulteriori informazioni, vedere [IDENT_CURRENT &#40; Transact-SQL &#41; ](../../t-sql/functions/ident-current-transact-sql.md).  
  
 L'ambito del @@IDENTITY funzione è la sessione corrente nel server locale in cui viene eseguito. Questa funzione non può essere applicata a server remoti o collegati. Per ottenere un valore Identity in un server diverso, eseguire una stored procedure nel contesto di un server remoto o collegato specifico in modo che recuperi il valore Identity e lo restituisca alla connessione chiamante nel server locale.  
  
 La replica può influire sul @@IDENTITY valore, perché è utilizzata all'interno delle stored procedure e trigger di replica. @@IDENTITY non è un indicatore affidabile dell'identità del più recente creato dall'utente se la colonna fa parte di un articolo di replica. È possibile utilizzare la sintassi della funzione SCOPE_IDENTITY () anziché @@IDENTITY. Per ulteriori informazioni, vedere [SCOPE_IDENTITY &#40; Transact-SQL &#41;](../../t-sql/functions/scope-identity-transact-sql.md)  
  
> [!NOTE]  
>  La stored procedure chiamante o [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione deve essere riscritte per utilizzare il `SCOPE_IDENTITY()` che restituisce l'ultimo valore identity utilizzato nell'ambito di tale istruzione utente e non l'identità nell'ambito del trigger nidificato utilizzato dalla funzione replica.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene inserita una riga in una tabella contenente una colonna Identity (`LocationID`) e viene utilizzata la funzione `@@IDENTITY` per visualizzare il valore Identity nella nuova riga.  
  
```  
USE AdventureWorks2012;  
GO  
--Display the value of LocationID in the last row in the table.  
SELECT MAX(LocationID) FROM Production.Location;  
GO  
INSERT INTO Production.Location (Name, CostRate, Availability, ModifiedDate)  
VALUES ('Damaged Goods', 5, 2.5, GETDATE());  
GO  
SELECT @@IDENTITY AS 'Identity';  
GO  
--Display the value of LocationID of the newly inserted row.  
SELECT MAX(LocationID) FROM Production.Location;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [IDENT_CURRENT &#40;Transact-SQL&#41;](../../t-sql/functions/ident-current-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [SCOPE_IDENTITY &#40; Transact-SQL &#41;](../../t-sql/functions/scope-identity-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
  
  

