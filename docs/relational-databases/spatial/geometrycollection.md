---
title: "GeometryCollection | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-spatial"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sottotipo di geometria GeomCollection [SQL Server]"
  - "sottotipi di geometria [SQL Server]"
ms.assetid: 4445c0d9-a66b-4d7c-88e4-a66fa6f7d9fd
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# GeometryCollection
  **GeometryCollection** è una raccolta di zero o più istanze di tipo **geometry** o **geography**. **GeometryCollection** può essere vuoto.  
  
## Istanze GeometryCollection  
  
### Istanze accettate  
 Per poter essere accettata, un'istanza **GeometryCollection** deve essere un'istanza **GeometryCollection** vuota oppure tutte le istanze che comprendono l'istanza **GeometryCollection** devono essere istanze accettate. Nell'esempio seguente vengono illustrate le istanze accettate.  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
 Nell'esempio seguente viene generata un'eccezione `System.FormatException`, poiché l'istanza **LinesString** nell'istanza **GeometryCollection** non è accettata.  
  
```  
DECLARE @g geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1), POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
### Istanze valide  
 Un'istanza **GeometryCollection** è valida se tutte le istanze che comprendono l'istanza **GeometryCollection** sono valide. Nell'esempio seguente vengono indicate tre istanze **GeometryCollection** valide e un'istanza non valida.  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g4 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, 1 -5, -5 5, -5 -1, -1 -1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` non è valida, poiché l'istanza **Polygon** nell'istanza **GeometryCollection** non è valida.  
  
 Per altre informazioni sulle istanze accettate e valide, vedere [Point](../../relational-databases/spatial/point.md), [MultiPoint](../../relational-databases/spatial/multipoint.md), [LineString](../../relational-databases/spatial/linestring.md), [MultiLineString](../../relational-databases/spatial/multilinestring.md), [Polygon](../../relational-databases/spatial/polygon.md) e [MultiPolygon](../../relational-databases/spatial/multipolygon.md).  
  
## Esempi  
 Nell'esempio seguente viene creata un'istanza di un `geometry``GeometryCollection` con i valori Z in SRID 1 in cui sono incluse le istanze `Point` e `Polygon`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION(POINT(3 3 1), POLYGON((0 0 2, 1 10 3, 1 0 4, 0 0 2)))', 1);  
```  
  
## Vedere anche  
 [Dati spaziali &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  