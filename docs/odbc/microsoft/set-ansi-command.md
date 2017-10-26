---
title: Comando ANSI SET | Documenti Microsoft
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
- set ANSI command [ODBC]
ms.assetid: cf9a01b2-14bf-458c-a73c-2a58ddef32d8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2095dc0b30fc2e16d4ce691cc097dcda1614d090
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="set-ansi-command"></a>Comando ANSI SET
Determina come i confronti tra stringhe di lunghezza diversa vengono apportati con l'operatore = nei comandi di Visual FoxPro SQL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET ANSI ON | OFF  
```  
  
## <a name="arguments"></a>Argomenti  
 ON  
 (Impostazione predefinita per il driver; il valore predefinito di Visual FoxPro è impostata su OFF). Riempie che la stringa più corta con gli spazi vuoti è necessario rendono lunghezza uguale o maggiore della stringa. Le due stringhe vengono quindi confrontati carattere per carattere per l'intera lunghezza. Si consideri questo confronto:  
  
```  
'Tommy' = 'Tom'  
```  
  
 Il risultato è False (. F.) se il SET ANSI, infatti, quando l'operazione di riempimento, 'Tom' diventa 'Tom' e le stringhe 'Tom' e 'Tommaso' non corrispondono carattere per carattere.  
  
 I = = (operatore) viene utilizzato questo metodo per i confronti di comandi di Visual FoxPro SQL.  
  
 OFF  
 Specifica che la stringa più corta non vengano riempiti con spazi vuoti. Le due stringhe vengono confrontate carattere per carattere fino a quando non viene raggiunta la fine della stringa più corta. Si consideri questo confronto:  
  
```  
'Tommy' = 'Tom'  
```  
  
 Il risultato è True (. Quando SET ANSI è off, in quanto T.) il confronto si arresta dopo 'Tom'.  
  
## <a name="remarks"></a>Osservazioni  
 SET ANSI determina se il valore inferiore tra due stringhe viene riempito con spazi vuoti quando viene effettuato un confronto tra stringhe SQL. SET ANSI non ha alcun effetto = = (operatore); Quando si utilizza l'operatore = =, la stringa più corta sempre viene riempita con spazi vuoti per il confronto.  
  
## <a name="string-order"></a>Ordine di stringa  
 Nei comandi SQL, l'ordine da sinistra a destra di due stringhe in un confronto è irrelevantswitching una stringa da un lato della = o = = (operatore) a altra non influisce sul risultato del confronto.  
  
## <a name="see-also"></a>Vedere anche  
 [Selezionare - comando SQL](../../odbc/microsoft/select-sql-command.md)   
 [Comando esatto SET](../../odbc/microsoft/set-exact-command.md)

