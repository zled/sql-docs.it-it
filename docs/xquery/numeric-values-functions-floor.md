---
title: Funzione floor (XQuery) | Documenti Microsoft
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- floor function [XQuery]
- fn:floor function
ms.assetid: 4ace57dd-b66e-4b60-a2b9-a1b0f1a0831d
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 41dee329166c3c791a5caf0d5a31393278a96d5d
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="numeric-values-functions---floor"></a>Funzioni di valori numeriche - floor
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce il numero più alto senza nessuna frazione, maggiore del valore del relativo argomento. Se l'argomento è una sequenza vuota, restituisce la sequenza vuota.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn:floor ($arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Argomenti  
 *$arg*  
 Numero al quale viene applicata la funzione.  
  
## <a name="remarks"></a>Osservazioni  
 Se il tipo di *$arg* è uno dei tre tipi numerici di base, **xs: float**, **xs: double**, o **xs: decimal**, il tipo restituito è uguale al *$arg* tipo. Se il tipo di *$arg* è un tipo derivato da uno dei tipi numerici, il tipo restituito è il tipo di base numerico.  
  
 Se è di input per le funzioni fn: floor, fn: Ceiling o Fn **xdt: untypedAtomic**, dati non tipizzati, viene eseguito in modo implicito il cast **xs: double**. Qualsiasi altro tipo di dati genera un errore statico.  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo nel database di esempio AdventureWorks.  
  
 È possibile utilizzare l'esempio di utilizzo nel [funzione ceiling (XQuery)](../xquery/numeric-values-functions-ceiling.md) per il **floor ()** funzione XQuery. È necessario effettuare è sostituire il **Ceiling ()** nella query con funzione di **floor ()** (funzione).  
  
## <a name="implementation-limitations"></a>Limitazioni di implementazione  
 Limitazioni:  
  
-   Il **floor ()** funzione esegue il mapping di tutti i valori integer a xs: decimal.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione CEILING &#40; XQuery &#41;](../xquery/numeric-values-functions-ceiling.md)   
 [arrotondare Function &#40; XQuery &#41;](../xquery/numeric-values-functions-round.md)   
 [Funzioni XQuery per il tipo di dati XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
