---
title: Funzione AVG (XQuery) | Documenti Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:avg function
- avg function [XQuery]
ms.assetid: 0cc60267-3c56-4a88-8ad7-bb07f0255d56
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6c347eb78dd3ac8e58075cc91edeee87b3a4418d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33077161"
---
# <a name="aggregate-functions---avg"></a>Funzioni di aggregazione: avg
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce la media di una sequenza di numeri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn:avg($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>Argomenti  
 *$arg*  
 Sequenza di valori atomici per la quale viene calcolata la media.  
  
## <a name="remarks"></a>Osservazioni  
 Tutti i tipi di valori atomizzati passati a **AVG ()** deve essere un sottotipo di esattamente uno dei tre tipi di base numerici predefiniti o xdt: untypedAtomic. e non possono essere una combinazione di tipi. I valori del tipo xdt:untypedAtomic vengono considerati come xs:double. Il risultato di **AVG ()** riceve il tipo di base dei tipi passati, ad esempio xs: double nel caso di xdt: untypedAtomic.  
  
 Se l'input è costituito da dati statici vuoti, viene generato un errore statico.  
  
 Il **AVG ()** funzione restituisce la media dei numeri calcolata. Esempio:  
  
 **SUM (** *$arg* **) div count (** *$arg* **)**  
  
 Se *$arg* è una sequenza vuota, viene restituita la sequenza vuota.  
  
 Se non è possibile eseguire il cast di un valore xdt: untypedAtomic a xs: Double, tale valore viene ignorato nella sequenza di input, *$arg*.  
  
 In tutti gli altri casi, la funzione restituisce un errore statico.  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo nel database AdventureWorks.  
  
### <a name="a-using-the-avg-xquery-function-to-find-work-center-locations-in-the-manufacturing-process-in-which-labor-hours-are-greater-than-the-average-for-all-work-center-locations"></a>A. Utilizzo della funzione XQuery avg() per trovare i centri di lavorazione del processo di produzione con ore di manodopera superiori alla media di tutti i centri.  
 È possibile riscrivere la query fornita [funzione min (XQuery)](../xquery/aggregate-functions-min.md) per utilizzare il **AVG ()** (funzione).  
  
## <a name="implementation-limitations"></a>Limitazioni di implementazione  
 Limitazioni:  
  
-   Il **AVG ()** funzione esegue il mapping di tutti i valori interi a xs: decimal.  
  
-   Il **AVG ()** funzione con valori di tipo xs: Duration non è supportata.  
  
-   Non sono supportate le sequenze con combinazioni di tipi che non rispettano i limiti del tipo di base.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni XQuery per il tipo di dati XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
