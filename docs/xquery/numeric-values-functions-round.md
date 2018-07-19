---
title: Funzione Round (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:round function
- round function [XQuery]
ms.assetid: 320b572f-bd5b-4055-95a6-dec5718c0041
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 69c9e11d9cb6dda3aa50a2d49e3eb9c55b99a57b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38055129"
---
# <a name="numeric-values-functions---round"></a>Funzioni per valori numerici - round
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce il numero senza parte frazionaria più vicino all'argomento. Se esiste più di un numero, viene restituito quello più vicino a infinito positivo. Esempio:  
  
 Se l'argomento è 2.5 **Round ()** restituisce 3.  
  
 Se l'argomento, 2.4999 **Round ()** restituisce 2.  
  
 Se l'argomento è -2,5, **Round ()** restituisce -2.  
  
 Se l'argomento è una sequenza vuota, **Round ()** restituisce una sequenza vuota.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn:round ( $arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Argomenti  
 *$arg*  
 Numero al quale viene applicata la funzione.  
  
## <a name="remarks"></a>Note  
 Se il tipo di *$arg* è uno dei tre tipi numerici di base, **xs: float**, **xs: double**, oppure **xs: decimal**, il tipo restituito è come il *$arg* tipo. Se il tipo della *$arg* è un tipo derivato da uno dei tipi numerici, il tipo restituito è il tipo di base numerico.  
  
 Se di input per il **: floor**, **fn: Ceiling**, o **Fn** funzioni è **xdt: untypedAtomic**, i dati non tipizzati, viene eseguito in modo implicito il cast **xs: double**.  
  
 Qualsiasi altro tipo di dati genera un errore statico.  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo nel database AdventureWorks.  
  
 È possibile usare l'esempio reale disponibile nella [funzione ceiling (XQuery)](../xquery/numeric-values-functions-ceiling.md) per il **Round ()** funzione XQuery. È necessario eseguire è sostituire il **Ceiling ()** funzione nella query con la **Round ()** (funzione).  
  
## <a name="implementation-limitations"></a>Limitazioni di implementazione  
 Limitazioni:  
  
-   Il **Round ()** funzione esegue il mapping di valori interi a xs: decimal.  
  
-   Il **Round ()** funzione dei valori xs: Double e xs: float compreso tra - 0.5e0 e - 0e0 a 0e0 anziché a - 0e0 corrispondono.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione floor &#40;XQuery&#41;](../xquery/numeric-values-functions-floor.md)   
 [Funzione CEILING &#40;XQuery&#41;](../xquery/numeric-values-functions-ceiling.md)  
  
  
