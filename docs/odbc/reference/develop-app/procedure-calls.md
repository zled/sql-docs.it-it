---
title: Le chiamate di procedura | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], procedure calls
- procedure calls [ODBC]
ms.assetid: 145130cc-40e7-4722-8417-dff131084752
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6327ef340fe5fbd712ad9237bb6749d20bbd69af
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912778"
---
# <a name="procedure-calls"></a>Chiamate di procedure
Oggetto *procedura* è un oggetto eseguibile archiviato nell'origine dati. In genere, si tratta di una o più istruzioni SQL precompilate. La sequenza di escape per chiamare una stored procedure  
  
 **{**[**? =**]**chiamare** *-nome della stored procedure*[**(**[*parametro*] [**,**[*parametro*]]... **)**]**}**  
  
 dove *nome procedura* specifica il nome di una stored procedure e *parametro* specifica un parametro di routine.  
  
 Per ulteriori informazioni sulla sequenza di escape chiamata di procedura, vedere [sequenza di Escape di chiamata di procedura](../../../odbc/reference/appendixes/procedure-call-escape-sequence.md) nella grammatica SQL di appendice c:.  
  
 Una procedura può avere zero o più parametri. Può inoltre restituire un valore, come indicato dall'indicatore di parametro facoltativi **? =** all'inizio della sintassi. Se *parametro* è un input o un parametro di input/output, può essere un valore letterale o un marcatore di parametro. Tuttavia, applicazioni interoperative devono sempre utilizzare marcatori di parametro poiché alcune origini dati non accettano valori di parametro del valore letterale. Se *parametro* è un parametro di output, deve essere un marcatore di parametro. Marcatori di parametro devono essere associati con **SQLBindParameter** prima della chiamata di stored procedure viene eseguita l'istruzione.  
  
 I parametri di input e di input/output possono essere omessi dalle chiamate alle procedure. Se una routine viene chiamata con parentesi ma senza parametri, ad esempio {chiamare *nome procedura*()}, il driver indica all'origine dati per utilizzare il valore predefinito per il primo parametro. Se la procedura non ha alcun parametro, ciò potrebbe causare la procedura per l'esito negativo. Se una routine viene chiamata senza parentesi, ad esempio {chiamare *nome procedura*}, il driver non invia i valori dei parametri.  
  
 È possibile specificare valori letterali per parametri di input e di input/output nelle chiamate alle procedure. Ad esempio, si supponga che la procedura **InsertOrder** include cinque parametri di input. La seguente chiamata al **InsertOrder** omette il primo parametro, fornisce un valore letterale per il secondo parametro e utilizza un marcatore di parametro per il terzo, quarto e quinto parametri:  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}   // Not interoperable!  
```  
  
 Si noti che se un parametro viene omesso, la virgola che lo separa da altri parametri deve comunque essere presente. Se si omette un parametro di input o di input/output, la procedura utilizza il valore predefinito del parametro. Un altro modo per specificare che il valore predefinito di un parametro di input o input/output consiste nell'impostare il valore del buffer di lunghezza/indicatore associato al parametro su SQL_DEFAULT_PARAM.  
  
 Se si omette un parametro di input/output o se viene fornito un valore letterale per il parametro, il driver ignora il valore di output. Analogamente, se il marcatore di parametro per il valore restituito di una procedura viene omesso, il driver ignora il valore restituito. Se, infine, un'applicazione specifica un parametro di valore restituito per una procedura che non restituisce alcun valore, il driver imposta il valore per il buffer di lunghezza/indicatore associato al parametro su SQL_NULL_DATA.  
  
 Si supponga che la routine PARTS_IN_ORDERS crea un set di risultati che contiene un elenco di ordini che contengono un numero di parte specifica. Il codice seguente chiama questa procedura per il numero di parte 544:  
  
```  
SQLUINTEGER   PartID;  
SQLINTEGER    PartIDInd = 0;  
  
// Bind the parameter.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_SLONG, SQL_INTEGER, 0, 0,  
                  &PartID, 0, PartIDInd);  
  
// Place the department number in PartID.  
PartID = 544;  
  
// Execute the statement.  
SQLExecDirect(hstmt, "{call PARTS_IN_ORDERS(?)}", SQL_NTS);  
```  
  
 Per determinare se un'origine dati supporta le procedure, un'applicazione chiama **SQLGetInfo** con l'opzione SQL_PROCEDURES.  
  
 Per ulteriori informazioni sulle procedure, vedere [procedure](../../../odbc/reference/develop-app/procedures-odbc.md).
