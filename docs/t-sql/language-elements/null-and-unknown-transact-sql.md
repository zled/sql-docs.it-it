---
title: NULL e sconosciuto (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 9d491846-4730-4740-a680-77c69fae4a58
caps.latest.revision: 5
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bdac1899707b3caa4f4c515324511a47830f2722
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="null-and-unknown-transact-sql"></a>NULL e sconosciuto (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  NULL indica che il valore è sconosciuto. Un valore null è diverso dal valore zero o vuota. Non esistono due valori Null uguali. I confronti tra due valori null o tra un valore null e qualsiasi altro valore restituiscono unknown in quanto il valore di ogni NULL è sconosciuto.  
  
 I valori null indicano in genere dati che sono sconosciuto, non è applicabile, o da aggiungere in un secondo momento. È possibile, ad esempio, che l'iniziale del secondo nome di un cliente non sia nota nel momento in cui il cliente emette un ordine.  
  
 Si noti quanto segue sui valori null:  
  
-   Per verificare i valori Null in una query, utilizzare IS NULL o IS NOT NULL nella clausola WHERE.  
  
-   I valori null possono essere inseriti in una colonna specificando esplicitamente NULL in un'istruzione INSERT o UPDATE o specificando la colonna da un'istruzione INSERT.  
  
-   I valori null possono essere utilizzati come le informazioni necessarie per distinguere una riga in una tabella da un'altra riga in una tabella, ad esempio le chiavi primarie, o per le informazioni utilizzate per distribuire le righe, ad esempio le chiavi di distribuzione.  
  
 Se i dati includono valori Null, gli operatori logici e di confronto possono restituire potenzialmente un terzo valore, ovvero UNKNOWN, anziché TRUE o FALSE. Questa logica a tre valori è necessaria, ma causa numerosi errori nelle applicazioni. Nelle tabelle riportate di seguito viene descritto il risultato ottenuto dal confronto tra valori Null.  
  
 La tabella seguente illustra i risultati dell'applicazione di un operatore AND a due operandi booleani, dove un operando restituisce NULL.  
  
|Operando di 1|Operando 2|Risultato|  
|---------------|---------------|------------|  
|TRUE|NULL|FALSE|  
|NULL|NULL|FALSE|  
|FALSE|NULL|FALSE|  
  
 La tabella seguente illustra i risultati dell'applicazione di un operatore OR a due operandi booleani, dove un operando restituisce NULL.  
  
|Operando di 1|Operando 2|Risultato|  
|---------------|---------------|------------|  
|TRUE|NULL|TRUE|  
|NULL|NULL|UNKNOWN|  
|FALSE|NULL|UNKNOWN|  
  
## <a name="see-also"></a>Vedere anche  
 [E &#40; Transact-SQL &#41;](../../t-sql/language-elements/and-transact-sql.md)   
 [O &#40; Transact-SQL &#41;](../../t-sql/language-elements/or-transact-sql.md)   
 [NON &#40; Transact-SQL &#41;](../../t-sql/language-elements/not-transact-sql.md)   
 [È NULL &#40; Transact-SQL &#41;](../../t-sql/queries/is-null-transact-sql.md)  
  
  
