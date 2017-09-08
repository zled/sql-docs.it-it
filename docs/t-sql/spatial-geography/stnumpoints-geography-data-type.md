---
title: STNumPoints (tipo di dati geography) | Documenti Microsoft
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
- STNumPoints (geography Data Type)
- STNumPoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumPoints method
ms.assetid: 25ff7ad1-ba5f-4cfb-816a-59255ac1591d
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 803e631cb1e0250ebedd28a97afe4e20476396cf
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stnumpoints-geography-data-type"></a>STNumPoints (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il numero totale di punti in ognuna delle figure di un **geography** istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STNumPoints ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **int**  
  
 Tipo CLR restituito: **SqlInt32**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo conta i punti nella descrizione di un **geography** istanza. Vengono contati anche i punti duplicati; tuttavia, i punti di connessione tra i segmenti vengono contati una sola volta. Se questa istanza è una raccolta, il metodo restituisce il numero totale di punti nella raccolta.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-retrieving-the-total-number-of-points-in-a-linestring"></a>A. Recupero del numero complessivo di punti in LineString  
 Nell'esempio seguente viene creata un'istanza `LineString` e viene utilizzato `STNumPoints()` per determinare il numero di punti utilizzati nella descrizione dell'istanza.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STNumPoints();  
```  
  
### <a name="b-retrieving-the-total-number-of-points-in-a-geometrycollection"></a>B. Recupero del numero complessivo di punti in GeometryCollection  
 Nell'esempio seguente viene restituita la somma dei punti di tutti gli elementi in `GeometryCollection`.  
  
```  
DECLARE @g geography = 'GEOMETRYCOLLECTION(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)  
    ,CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)))';  
SELECT @g.STNumPoints();  
```  
  
### <a name="c-returning-the-number-of-points-in-a-compoundcurve"></a>C. Restituzione del numero di punti in CompoundCurve  
 Nell'esempio seguente viene restituito il numero di punti in un'istanza CompoundCurve. La query restituisce 5 anziché 6 perché in STNumPoints() i punti di connessione tra i segmenti vengono contati una sola volta.  
  
 `DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658),( -122.348 47.658, -121.56 48.12, -122.358 47.653))'`  
  
 `SELECT @g.STNumPoints();`  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geografia](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
