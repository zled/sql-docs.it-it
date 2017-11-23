---
title: Ridurre (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Reduce_TSQL
- Reduce
dev_langs: TSQL
helpviewer_keywords: Reduce method
ms.assetid: 132184bf-c4d2-4a27-900d-8373445dce2a
caps.latest.revision: "30"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f92ff59bff23d1b3cd2909c0d6aedd45443a159f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="reduce-geometry-data-type"></a>Reduce (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un'approssimazione del determinato **geometry** istanza prodotto dall'esecuzione di un'estensione dell'algoritmo Douglas-Peucker sull'istanza con la tolleranza specificata.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.Reduce ( tolerance )  
```  
  
## <a name="arguments"></a>Argomenti  
 *tolleranza di errore*  
 È un valore di tipo **float**. *tolleranza* è la tolleranza per l'input per l'algoritmo di approssimazione.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Osservazioni  
 Per i tipi di raccolta, questo algoritmo opera indipendentemente su ciascun **geometry** contenuti nell'istanza.  
  
 Questo algoritmo non modifica **punto** istanze.  
  
 In **LineString**, **CircularString**, e **CompoundCurve** istanze, l'algoritmo di approssimazione mantiene l'originale punti iniziale e finale dell'istanza, e in modo iterativo, aggiunge nuovamente il punto dall'istanza originale con la maggiore deviazione rispetto al risultato finché nessun punto devia più della tolleranza specificata.  
  
 `Reduce()`Restituisce un **LineString**, **CircularString**, o **CompoundCurve** istanza per **CircularString** istanze.  `Reduce()`Restituisce un **CompoundCurve** o **LineString** istanza per **CompoundCurve** istanze.  
  
 In **poligono** istanze, l'algoritmo di approssimazione viene applicato indipendentemente a ogni anello. Il metodo produrrà un `FormatException` se l'oggetto restituito **poligono** istanza non è valida; ad esempio, un non valido **MultiPolygon** istanza viene creata se `Reduce()` viene applicato per semplificare ogni anello nell'istanza e gli anelli risultanti si sovrappongono.  In **CurvePolygon** istanze con un anello esterno e nessun anello interno, `Reduce()` restituisce un **CurvePolygon**, **LineString**, o **punto** istanza.  Se il **CurvePolygon** dispone di anelli interni un **CurvePolygon** o **MultiPoint** istanza viene restituita.  
  
 Quando viene rilevato un segmento di arco circolare, l'algoritmo di approssimazione controlla se è possibile approssimare l'arco secondo la corda in metà della tolleranza specificata.  Se la corda soddisfa questi criteri, l'arco circolare viene sostituito nei calcoli dalla corda. Se non soddisfa questi criteri, l'arco circolare viene mantenuto e l'algoritmo di approssimazione viene applicato ai segmenti rimanenti.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-reduce-to-simplify-a-linestring"></a>A. Utilizzo di Riduce() per semplificare LineString  
 Nell'esempio seguente viene creata un'istanza `LineString` e viene utilizzato il metodo `Reduce()` per semplificarla.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0, 2 1, 3 0, 4 1)', 0);  
SELECT @g.Reduce(.75).ToString();  
```  
  
### <a name="b-using-reduce-with-varying-tolerance-levels-on-a-circularstring"></a>B. Utilizzo di Riduce() con livelli di tolleranza diversi su CircularString  
 L'esempio seguente usa `Reduce()` con tre livelli di tolleranza su un **CircularString** istanza:  
  
```
 DECLARE @g geometry = 'CIRCULARSTRING(0 0, 8 8, 16 0, 20 -4, 24 0)'; 
 SELECT @g.Reduce(5).ToString(); 
 SELECT @g.Reduce(15).ToString(); 
 SELECT @g.Reduce(16).ToString();
 ```  
  
 Nell'esempio viene prodotto l'output seguente:  
  
 ```
 CIRCULARSTRING (0 0, 8 8, 16 0, 20 -4, 24 0) 
 COMPOUNDCURVE (CIRCULARSTRING (0 0, 8 8, 16 0), (16 0, 24 0)) 
 LINESTRING (0 0, 24 0)
 ```  
  
 Ogni istanza restituita contiene i punti finali (0 0) e (24 0).  
  
### <a name="c-using-reduce-with-varying-tolerance-levels-on-a-compoundcurve"></a>C. Utilizzo di Riduce() con livelli di tolleranza diversi su CompoundCurve  
 L'esempio seguente usa `Reduce()` con due livelli di tolleranza su un **CompoundCurve** istanza:  
  
```
 DECLARE @g geometry = 'COMPOUNDCURVE(CIRCULARSTRING(0 0, 8 8, 16 0, 20 -4, 24 0),(24 0, 20 4, 16 0))';  
 SELECT @g.Reduce(15).ToString();  
 SELECT @g.Reduce(16).ToString();
 ```  
  
 In questo esempio si noti che il secondo **selezionare** istruzione restituisce il **LineString** istanza: `LineString(0 0, 16 0)`.  
  
### <a name="showing-an-example-where-the-original-start-and-end-points-are-lost"></a>Visualizzazione di un esempio in cui i punti di inizio e fine originali vengono persi  
 Nell'esempio seguente viene illustrato come i punti di inizio e fine originali potrebbero non essere mantenuti dall'istanza risultante. Questo errore si verifica perché mantenere all'inizio originario e punti di fine darà origine a un oggetto non valido **LineString** istanza.  
  
```  
DECLARE @g geometry = 'LINESTRING(0 0, 4 0, 2 .01, 1 0)';  
DECLARE @h geometry = @g.Reduce(1);  
SELECT @g.STIsValid() AS Valid  
SELECT @g.ToString() AS Original, @h.ToString() AS Reduced;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geometria statici estesi](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

