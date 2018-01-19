---
title: BufferWithCurves (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords: BufferWithCurves method (geometry)
ms.assetid: 8ffaba3f-d2dd-4e57-9f41-3ced9f14b600
caps.latest.revision: "29"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2651ae4e2a4d245f61115438e959a6881ff1935f
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="bufferwithcurves-geometry-data-type"></a>BufferWithCurves (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Restituisce un **geometry** istanza che rappresenta il set di tutti i punti la cui distanza dal chiamante **geometry** istanza è minore o uguale al *distanza* parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.BufferWithCurves ( distance )  
```  
  
## <a name="arguments"></a>Argomenti  
 *distance*  
 È un **float** che indica la distanza massima che punti che compongono il buffer deve essere compresa la **geometry** istanza.  
  
## <a name="return-types"></a>Tipi restituiti  
Tipo restituito di SQL Server: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="exceptions"></a>Eccezioni  
 I criteri seguenti genereranno un **ArgumentException**.  
  
-   Nessun parametro viene passato al metodo, ad esempio `@g.BufferWithCurves()`  
  
-   Un parametro non numerico viene passato al metodo, ad esempio `@g.BufferWithCurves('a')`  
  
-   **NULL** viene passato al metodo, ad esempio`@g.BufferWithCurves(NULL)`  
  
## <a name="remarks"></a>Osservazioni  
 Nell'illustrazione seguente viene mostrato un esempio di un'istanza di geometria restituita da questo metodo.  
  
 ![BufferedCurve](../../t-sql/spatial-geometry/media/bufferedcurve.gif)
  
 Nella tabella seguente vengono illustrati i risultati restituiti per i diversi valori della distanza.  
  
|Valore del parametro distance|Dimensioni tipo|Tipo spaziale restituito|  
|--------------------|---------------------|---------------------------|  
|distance < 0|Zero o uno|Vuoto **GeometryCollection** istanza|  
|distance < 0|Due o più|Oggetto **CurvePolygon** o **GeometryCollection** istanza con un buffer negativo. **Nota:** un buffer negativo potrebbe creare un oggetto vuoto **GeometryCollection**|  
|distance = 0|Tutte le dimensioni|Copia di richiamare **geometry** istanza|  
|distance > 0|Tutte le dimensioni|**CurvePolygon** o **GeometryCollection** istanza|  
  
> [!NOTE]  
>  Poiché *distanza* è un **float**, un valore estremamente ridotto può corrispondere a zero nei calcoli. Quando ciò si verifica quindi una copia del chiamante **geometry** istanza viene restituita. Vedere [float e real &#40; Transact-SQL &#41; ](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
 Un buffer negativo rimuove tutti i punti racchiusi nella distanza specificata del limite della geometria. Nell'illustrazione seguente viene mostrato un buffer negativo come area lievemente ombreggiata del cerchio. La linea punteggiata è il limite del poligono originale e la linea continua è il limite del poligono risultante.  
  
 Se un **stringa** parametro viene passato al metodo, quindi verrà convertito in un **float** o genererà un `ArgumentException`.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-calling-bufferwithcurves-with-a-parameter-value--0-on-one-dimensional-geometry-instance"></a>A. Chiamata a BufferWithCurves() con un valore di parametro < 0 in un'istanza di geometria unidimensionale  
 Nell'esempio seguente viene restituita un'istanza `GeometryCollection` vuota:  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(-1).ToString(); 
 ```
  
### <a name="b-calling-bufferwithcurves-with-a-parameter-value--0-on-a-two-dimensional-geometry-instance"></a>B. Chiamata a BufferWithCurves() con un valore di parametro < 0 in un'istanza di geometria bidimensionale  
 Nell'esempio seguente viene restituita un'istanza `CurvePolygon` con un buffer negativo:  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.BufferWithCurves(-1).ToString()
 ```  
  
### <a name="c-calling-bufferwithcurves-with-a-parameter-value--0-that-returns-an-empty-geometrycollection"></a>C. Chiamata a BufferWithCurves() con un valore di parametro < 0 che restituisce un'istanza GeometryCollection vuota  
 Nell'esempio seguente viene illustrato cosa accade quando il *distanza* parametro è uguale a -2:  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.BufferWithCurves(-2).ToString();
 ```  
  
 Questo **selezionare** istruzione restituisce`GEOMETRYCOLLECTION EMPTY`  
  
### <a name="d-calling-bufferwithcurves-with-a-parameter-value--0"></a>D. Chiamata a BufferWithCurves() con un valore di parametro = 0  
 Nell'esempio seguente restituisce una copia dell'oggetto chiamante **geometry** istanza:  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(0).ToString();
 ```  
  
### <a name="e-calling-bufferwithcurves-with-a-non-zero-parameter-value-that-is-extremely-small"></a>E. Chiamata a BufferWithCurves() con un valore di parametro diverso da zero ed estremamente basso  
 L'esempio seguente restituisce anche una copia del chiamante **geometry** istanza:  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 DECLARE @distance float = 1e-20; 
 SELECT @g.BufferWithCurves(@distance).ToString();
 ```  
  
### <a name="f-calling-bufferwithcurves-with-a-parameter-value--0"></a>F. Chiamata a BufferWithCurves() con un valore di parametro > 0  
 Nell'esempio seguente viene restituita un'istanza `CurvePolygon`:  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(2).ToString();
 ```  
  
### <a name="g-passing-a-valid-string-parameter"></a>G. Passaggio di un parametro di stringa valido  
 Nell'esempio seguente viene restituita la stessa istanza `CurvePolygon` come indicato precedentemente, ma un parametro di stringa viene passato al metodo:  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves('2').ToString();
 ```  
  
### <a name="h-passing-an-invalid-string-parameter"></a>H. Passaggio di un parametro di stringa non valido  
 Nell'esempio seguente verrà generato un errore:  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)' 
 SELECT @g.BufferWithCurves('a').ToString();
 ```  
  
 Si noti che nei due esempi precedenti è stato passato un valore letterale stringa al metodo `BufferWithCurves()`. Il primo esempio funziona perché il valore letterale stringa può essere convertito in un valore numerico. Tuttavia, nel secondo esempio viene generata un'eccezione `ArgumentException`.  
  
### <a name="i-calling-bufferwithcurves-on-multipoint-instance"></a>I. Chiamata a BufferWithCurves() in un'istanza MultiPoint  
 Nell'esempio seguente vengono restituite due istanze `GeometryCollection` e un'istanza `CurvePolygon`:  
  
```
 DECLARE @g geometry = 'MULTIPOINT((1 1),(1 4))'; 
 SELECT @g.BufferWithCurves(1).ToString(); 
 SELECT @g.BufferWithCurves(1.5).ToString(); 
 SELECT @g.BufferWithCurves(1.6).ToString();
 ```  
  
 I primi due **selezionare** istruzioni restituiscono un `GeometryCollection` istanza perché il parametro *distanza* è minore o uguale a 1/2 la distanza tra i due punti (1 1) e (1 4). Il terzo **selezionare** istruzione restituisce un `CurvePolygon` istanza perché le istanze memorizzate nel buffer dei due punti (1 1) e (1 4) si sovrappongono.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geometria](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
 
