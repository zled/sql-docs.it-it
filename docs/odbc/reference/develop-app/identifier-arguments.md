---
title: Identificatore argomenti | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- identifier arguments [ODBC]
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], identifier
ms.assetid: b9de003f-cb49-4dec-b528-14a5b8ff12bd
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5cbeb7d146cf82a752beed19befca0cf52eeb2ab
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="identifier-arguments"></a>Argomenti di tipo identificatore
Se una stringa in un argomento dell'identificatore è racchiuso tra virgolette, il driver rimuove iniziali e gli spazi vuoti finali e considera letteralmente la stringa tra virgolette. Se la stringa non è racchiuso tra virgolette, il driver rimuove riduzioni e gli spazi vuoti finali stringa in maiuscolo. L'impostazione di un argomento dell'identificatore a un puntatore null restituisce SQL_ERROR e SQLSTATE HY009 (utilizzo non valido del puntatore null), a meno che l'argomento è un nome di catalogo e i cataloghi non sono supportati.  
  
 Se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_TRUE, questi argomenti vengono trattati come argomenti di identificatore. In questo caso, il carattere di sottolineatura (_) e il segno di percentuale (%) verrà considerato come il carattere effettivo, non come un carattere di criterio di ricerca. Questi argomenti vengono trattati come un normale argomento o un argomento di modello, a seconda dell'argomento, se questo attributo è impostato su SQL_FALSE.  
  
 Anche se gli identificatori che contengono caratteri speciali devono essere racchiusi tra virgolette in istruzioni SQL, sono necessario non essere racchiusi tra virgolette quando viene passato come argomenti di funzione di catalogo, perché passati alle funzioni di catalogo di virgolette vengono interpretate letteralmente. Si supponga ad esempio l'identificatore del tipo di virgolette (che è specifico del driver e viene restituita tramite **SQLGetInfo**) è un segno di virgolette doppie ("). La prima chiamata a **SQLTables** restituisce un set di risultati contenente informazioni sulla tabella contabilità fornitori, mentre la seconda chiamata restituisce informazioni sulla tabella "Contabilità fornitori", che è probabilmente diverso da quanto previsto.  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, "Accounts Payable", SQL_NTS, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "\"Accounts Payable\"", SQL_NTS, NULL, 0);  
```  
  
 Gli identificatori delimitati vengono utilizzati per distinguere un nome di colonna true da una pseudo-colonna con lo stesso nome, ad esempio ROWID in Oracle. Se viene passato un argomento di una funzione di catalogo "ROWID", la funzione funziona con la pseudo-colonna ROWID se esiste. Se la pseudo-colonna non esiste, la funzione funziona con la colonna "ROWID". Se il valore ROWID viene passato un argomento di una funzione di catalogo, la funzione funziona con la colonna ROWID.  
  
 Per ulteriori informazioni sugli identificatori tra virgolette, vedere [identificatori tra virgolette](../../../odbc/reference/develop-app/quoted-identifiers.md).
