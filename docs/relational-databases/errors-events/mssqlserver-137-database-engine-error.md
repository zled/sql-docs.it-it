---
title: MSSQLSERVER_137 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 137 (Database Engine error)
ms.assetid: 47fb4212-2165-4fec-bc41-6d548465d7be
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6d581cb6eeeb0965143b4830f90c0c537d4db7db
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver137"></a>MSSQLSERVER_137
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|137|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|P_SCALAR_VAR_NOTFOUND|  
|Testo del messaggio|Dichiarare la variabile scalare "%.*ls".|  
  
## <a name="explanation"></a>Spiegazione  
Questo errore si verifica quando una variabile viene utilizzata in uno script SQL senza essere stata dichiarata in precedenza. Nell'esempio seguente viene restituito l'errore 137 per entrambe le istruzioni SET e SELECT poiché non è stata dichiarata la variabile **@mycol**.  
  
SET @mycol = 'ContactName';  
  
SELECT @mycol;  
  
Una delle cause più complesse di questo errore include l'utilizzo di una variabile dichiarata al di fuori dell'istruzione EXECUTE. La variabile **@mycol** specificata nell'istruzione SELECT, ad esempio, è locale per l'istruzione SELECT, ma è esterna all'istruzione EXECUTE.  
  
USE AdventureWorks2012;  
  
GO  
  
DECLARE @mycol nvarchar(20);  
  
SET @mycol = 'Name';  
  
EXECUTE ('SELECT @mycol FROM Production.Product;');  
  
## <a name="user-action"></a>Azione dell'utente  
Verificare che qualsiasi variabile utilizzata in uno script SQL venga dichiarata prima di essere utilizzata.  
  
Riscrivere lo script in modo che non faccia riferimento a variabili nell'istruzione EXECUTE dichiarate al di fuori dell'istruzione stessa. Ad esempio  
  
USE AdventureWorks2012;  
  
GO  
  
DECLARE @mycol nvarchar(20) ;  
  
SET @mycol = 'Name';  
  
EXECUTE ('SELECT ' + @mycol + ' FROM Production.Product';) ;  
  
## <a name="see-also"></a>Vedere anche  
[EXECUTE &#40;Transact-SQL&#41;](~/t-sql/language-elements/execute-transact-sql.md)  
[Istruzioni SET &#40;Transact-SQL&#41;](~/t-sql/statements/set-statements-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](~/t-sql/language-elements/declare-local-variable-transact-sql.md)  
  
