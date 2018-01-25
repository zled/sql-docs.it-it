---
title: BufferWithCurves (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 08/11/2017
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
- BufferWithCurves
- BufferWithCurves_TSQL
dev_langs: TSQL
helpviewer_keywords: BufferWithCurves method (geography)
ms.assetid: abf0a11c-c99c-4faa-bf80-3ae8e04d7bfb
caps.latest.revision: "16"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0978418fe682728d02f7c65b5bff581154ae231c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="bufferwithcurves-geography-data-type"></a>BufferWithCurves (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce un **geography** istanza che rappresenta il set di tutti i punti la cui distanza dal chiamante **geography** istanza è minore o uguale al *distanza* parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.BufferWithCurves ( distance )  
```  
  
## <a name="arguments"></a>Argomenti  
 *distance*  
 È un **float** che indica la distanza massima che punti che compongono il buffer può essere dall'istanza di geografia.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="exceptions"></a>Eccezioni  
 I criteri seguenti genereranno un **ArgumentException**.  
  
-   Nessun parametro viene passato al metodo, ad esempio `@g.BufferWithCurves()`  
  
-   Un parametro non numerico viene passato al metodo, ad esempio `@g.BufferWithCurves('a')`  
  
-   **NULL** viene passato al metodo, ad esempio`@g.BufferWithCurves(NULL)`  
  
## <a name="remarks"></a>Osservazioni  
 Nella tabella seguente vengono illustrati i risultati restituiti per i diversi valori della distanza.  
  
|Valore del parametro distance|Dimensioni tipo|Tipo spaziale restituito|  
|--------------------|---------------------|---------------------------|  
|distance < 0|Zero o uno|Vuoto **GeometryCollection** istanza|  
|distanza \< 0|Due o più|Oggetto **CurvePolygon** o **GeometryCollection** istanza con un buffer negativo.<br /><br /> Nota: Un buffer negativo potrebbe creare un oggetto vuoto **GeometryCollection**|
|distance = 0|Tutte le dimensioni|Copia di richiamare **geography** istanza|  
|distance > 0|Tutte le dimensioni|**CurvePolygon** o **GeometryCollection** istanza|  
  
> [!NOTE]  
>  Poiché *distanza* è un **float**, un valore estremamente ridotto può corrispondere a zero nei calcoli.  Quando ciò si verifica, quindi una copia del chiamante **geography** istanza viene restituita.  
  
 Se un **stringa** parametro viene passato al metodo, quindi verrà convertito in un **float** o genererà un `ArgumentException`.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-calling-bufferwithcurves-with-a-parameter-value--0-on-one-dimensional-geography-instance"></a>A. Chiamata a BufferWithCurves() con un valore di parametro < 0 in un'istanza di geografia unidimensionale  
 Nell'esempio seguente viene restituita un'istanza `GeometryCollection` vuota:  
  
 ```sql
 DECLARE @g geography= 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves(-1).ToString();
``` 
  
### <a name="b-calling-bufferwithcurves-with-a-parameter-value--0-on-a-two-dimensional-geography-instance"></a>B. Chiamata a BufferWithCurves() con un valore di parametro < 0 in un'istanza di geografia bidimensionale  
 Nell'esempio seguente viene restituita un'istanza `CurvePolygon` con un buffer negativo:  
  
 ```sql
 DECLARE @g geography = 'CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.BufferWithCurves(-1).ToString()
 ```  
  
### <a name="c-calling-bufferwithcurves-with-a-parameter-value--0-that-returns-an-empty-geometrycollection"></a>C. Chiamata a BufferWithCurves() con un valore di parametro < 0 che restituisce un'istanza GeometryCollection vuota  
 Nell'esempio seguente viene illustrato cosa accade quando il *distanza* parametro è uguale a -2:  
  
 ```sql
 DECLARE @g geography = 'CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.BufferWithCurves(-2).ToString();
 ```  
  
 Questo **selezionare** istruzione restituisce`GEOMETRYCOLLECTION EMPTY`  
  
### <a name="d-calling-bufferwithcurves-with-a-parameter-value--0"></a>D. Chiamata a BufferWithCurves() con un valore di parametro = 0  
 Nell'esempio seguente restituisce una copia dell'oggetto chiamante **geography** istanza:  

 ```sql
 DECLARE @g geography = 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves(0).ToString();
 ```  
  
### <a name="e-calling-bufferwithcurves-with-a-non-zero-parameter-value-that-is-extremely-small"></a>E. Chiamata a BufferWithCurves() con un valore di parametro diverso da zero ed estremamente basso  
 L'esempio seguente restituisce anche una copia del chiamante **geography** istanza:  

 ```sql
 DECLARE @g geography = 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @distance float = 1e-20;  
 SELECT @g.BufferWithCurves(@distance).ToString();
 ```  
  
### <a name="f-calling-bufferwithcurves-with-a-parameter-value--0"></a>F. Chiamata a BufferWithCurves() con un valore di parametro > 0  
 Nell'esempio seguente viene restituita un'istanza `CurvePolygon`:  

 ```sql
 DECLARE @g geography= 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves(2).ToString();
 ```  
### <a name="g-passing-a-valid-string-parameter"></a>G. Passaggio di un parametro di stringa valido  
 Nell'esempio seguente viene restituita la stessa istanza `CurvePolygon` come indicato precedentemente, ma un parametro di stringa viene passato al metodo:  

 ```sql
 DECLARE @g geography= 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves('2').ToString();
```  
  
### <a name="h-passing-an-invalid-string-parameter"></a>H. Passaggio di un parametro di stringa non valido  
 Nell'esempio seguente verrà generato un errore:  

 ```sql
 DECLARE @g geography = 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)'  
 SELECT @g.BufferWithCurves('a').ToString();
 ```  
  
 Si noti che nei due esempi precedenti è stato passato un valore letterale stringa al metodo `BufferWithCurves()`. Il primo esempio funziona perché il valore letterale stringa può essere convertito in un valore numerico. Tuttavia, nel secondo esempio viene generata un'eccezione `ArgumentException`.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [BufferWithCurves &#40; tipo di dati geometry &#41;](../../t-sql/spatial-geometry/bufferwithcurves-geometry-data-type.md)  
  
  
