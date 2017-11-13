---
title: In ODBC sequenze di escape | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- escape sequences [ODBC]
- SQL statements [ODBC], escape sequences
- escape sequences [ODBC], about escape sequences
ms.assetid: cf229f21-6c38-4b5b-aca8-f1be0dfeb3d0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 92fd9745bccacad3d7487c3ed9f1bee58eeb4411
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="escape-sequences-in-odbc"></a>Sequenze di escape in ODBC
Un numero di funzionalità del linguaggio, ad esempio gli operatori outer join e chiamate di funzione scalare, in genere viene implementato da DBMS. Tuttavia, la sintassi per queste funzionalità tendono a essere DBMS specifici, anche quando la sintassi standard definita organismi vari standard. Per questo motivo, ODBC definisce sequenze di escape che contengono la sintassi standard per le funzionalità del linguaggio seguenti:  
  
-   Valori letterali di intervallo di date, time, timestamp e datetime  
  
-   Funzioni scalari, ad esempio numerico, stringa e funzioni di conversione di tipi di dati  
  
-   COME carattere di escape del predicato  
  
-   Outer join  
  
-   Chiamate di procedure  
  
 La sequenza di escape utilizzata da ODBC è il seguente:  
  
```  
  
(extension)  
  
```  
  
## <a name="remarks"></a>Osservazioni  
 La sequenza di escape viene riconosciuta e analizzata dal driver, che sostituiscono le sequenze di escape con la grammatica per DBMS specifici. Per ulteriori informazioni sulla sintassi della sequenza di escape, vedere [sequenze di Escape ODBC](../../../odbc/reference/appendixes/odbc-escape-sequences.md) nella grammatica SQL di appendice c:.  
  
> [!NOTE]  
>  In ODBC 2. *x*, questa è la sintassi standard della sequenza di escape: **-(\*fornitore (***-nome del fornitore***), prodotto (** *nome prodotto***)***estensione*  **\*).**  
>   
>  Oltre a questa sintassi, è stata definita una sintassi abbreviata nel formato: **{***estensione***}**  
>   
>  In ODBC 3. *x*, la forma estesa della sequenza di escape è stata deprecata e la forma abbreviata viene utilizzato in modo esclusivo.  
  
 Poiché le sequenze di escape vengono mappate dal driver per la sintassi specifici del DBMS, un'applicazione può utilizzare la sequenza di escape o una sintassi specifici del DBMS. Tuttavia, le applicazioni che utilizzano la sintassi specifici del DBMS non sarà interoperative. Quando si utilizza la sequenza di escape, le applicazioni devono assicurarsi che l'attributo di istruzione SQL_ATTR_NOSCAN è stato disattivato, ovvero per impostazione predefinita. In caso contrario, la sequenza di escape verrà inviata direttamente all'origine dati, in cui in genere causerà un errore di sintassi.  
  
 I driver supportano solo le sequenze di escape che possono eseguire il mapping alle caratteristiche linguistiche sottostante. Ad esempio, se l'origine dati non supporta gli operatori outer join, non sarà il driver. Per determinare quali sequenze di escape sono supportati, un'applicazione chiama **SQLGetTypeInfo** e **SQLGetInfo**. Per ulteriori informazioni, vedere la sezione successiva, [Date, Time e Timestamp letterali](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Date, Time e Timestamp letterali](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)  
  
-   [Chiamate di funzione scalare](../../../odbc/reference/develop-app/scalar-function-calls.md)  
  
-   [COME carattere di Escape predicato](../../../odbc/reference/develop-app/like-predicate-escape-character.md)  
  
-   [Outer join](../../../odbc/reference/develop-app/outer-joins.md)  
  
-   [Chiamate di procedure](../../../odbc/reference/develop-app/procedure-calls.md)

