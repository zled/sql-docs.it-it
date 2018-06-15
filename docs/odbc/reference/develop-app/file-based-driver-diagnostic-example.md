---
title: Esempio di diagnostica di Driver basati su file | Documenti Microsoft
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
- file-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: 0575fccd-4641-478d-a3cc-5a764e35bae2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d58072bebac57eca8976064b85a25999475a9586
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910376"
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
