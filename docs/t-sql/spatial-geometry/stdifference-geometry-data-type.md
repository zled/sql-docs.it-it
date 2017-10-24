---
title: STDifference (tipo di dati geometry) | Documenti Microsoft
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
- STDifference_TSQL
- STDifference (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDifference (geometry Data Type)
ms.assetid: 737f39bb-8750-4ffb-8594-23febc2f1075
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7c6b79813c903e5c5541b2aab8d09ba1858f28f0
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stdifference-geometry-data-type"></a>STDifference (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un oggetto che rappresenta il punto impostato da uno **geometry** istanza che si trovano all'interno di altra **geometry** istanza.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STDifference ( other_geometry )  
```  
  
## <a name="arguments"></a>Argomenti  
 *other_geometry*  
 Un altro **geometry** istanza che indica i punti da rimuovere dall'istanza in cui `STDifference()` viene richiamato.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituisce sempre null se gli ID di riferimento spaziale (SRID) del **geometry** istanze non corrispondono.   Il risultato può contenere segmenti di arco circolare solo se le istanze di input contengono segmenti di arco circolare.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-computing-the-difference-between-two-polygon-instances"></a>A. Calcolo della differenza tra due istanze Polygon  
 Nell'esempio seguente viene utilizzato `STDifference()` per calcolare la differenza tra due poligoni.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 2 2, 2 0, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STDifference(@h).ToString();  
```  
  
### <a name="b-invoking-stdifference-on-a-curvepolygon-instance"></a>B. Chiamata di STDifference() in un'istanza CurvePolygon  
 Nell'esempio seguente viene utilizzato STDifference() in un'istanza CurvePolygon.  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON ((1 -1, 5 -1, 5 3, 1 3, 1 -1))';  
 -- Note the different results returned by the two SELECT statements  
 SELECT @h.STDifference(@g).ToString(), @g.STDifference(@h).ToString();
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


