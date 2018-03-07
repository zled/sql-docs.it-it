---
title: NULL e sconosciuto (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 9d491846-4730-4740-a680-77c69fae4a58
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c26004fdfa5f2607235ffe7dddb7826a77f38b31
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="null-and-unknown-transact-sql"></a>NULL e sconosciuto (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  NULL indica che il valore è sconosciuto. Un valore null è diverso dal valore zero o vuota. Non esistono due valori Null uguali. I confronti tra due valori null o tra un valore null e qualsiasi altro valore restituiscono unknown in quanto il valore di ogni NULL è sconosciuto.  
  
 I valori null indicano in genere dati che sono sconosciuto, non è applicabile, o da aggiungere in un secondo momento. È possibile, ad esempio, che l'iniziale del secondo nome di un cliente non sia nota nel momento in cui il cliente emette un ordine.  
  
 Si noti quanto segue sui valori null:  
  
-   Per verificare i valori Null in una query, utilizzare IS NULL o IS NOT NULL nella clausola WHERE.  
  
-   I valori null possono essere inseriti in una colonna specificando esplicitamente NULL in un'istruzione INSERT o UPDATE o specificando la colonna da un'istruzione INSERT.  
  
-   I valori null possono essere utilizzati come le informazioni necessarie per distinguere una riga in una tabella da un'altra riga in una tabella, ad esempio le chiavi primarie, o per le informazioni utilizzate per distribuire le righe, ad esempio le chiavi di distribuzione.  
  
 Se i dati includono valori Null, gli operatori logici e di confronto possono restituire potenzialmente un terzo valore, ovvero UNKNOWN, anziché TRUE o FALSE. Questa logica a tre valori è necessaria, ma causa numerosi errori nelle applicazioni. Operatori logici in un'espressione booleana che include incognite restituirà sconosciuto a meno che il risultato dell'operatore non dipende da espressione sconosciuto. Queste tabelle sono esempi di questo comportamento.  
  
 Nella tabella seguente mostra i risultati di applicazione di un operatore AND a due espressioni booleane in un'espressione restituisce UNKNOWN.  
  
|Espressione di 1|Espressione 2|Risultato|  
|---------------|---------------|------------|  
|TRUE|UNKNOWN|UNKNOWN|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|FALSE|  
  
 Nella tabella seguente mostra i risultati di applicazione di un operatore OR a due espressioni booleane in un'espressione restituisce UNKNOWN.  
  
|Espressione di 1|Espressione 2|Risultato|  
|---------------|---------------|------------|  
|TRUE|UNKNOWN|TRUE|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|UNKNOWN|  
  
## <a name="see-also"></a>Vedere anche  
 [AND &#40;Transact-SQL&#41;](../../t-sql/language-elements/and-transact-sql.md)   
 [OR &#40;Transact-SQL&#41;](../../t-sql/language-elements/or-transact-sql.md)   
 [NOT &#40;Transact-SQL&#41;](../../t-sql/language-elements/not-transact-sql.md)   
 [IS NULL &#40;Transact-SQL&#41;](../../t-sql/queries/is-null-transact-sql.md)  
  
  
