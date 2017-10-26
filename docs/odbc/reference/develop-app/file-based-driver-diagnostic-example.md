---
title: Esempio di diagnostica di Driver basati su file | Documenti Microsoft
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
- file-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: 0575fccd-4641-478d-a3cc-5a764e35bae2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 309bea8c888b7fd057e942dd348125c9b420afb7
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="file-based-driver-diagnostic-example"></a>Esempio di diagnostica di Driver basati su file
Un driver basati su file funge sia da un driver ODBC che come un'origine dati. Vengono pertanto generati errori e avvisi sia come un componente in una connessione ODBC e come un'origine dati. Poiché anche il componente che si interfaccia con gestione Driver, viene formattato e restituisce gli argomenti per **SQLGetDiagRec**.  
  
 Ad esempio, se un driver Microsoft® per dBASE non è riuscito ad allocare memoria sufficiente, potrebbe restituire i valori seguenti **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY001"  
Native Error:      42052  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver]Unable to allocate sufficient memory."  
```  
  
 Poiché questo errore non è correlato all'origine dati, il driver aggiunti solo i prefissi degli spazi per il messaggio di diagnostica per il fornitore ([Microsoft]) e il driver ([ODBC Driver di dBASE]).  
  
 Se il driver non è riuscito a trovare il file Employee. dbf, potrebbe restituire i valori seguenti **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1305  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver][dBASE]No such table or object"  
```  
  
 Poiché questo errore è correlato all'origine dati, il driver aggiunto il formato di file dell'origine dati ([dBASE]) come prefisso per il messaggio di diagnostica. Poiché il driver è stato anche il componente di interfaccia duale con l'origine dati, aggiungerlo prefissi per il fornitore ([Microsoft]) e il driver ([ODBC Driver di dBASE]).

