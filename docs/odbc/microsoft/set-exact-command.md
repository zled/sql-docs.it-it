---
title: Comando esatto SET | Documenti Microsoft
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
- SET EXACT command [ODBC]
ms.assetid: 9533d3e0-e7c1-49de-a3a3-0cc4373a91cb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c94efa07d23249c9fc3e9d661998419b68f7b624
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="set-exact-command"></a>Comando esatto SET
Specifica le regole di confronto di due stringhe di lunghezza diversa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET EXACT ON | OFF  
```  
  
## <a name="arguments"></a>Argomenti  
 ON  
 Specifica che le espressioni devono corrispondere a carattere per carattere equivalenti. Per il confronto, vengono ignorati gli spazi vuoti finali nelle espressioni. Per il confronto, il più breve delle due espressioni è applicato un riempimento a destra con spazi vuoti in base alla lunghezza di altra espressione.  
  
 OFF  
 (Predefinito). Specifica che, per essere equivalenti, espressioni devono corrispondere a carattere per carattere fino a quando non viene raggiunta la fine dell'espressione sul lato destro.  
  
## <a name="remarks"></a>Osservazioni  
 L'impostazione SET EXACT ha effetto se entrambe le stringhe siano della stessa lunghezza.  
  
## <a name="string-comparisons"></a>Confronti di stringhe  
 Visual FoxPro ha due operatori relazionali che verifica l'uguaglianza.  
  
 I = operatore esegue un confronto tra due valori dello stesso tipo. Questo operatore è adatta per il confronto dei caratteri, numerico, data e dati logico.  
  
 Tuttavia, quando si confrontano le espressioni di caratteri con l'operatore =, i risultati potrebbero non essere esattamente quanto previsto. Espressioni di caratteri vengono confrontate carattere per carattere da sinistra a destra fino a una delle espressioni non è uguale a altra, fino alla fine dell'espressione sul lato destro del = operatore è raggiungibile (SET esatto OFF), o fino a quando non le entità finali di entrambe le espressioni raggiunto (SET EXACT ON).  
  
 I = = operatore può essere utilizzato quando è necessario un confronto esatto di dati di tipo carattere. Se due espressioni di caratteri vengono confrontate con l'operatore = =, le espressioni su entrambi i lati del = = operatore deve contenere esattamente gli stessi caratteri, compresi gli spazi vuoti, per essere considerate uguali. L'impostazione SET EXACT viene ignorata quando si confrontano le stringhe di caratteri utilizzando = =.  
  
 Nella tabella seguente viene illustrato come la scelta dell'operatore e l'impostazione SET EXACT influire sui confronti. (Un carattere di sottolineatura rappresenta uno spazio vuoto).  
  
|Confronto|= IDENTICO OFF|= IDENTICO IN|= = ESATTA ON o OFF|  
|----------------|------------------|-----------------|--------------------------|  
|"abc" = "abc"|Corrispondenza|Corrispondenza|Corrispondenza|  
|"ab" = "abc"|Nessuna corrispondenza|Nessuna corrispondenza|Nessuna corrispondenza|  
|"abc" = "ab"|Corrispondenza|Nessuna corrispondenza|Nessuna corrispondenza|  
|"abc" = "ab_"|Nessuna corrispondenza|Nessuna corrispondenza|Nessuna corrispondenza|  
|"ab" = "ab_"|Nessuna corrispondenza|Corrispondenza|Nessuna corrispondenza|  
|"ab_" = "ab"|Corrispondenza|Corrispondenza|Nessuna corrispondenza|  
|"" = "ab"|Nessuna corrispondenza|Nessuna corrispondenza|Nessuna corrispondenza|  
|"ab" = ""|Corrispondenza|Nessuna corrispondenza|Nessuna corrispondenza|  
|"__" = ""|Corrispondenza|Corrispondenza|Nessuna corrispondenza|  
|"" = "___"|Nessuna corrispondenza|Corrispondenza|Nessuna corrispondenza|  
|TRIM("___") = ""|Corrispondenza|Corrispondenza|Corrispondenza|  
|"" = TRIM("___")|Corrispondenza|Corrispondenza|Corrispondenza|  
  
## <a name="see-also"></a>Vedere anche  
 [Comando ANSI SET](../../odbc/microsoft/set-ansi-command.md)

