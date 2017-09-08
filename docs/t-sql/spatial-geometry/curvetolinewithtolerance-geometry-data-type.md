---
title: CurveToLineWithTolerance (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- CurveToLineWithTolerance method (geometry)
ms.assetid: 96871075-1998-4cd9-86b1-3fc55577aee4
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5120f9c27e6157fd2f19c598ad984e1a3543db94
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="curvetolinewithtolerance-geometry-data-type"></a>CurveToLineWithTolerance (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Restituisce un'approssimazione poligonale di un' **geometry** istanza contenente i segmenti di arco circolare.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.CurveToLineWithTolerance ( tolerance, relative )  
```  
  
## <a name="arguments"></a>Argomenti  
 *tolleranza di errore*  
 È un **doppie** espressione che definisce l'errore massimo tra il segmento di arco circolare originale e l'approssimazione lineare.  
  
 *relativo*  
 È un **bool** espressione che indica se utilizzare un valore massimo relativo per la deviazione. Quando il parametro relative viene impostato su false (0), viene impostato un valore massimo assoluto per la deviazione che può presentare un'approssimazione lineare. Quando il parametro relative viene impostato su true (1), la tolleranza e viene calcolata come prodotto tra il parametro della tolleranza e il diametro del rettangolo di selezione per l'oggetto spaziale.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="exceptions"></a>Eccezioni  
 L'impostazione della tolleranza <= 0 genera un'eccezione `ArgumentOutOfRange`.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo può specificare la tolleranza di errore per i risultanti **LineString**.  
  
 Nella tabella seguente viene illustrato il tipo di istanza restituito da `CurveToLineWithTolerance()` per vari tipi.  
  
|Tipo di istanza di chiamata|Tipo spaziale restituito|  
|----------------------------|---------------------------|  
|Istanza di geometria vuota|Vuoto **GeometryCollection** istanza|  
|**Punto** e **MultiPoint**|**Punto** istanza|  
|**MultiPoint**|**Punto** o **MultiPoint** istanza|  
|**CircularString**, **CompoundCurve**, o **LineString**|**LineString** istanza|  
|**MultiLineString**|**LineString** o **MultiLineString** istanza|  
|**CurvePolygon** e **poligono**|**Poligono** istanza|  
|**MultiPolygon**|**Poligono** o **MultiPolygon** istanza|  
|**GeometryCollection** con una singola istanza che non contiene un segmento di arco circolare|L'istanza contenuta nel **GeometryCollection** determina il tipo di istanza restituita.|  
|**GeometryCollection** con un'istanza di segmento di arco circolare unidimensionale singolo (**CircularString**, **CompoundCurve**)|**LineString** istanza|  
|**GeometryCollection** con un'istanza di segmento di arco circolare bidimensionale singolo (**CurvePolygon**)|**Poligono** istanza|  
|**GeometryCollection** con più istanze unidimensionali|**MultiLineString** istanza|  
|**GeometryCollection** con più di due istanze bidimensionali|**MultiPolygon** istanza|  
|**GeometryCollection** con più istanze di dimensioni diverse|**GeometryCollection** istanza|  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-different-tolerance-values-on-a-circularstring-instance"></a>A. Utilizzo di valori di tolleranza diversi in un'istanza CircularString  
 Nell'esempio seguente viene illustrato come l'impostazione della tolleranza sul `LineString`istanza restituita da un `CircularString` istanza:  
  
 `DECLARE @g geometry;`  
  
 `SET @g = geometry::Parse('CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)');`  
  
 `SELECT @g.CurveToLineWithTolerance(0.1,0).STNumPoints(), @g.CurveToLineWithTolerance(0.01, 0).STNumPoints();`  
  
### <a name="b-using-the-method-on-a-multilinestring-instance-containing-one-linestring"></a>B. Utilizzo del metodo in un'istanza MultiLineString che contiene un'istanza LineString  
 Nell'esempio seguente viene illustrato ciò che viene restituito da un'istanza `MultiLineString` che contiene una sola istanza `LineString`:  
  
 `DECLARE @g geometry;`  
  
 `SET @g = geometry::Parse('MULTILINESTRING((1 3, 4 8, 6 9))');`  
  
 `SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();`  
  
### <a name="c-using-the-method-on-a-multilinestring-instance-containing-multiple-linestrings"></a>C. Utilizzo del metodo in un'istanza MultiLineString che contiene più istanze LineString  
 Nell'esempio seguente viene illustrato ciò che viene restituito da un'istanza `MultiLineString` che contiene più di un'istanza `LineString`:  
  
 `DECLARE @g geometry;`  
  
 `SET @g = geometry::Parse('MULTILINESTRING((1 3, 4 8, 6 9),(4 4, 9 18))');`  
  
 `SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();`  
  
### <a name="d-setting-relative-to-true-for-an-invoking-curvepolygon-instance"></a>D. Impostazione del parametro relative su true per un'istanza CurvePolygon di chiamata  
 Nell'esempio seguente viene utilizzato un `CurvePolygon` istanza chiamare `CurveToLineWithTolerance()` con *relativo* impostato su true:  
  
 `DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))';`  
  
 `SELECT @g.CurveToLineWithTolerance(.5,1).ToString();`  
  
### <a name="e-using-the-method-on-a-geometrycollection-instance"></a>E. Utilizzo del metodo in un'istanza GeometryCollection  
 Nell'esempio seguente viene chiamato `CurveToLineWithTolerance()` on a `GeometryCollection` che contiene un'istanza `CurvePolygon` bidimensionale e un'istanza `CircularString` unidimensionale. `CurveToLineWithTolerance()` converte entrambi i tipi di segmento di arco circolare in tipi di segmento lineare e li restituisce in un tipo `GeometryCollection`.  
  
 `DECLARE @g geometry;`  
  
 `SET @g = geometry::Parse('GEOMETRYCOLLECTION(CURVEPOLYGON( COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 0 2))), CIRCULARSTRING(4 4, 8 6, 9 5))');`  
  
 `SELECT @g.CurveToLineWithTolerance(0.1,0).STNumPoints(), @g.CurveToLineWithTolerance(0.1, 0).ToString();`  
  
## <a name="see-also"></a>Vedere anche  
 [CurveToLineWithTolerance &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/curvetolinewithtolerance-geography-data-type.md)   
 [STCurveToLine &#40; tipo di dati geometry &#41;](../../t-sql/spatial-geometry/stcurvetoline-geometry-data-type.md)  
  
  


