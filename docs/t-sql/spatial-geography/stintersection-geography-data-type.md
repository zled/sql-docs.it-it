---
title: STIntersection (tipo di dati geography) | Documenti Microsoft
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
- STIntersection_TSQL
- STIntersection (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIntersection method
ms.assetid: 7e09468f-499f-4a38-ba4b-bb30b8821e3b
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 44d5a38e914ec6ea485262e44048f5fe79f317c6
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stintersection-geography-data-type"></a>STIntersection (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce un oggetto che rappresenta i punti in cui un **geography** istanza interseca un'altra **geography** istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STIntersection ( other_geography )  
```  
  
## <a name="arguments"></a>Argomenti  
 *other_geography*  
 Un altro **geography** istanza da confrontare con l'istanza in cui viene richiamato stintersection ().  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 Viene restituita l'intersezione di due istanze geografiche  
  
 Stintersection () restituisce sempre null se gli identificatori di riferimento spaziale (SRID) del **geography** istanze non corrispondono.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta le istanze spaziali di dimensioni maggiori di un emisfero. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]può includere **FullGlobe** istanze nel set di risultati possibili restituito nel server.  
  
 Il risultato può contenere segmenti di arco circolare solo se le istanze di input contengono segmenti di arco circolare.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-computing-the-intersection-of-a-polygon-and-a-linestring"></a>A. Calcolo dell'intersezione di Polygon e LineString  
 Nell'esempio seguente viene utilizzato `STIntersection()` per calcolare l'intersezione tra `Polygon` e `LineString`.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STIntersection(@h).ToString();  
```  
  
### <a name="b-computing-the-intersection-of-a-polygon-and-a-curvepolygon"></a>B. Calcolo dell'intersezione di Polygon e CurvePolygon  
 Nell'esempio seguente viene restituita un'istanza che contiene un segmento di arco circolare.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('CURVEPOLYGON(CIRCULARSTRING(-122.351 47.656, -122.341 47.656, -122.341 47.661, -122.351 47.661, -122.351 47.656))', 4326);  
SELECT @g.STIntersection(@h).ToString();  
```  
  
### <a name="c-computing-the-symmetric-difference-with-fullglobe"></a>C. Calcolo della differenza simmetrica con FullGlobe  
 Nell'esempio seguente viene confrontata la differenza simmetrica di `Polygon` a `FullGlobe`.  
  
```  
DECLARE @g geography = 'POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
SELECT @g.STIntersection('FULLGLOBE').ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geografia](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

