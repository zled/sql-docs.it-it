---
title: Update () (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPDATE()_TSQL
- UPDATE()
dev_langs:
- TSQL
helpviewer_keywords:
- INSERT statement [SQL Server], UPDATE function
- testing column updates
- UPDATE function
- UPDATE() function
- detecting changes
- columns [SQL Server], change detection
- UPDATE statement [SQL Server], UPDATE function
- verifying column updates
- checking column updates
ms.assetid: 8e3be25b-2e3b-4d1f-a610-dcbbd8d72084
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 644848af581b0db5a26b9958db4660b4cab66163
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="update---trigger-functions-transact-sql"></a>UPDATE - funzioni Trigger (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce un valore booleano che indica se sono stati effettuati tentativi di esecuzione dell'operazione INSERT o UPDATE su una colonna specifica di una tabella o vista. UPDATE() viene utilizzata in qualsiasi punto all'interno del corpo di un trigger [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT o UPDATE per controllare se il trigger deve eseguire operazioni specifiche.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
UPDATE ( column )   
```  
  
## <a name="arguments"></a>Argomenti  
 *colonna*  
 Nome della colonna in cui verificare se viene eseguita un'operazione INSERT o UPDATE. Poiché il nome della tabella viene specificato nella clausola ON del trigger, non includere il nome della tabella prima del nome della colonna. La colonna può essere di qualsiasi [tipo di dati](../../t-sql/data-types/data-types-transact-sql.md) supportati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In questo contesto non è tuttavia possibile utilizzare colonne calcolate.  
  
## <a name="return-types"></a>Tipi restituiti  
 Boolean  
  
## <a name="remarks"></a>Osservazioni  
 UPDATE() restituisce TRUE indipendentemente dall'esito del tentativo di esecuzione dell'operazione INSERT o UPDATE.  
  
 Per testare un'azione di inserimento o aggiornamento per più di una colonna, specificare un aggiornamento separato (*colonna*) dopo la prima clausola. In alternativa, è possibile eseguire la stessa verifica utilizzando COLUMNS_UPDATED. In questo caso viene restituito uno schema di bit che indica le colonne inserite o aggiornate.  
  
 In operazioni INSERT l'opzione IF UPDATE restituisce il valore TRUE in quanto nelle colonne vengono inseriti valori espliciti o impliciti (NULL).  
  
> [!NOTE]  
>  La clausola IF UPDATE (*colonne*n) clausola funziona nello stesso modo, un se se... ELSE o WHILE e può utilizzare il blocco BEGIN... Blocco finale. Per ulteriori informazioni, vedere [del flusso di controllo Language &#40; Transact-SQL &#41; ](~/t-sql/language-elements/control-of-flow.md).  
  
 AGGIORNAMENTO (*colonna*) possono essere utilizzati ovunque all'interno del corpo di un [!INCLUDE[tsql](../../includes/tsql-md.md)] trigger.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creato un trigger che stampa un messaggio nel client in corrispondenza di un tentativo di aggiornamento della la colonna `StateProvinceID` o `PostalCode` della tabella `Address`.  
  
```  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT name FROM sys.objects  
      WHERE name = 'reminder' AND type = 'TR')  
   DROP TRIGGER Person.reminder;  
GO  
CREATE TRIGGER reminder  
ON Person.Address  
AFTER UPDATE   
AS   
IF ( UPDATE (StateProvinceID) OR UPDATE (PostalCode) )  
BEGIN  
RAISERROR (50009, 16, 10)  
END;  
GO  
-- Test the trigger.  
UPDATE Person.Address  
SET PostalCode = 99999  
WHERE PostalCode = '12345';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [COLUMNS_UPDATED &#40; Transact-SQL &#41;](../../t-sql/functions/columns-updated-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)  
  
  

