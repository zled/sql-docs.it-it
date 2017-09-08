---
title: Ridurre (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Reduce_TSQL
- Reduce
dev_langs:
- TSQL
helpviewer_keywords:
- Reduce method
ms.assetid: c5dfa8c1-6764-41d8-9150-f3cb30633d3e
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c5b174f3f4b8daf99c402b110ba10d95345783d7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="reduce-geography-data-type-"></a>Reduce (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce un'approssimazione del determinato **geography** istanza prodotta eseguendo l'algoritmo Douglas-Peucker sull'istanza con la tolleranza specificata.  
  
 Questo **geography** metodo supportata dal tipo di dati **FullGlobe** istanze o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.Reduce ( tolerance )  
```  
  
## <a name="arguments"></a>Argomenti  
  
|||  
|-|-|  
|Nome|Definizione|  
|*tolleranza di errore*|È un valore di tipo **float**. *tolleranza* è la tolleranza per l'input dell'algoritmo Douglas-Peucker. *tolleranza* deve essere un numero positivo.|  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 Per i tipi di raccolta, questo algoritmo opera indipendentemente su ciascun **geography** contenuti nell'istanza. Questo algoritmo non modifica **punto** istanze.  
  
 Questo metodo tenterà di mantenere gli endpoint di **LineString** istanze, ma potrebbe non riuscire a cui si desidera per mantenere un risultato valido.  
  
 Se `Reduce()` viene chiamato con un valore negativo, questo metodo genererà un' **ArgumentException**. Le tolleranze utilizzate in `Reduce()` devono essere numeri positivi.  
  
 Il funzionamento dell'algoritmo Douglas-Peucker su ogni curva o cerchio nel **geography** istanza rimuovendo tutti i punti tranne il punto di inizio e fine. Ogni punto rimosso viene quindi aggiunto nuovamente, a partire dal punto dista più lontano, fino a quando non più di *tolleranza* dal risultato. Poiché deve essere garantito un risultato valido, se necessario il risultato viene reso valido.  
  
 In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], questo metodo è stato esteso alle **FullGlobe** istanze.  
  
 Il metodo non è preciso.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `LineString` e viene utilizzato il metodo `Reduce()` per semplificarla.  
  
```  
DECLARE @g geography = 'LineString(120 45, 120.1 45.1, 199.9 45.2, 120 46)'  
SELECT @g.Reduce(10000).ToString()  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
