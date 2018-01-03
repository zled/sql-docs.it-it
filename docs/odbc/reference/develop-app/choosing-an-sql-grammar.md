---
title: Scelta di una grammatica SQL | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], SQL grammar
- SQL grammar [ODBC], selecting
ms.assetid: 4e0d189b-e407-47e0-92a9-f9982230dd0e
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6eedc2466842d922e1b10445500f05ad904d1a0b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="choosing-an-sql-grammar"></a>Scelta di una grammatica SQL
La prima decisione da prendere durante la costruzione di istruzioni SQL è quali grammatica da utilizzare. Oltre alle grammatiche disponibili dai corpi dei vari standard, ad esempio Open Group, ANSI e ISO, praticamente ogni fornitore del sistema DBMS definisce il proprio grammatica, ognuno dei quali varia leggermente dallo standard.  
  
 [Appendice c: la grammatica SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md), descrive la grammatica SQL minima che devono supportare tutti i driver ODBC. Questa sintassi sono un subset di Entry level di SQL-92. I driver possono supportare ulteriore grammatica per essere conformi a FIPS 127-2 transizione livelli definiti da SQL-92, intermedio o Full. Per ulteriori informazioni, vedere [la grammatica SQL minima](../../../odbc/reference/appendixes/sql-minimum-grammar.md) nella grammatica SQL di appendice c: e SQL-92.  
  
 Appendice C definisce inoltre *sequenze di escape* contenente grammatica standard per le funzionalità del linguaggio comunemente disponibili, ad esempio gli outer join, che non rientrano la grammatica SQL-92. Per ulteriori informazioni, vedere [sequenze di Escape ODBC](../../../odbc/reference/appendixes/odbc-escape-sequences.md) nella grammatica SQL di appendice c:, e [sequenze di Escape](../../../odbc/reference/develop-app/escape-sequences.md), più avanti in questa sezione.  
  
 Grammatica viene scelto influisce sul modo in cui il driver elabora l'istruzione. I driver è necessario modificare SQL-92 SQL e le sequenze di escape definite da ODBC per SQL DBMS specifici. Perché la maggior parte delle grammatiche SQL si basano su uno o più dei vari standard, la maggior parte dei driver eseguita senza alcuna operazione per soddisfare questo requisito. È spesso costituita solo di ricerca per le sequenze di escape definite da ODBC e sostituirli con la grammatica per DBMS specifici. Quando un driver rileva grammatica che non riconosce, si presuppone la grammatica è specifico del sistema DBMS e passa l'istruzione SQL senza apportare modifiche all'origine dati per l'esecuzione.  
  
 Pertanto, sono disponibili due opzioni di sintassi da utilizzare: la grammatica SQL-92 (e sequenze di escape ODBC) e una grammatica specifici del DBMS. Tra i due, solo la grammatica SQL-92 è interoperativa, in modo interoperative tutte le applicazioni devono utilizzare. Le applicazioni che non sono interoperativi possono utilizzare la grammatica SQL-92 o una grammatica specifici del DBMS. Le grammatiche specifici del DBMS offrono due vantaggi: È possibile sfruttare le funzionalità non coperto da SQL-92, che sono leggermente più veloce perché il driver non è necessario modificarle. La funzionalità di quest'ultima può essere applicata parzialmente impostando l'attributo di istruzione SQL_ATTR_NOSCAN, interrompe il driver di ricerca e sostituzione di sequenze di escape.  
  
 Se viene utilizzata la grammatica SQL-92, l'applicazione può scoprire come viene modificato dal driver chiamando **SQLNativeSql**. Ciò è spesso utile durante il debug di applicazioni. **SQLNativeSql** accetta un'istruzione SQL e lo restituisce dopo che il driver è stato modificato. Poiché questa funzione è il livello di conformità di interfaccia di base, è supportato da tutti i driver.
