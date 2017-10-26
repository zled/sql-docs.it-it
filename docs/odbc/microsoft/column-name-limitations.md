---
title: Limitazioni di nomi di colonna | Documenti Microsoft
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
- desktop database drivers [ODBC], column names
- ODBC desktop database drivers [ODBC], column names
ms.assetid: 5a339f61-c52f-40ad-8deb-d785f72753d4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a5e2fb7cf9f54177ce357058e51e541b6a442379
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="column-name-limitations"></a>Limitazioni di nomi di colonna
I nomi di colonna possono contenere qualsiasi carattere validi (ad esempio, spazi). Se i nomi di colonna contengono caratteri tranne lettere, numeri e caratteri di sottolineatura, il nome deve essere delimitato racchiudendolo tra virgolette indietro (').  
  
 Quando viene utilizzato il driver Microsoft Access o Microsoft Excel, i nomi di colonna sono limitati a 64 caratteri e i nomi lunghi generano un errore. Quando viene utilizzato il driver Paradox, il nome di colonna massima è di 25 caratteri. Quando viene utilizzato il driver di testo, il nome di colonna massima è di 64 caratteri e i nomi lunghi vengono troncati.  
  
 Quando viene utilizzato il driver dBASE, caratteri con un valore ASCII maggiore di 127 vengono convertiti in caratteri di sottolineatura.  
  
 Quando viene utilizzato il driver per Microsoft Excel, se i nomi di colonna sono presenti, devono essere nella prima riga. Un nome che, in Microsoft Excel, utilizza il "!" carattere deve essere racchiuso tra virgolette indietro ('). Il "!" carattere viene convertito in carattere "$", perché il "!" carattere non è valido in un nome ODBC, anche quando il nome è racchiuso tra virgolette indietro. Tutti gli altri caratteri validi di Microsoft Excel (tranne che il carattere barra verticale (& #124 ;)) sono utilizzabili in un nome di colonna, inclusi gli spazi. Un identificatore delimitato da utilizzare per il nome di una colonna di Microsoft Excel per includere uno spazio. I nomi di colonna specificato verranno sostituiti con nomi generati dal driver, ad esempio, "Col1" per la prima colonna.  
  
 Il carattere barra verticale (&#124;) non può essere utilizzato in un nome di colonna, se il nome è racchiuso tra virgolette indietro o non.  
  
 Quando viene utilizzato il driver di testo, il driver fornisce un nome predefinito se non viene specificato un nome di colonna. Ad esempio, il driver chiama la prima colonna F1, F2 della seconda colonna e così via.

