---
title: STBuffer (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STBuffer (geometry Data Type)
- STBuffer_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STBuffer (geometry Data Type)
ms.assetid: ca6bf2dc-1d38-4503-b87e-f2ea033d36ba
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 87ad6ea01e471cf1ec407f0b8372300d07f0118f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stbuffer-geometry-data-type"></a>STBuffer (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un oggetto geometrico che rappresenta l'unione di tutti i punti la cui distanza da un **geometry** istanza è minore o uguale a un valore specificato.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STBuffer ( distance )  
```  
  
## <a name="arguments"></a>Argomenti  
 *distanza*  
 È un valore di tipo **float** (**doppie** in .NET Framework) che specifica la distanza dall'istanza di geometria intorno alla quale calcolare il buffer.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Osservazioni  
 `STBuffer()`Calcola un buffer in modo analogo [BufferWithTolerance](../../t-sql/spatial-geometry/bufferwithtolerance-geometry-data-type.md), specificando *tolleranza* = distanza \* .001 e *relativo*  =   **false**.  
  
 Quando *distanza* > 0, un **poligono** o **MultiPolygon** istanza viene restituita.  
  
> [!NOTE]  
>  Poiché la distanza è un **float**, un valore estremamente ridotto può corrispondere a zero nei calcoli.  Quando ciò si verifica, una copia del chiamante **geometry** istanza viene restituita.  Vedere [float e real &#40; Transact-SQL &#41;](../../t-sql/data-types/float-and-real-transact-sql.md)  
  
 Quando *distanza* = 0, quindi una copia del chiamante **geometry** istanza viene restituita.  
  
 Quando *distanza* < 0, quindi  
  
-   un oggetto vuoto **GeometryCollection** istanza viene restituita quando le dimensioni dell'istanza sono 0 o 1.  
  
-   viene restituito un buffer negativo quando le dimensioni dell'istanza sono 2 o maggiori di 2.  
  
    > [!NOTE]  
    >  Un buffer negativo può inoltre creare un oggetto vuoto **GeometryCollection** istanza.  
  
 Un buffer negativo rimuove tutti i punti racchiusi nella distanza specificata del limite della geometria.  
  
 L'errore tra il buffer calcolato e quello teorico è max (tolleranza, extent * all'1. e-7) in cui tolleranza = distanza \* .001. Per ulteriori informazioni sulle estensioni, vedere [metodo riferimento al tipo di dati geometry](http://msdn.microsoft.com/library/d88e632b-6b2f-4466-a15f-9fbef1a347a7).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-calling-stbuffer-with-parametervalue--0-on-one-dimensional-geometry-instance"></a>A. Chiamata a STBuffer() con parameter_value < 0 in un'istanza di geometria unidimensionale  
 Nell'esempio seguente viene restituita un'istanza `GeometryCollection` vuota:  
  
 `DECLARE @g geometry= 'LINESTRING(3 4, 8 11)';`  
  
 `SELECT @g.STBuffer(-1).ToString();`  
  
### <a name="b-calling-stbuffer-with-parametervalue--0-on-a-polygon-instance"></a>B. Chiamata a STBuffer() con parameter_value < 0 in un'istanza Polygon  
 Nell'esempio seguente viene restituita un'istanza `Polygon` con un buffer negativo:  
  
 `DECLARE @g geometry = 'POLYGON((1 1, 1 5, 5 5, 5 1, 1 1))';`  
  
 `SELECT @g.STBuffer(-1).ToString();`  
  
### <a name="c-calling-stbuffer-with-parametervalue--0-on-a-curvepolygon-instance"></a>C. Chiamata a STBuffer() con parameter_value < 0 in un'istanza CurvePolygon  
 Nell'esempio seguente viene restituita un'istanza `Polygon` con un buffer negativo da un'istanza `CurvePolygon`:  
  
 `DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))';`  
  
 `SELECT @g.STBuffer(-1).ToString();`  
  
> [!NOTE]  
>  Viene restituita un'istanza `Polygon` anziché `CurvePolygon`.  Per restituire un `CurvePolygon` dell'istanza, vedere [BufferWithCurves &#40; tipo di dati geometry &#41;](../../t-sql/spatial-geometry/bufferwithcurves-geometry-data-type.md)  
  
### <a name="d-calling-stbuffer-with-a-negative-parameter-value-that-returns-an-empty-instance"></a>D. Chiamata a STBuffer () con un valore di parametro negativo mediante il quale viene restituita un'istanza vuota  
 Nell'esempio seguente viene illustrato cosa accade quando il *distanza* parametro è uguale a -2 per l'esempio precedente.  
  
 `DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))';`  
  
 `SELECT @g.STBuffer(-2).ToString();`  
  
 Questo **selezionare** istruzione restituisce un`GEOMETRYCOLLECTION EMPTY.`  
  
### <a name="e-calling-stbuffer-with-parametervalue--0"></a>E. Chiamata a STBuffer() con parameter_value = 0  
 Nell'esempio seguente viene restituita una copia dell'istanza `geometry` chiamante:  
  
 `DECLARE @g geometry = 'LINESTRING(3 4, 8 11)';`  
  
 `SELECT @g.STBuffer(0).ToString();`  
  
### <a name="f-calling-stbuffer-with-a-non-zero-parameter-value-that-is-extremely-small"></a>F. Chiamata a STBuffer() con un valore di parametro diverso da zero ed estremamente basso  
 Nell'esempio seguente viene inoltre restituita una copia dell'istanza `geometry` chiamante:  
  
 `DECLARE @g geometry = 'LINESTRING(3 4, 8 11)';`  
  
 `DECLARE @distance float = 1e-20;`  
  
 `SELECT @g.STBuffer(@distance).ToString();`  
  
### <a name="g-calling-stbuffer-with-parametervalue--0"></a>G. Chiamata a STBuffer() con parameter_value > 0  
 Nell'esempio seguente viene restituita un'istanza `Polygon`:  
  
 `DECLARE @g geometry= 'LINESTRING(3 4, 8 11)';`  
  
 `SELECT @g.STBuffer(2).ToString();`  
  
### <a name="h-calling-stbuffer-with-a-string-parameter-value"></a>H. Chiamata a STBuffer() con un valore di parametro stringa  
 Nell'esempio seguente viene restituita la stessa istanza `Polygon` come indicato precedentemente, ma un parametro di stringa viene passato al metodo:  
  
 `DECLARE @g geometry= 'LINESTRING(3 4, 8 11)';`  
  
 `SELECT @g.STBuffer('2').ToString();`  
  
 Nell'esempio seguente verrà generato un errore:  
  
 `DECLARE @g geometry = 'LINESTRING(3 4, 8 11)';`  
  
 `SELECT @g.STBuffer('a').ToString();`  
  
> [!NOTE]  
>  Nei due esempi precedenti è stato passato un valore letterale stringa a `STBuffer()`.  Il primo esempio funziona perché il valore letterale stringa può essere convertito in un valore numerico. Tuttavia, nel secondo esempio viene generata un'eccezione `ArgumentException`.  
  
### <a name="i-calling-stbuffer-on-a-multipoint-instance"></a>I. Chiamata a STBuffer() in un'istanza MultiPoint  
 Nell'esempio seguente vengono restituite due istanze `MultiPolygon` e un'istanza `Polygon`:  
  
 `DECLARE @g geometry = 'MULTIPOINT((1 1),(1 4))';`  
  
 `SELECT @g.STBuffer(1).ToString();`  
  
 `SELECT @g.STBuffer(1.5).ToString();`  
  
 `SELECT @g.STBuffer(1.6).ToString();`  
  
 I primi due **selezionare** istruzioni restituiscono un `MultiPolygon` istanza perché il parametro *distanza* è minore o uguale a 1/2 la distanza tra i due punti (1 1) e (1 4). Il terzo **selezionare** istruzione restituisce un `Polygon` istanza perché le istanze memorizzate nel buffer dei due punti (1 1) e (1 4) si sovrappongono.  
  
## <a name="see-also"></a>Vedere anche  
 [BufferWithTolerance &#40; tipo di dati geometry &#41;](../../t-sql/spatial-geometry/bufferwithtolerance-geometry-data-type.md)   
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


