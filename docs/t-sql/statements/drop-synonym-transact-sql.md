---
title: DROP SYNONYM (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SYNONYM
- DROP_SYNONYM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting synonyms
- synonyms [SQL Server], removing
- removing synonyms
- DROP SYNONYM statement
- dropping synonyms
ms.assetid: 23578932-e4de-4c39-a5a0-ce45139c4269
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 25af262ddc5655bc42e4893daecefe0cd8fb85d9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="drop-synonym-transact-sql"></a>DROP SYNONYM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Rimuove un sinonimo da uno schema specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP SYNONYM [ IF EXISTS ] [ schema. ] synonym_name  
```  
  
## <a name="arguments"></a>Argomenti  
 *SE ESISTE*  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [versione](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 Elimina in modo condizionale il sinonimo solo se esiste già.  
  
 *schema*  
 Specifica lo schema in cui è contenuto il sinonimo. Se lo schema viene omesso, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizza lo schema predefinito dell'utente corrente.  
  
 *synonym_name*  
 Nome del sinonimo da eliminare.  
  
## <a name="remarks"></a>Osservazioni  
 I riferimenti ai sinonimi non sono associati a uno schema. È pertanto possibile eliminare un sinonimo in qualsiasi momento. I riferimenti ai sinonimi eliminati verranno trovati solo in fase di esecuzione.  
  
 È possibile creare, eliminare e fare riferimento ai sinonimi in SQL dinamico.  
  
## <a name="permissions"></a>Permissions  
 Per eliminare un sinonimo, un utente deve soddisfare almeno una delle condizioni seguenti: L'utente deve essere:  
  
-   Il proprietario corrente di un sinonimo.  
  
-   Un utente autorizzato che dispone dell'autorizzazione CONTROL su un sinonimo.  
  
-   Un utente autorizzato che dispone dell'autorizzazione ALTER SCHEMA sullo schema contenitore.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene prima creato e quindi eliminato il sinonimo `MyProduct`.  
  
```  
USE tempdb;  
GO  
-- Create a synonym for the Product table in AdventureWorks2012.  
CREATE SYNONYM MyProduct  
FOR AdventureWorks2012.Production.Product;  
GO  
-- Drop synonym MyProduct.  
USE tempdb;  
GO  
DROP SYNONYM MyProduct;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SYNONYM &#40; Transact-SQL &#41;](../../t-sql/statements/create-synonym-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
