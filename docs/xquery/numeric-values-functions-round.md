---
title: Funzione Round (XQuery) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- fn:round function
- round function [XQuery]
ms.assetid: 320b572f-bd5b-4055-95a6-dec5718c0041
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a579433be42dbd22db3467cbf72a9bb4de623a51
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="numeric-values-functions---round"></a>Funzioni a valori numeriche - round
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce il numero senza parte frazionaria più vicino all'argomento. Se esiste più di un numero, viene restituito quello più vicino a infinito positivo. Esempio:  
  
 Se l'argomento è 2.5, **Round ()** restituisce 3.  
  
 Se l'argomento è 2.4999, **Round ()** restituisce 2.  
  
 Se l'argomento è -2,5, **Round ()** restituisce -2.  
  
 Se l'argomento è una sequenza vuota, **Round ()** restituisce la sequenza vuota.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn:round ( $arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Argomenti  
 *$arg*  
 Numero al quale viene applicata la funzione.  
  
## <a name="remarks"></a>Osservazioni  
 Se il tipo di *$arg* è uno dei tre tipi numerici di base, **xs: float**, **xs: double**, o **xs: decimal**, il tipo restituito è uguale al *$arg* tipo. Se il tipo di *$arg* è un tipo derivato da uno dei tipi numerici, il tipo restituito è il tipo di base numerico.  
  
 Se l'input di **fn: floor**, **fn: Ceiling**, o **Fn** funzioni è **xdt: untypedAtomic**, dati non tipizzati, viene eseguito in modo implicito il cast **xs: double**.  
  
 Qualsiasi altro tipo di dati genera un errore statico.  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo nel database AdventureWorks.  
  
 È possibile utilizzare l'esempio di utilizzo nel [funzione ceiling (XQuery)](../xquery/numeric-values-functions-ceiling.md) per il **Round ()** funzione XQuery. È necessario effettuare è sostituire il **Ceiling ()** nella query con funzione di **Round ()** (funzione).  
  
## <a name="implementation-limitations"></a>Limitazioni di implementazione  
 Limitazioni:  
  
-   Il **Round ()** funzione esegue il mapping di valori interi a xs: decimal.  
  
-   Il **Round ()** funzione di xs: Double e xs: float valori compresi tra - 0.5 E0 e - 0e0 viene eseguito il mapping a 0e0 anziché a - 0e0.  
  
## <a name="see-also"></a>Vedere anche  
 [floor (funzione) &#40; XQuery &#41;](../xquery/numeric-values-functions-floor.md)   
 [Funzione CEILING &#40; XQuery &#41;](../xquery/numeric-values-functions-ceiling.md)  
  
  
