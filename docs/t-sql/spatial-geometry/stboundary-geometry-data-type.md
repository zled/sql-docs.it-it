---
title: STBoundary (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- STBoundary (geometry Data Type)
- STBoundary_TSQL
dev_langs: TSQL
helpviewer_keywords: STBoundary (geometry Data Type)
ms.assetid: f0551674-e6e8-4926-9038-df03f2c807d7
caps.latest.revision: "22"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8af92a892be08f0fe51c4cbea77eee4147f235ba
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="stboundary-geometry-data-type"></a>STBoundary (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il limite di un **geometry** istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STBoundary ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Osservazioni  
 `STBoundary()`Restituisce un oggetto vuoto **GeometryCollection** quando gli endpoint per un **LineString**, **CircularString**, o **CompoundCurve** istanza sono gli stessi.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-stboundary-on-a-linestring-instance-with-different-endpoints"></a>A. Utilizzo di STBoundary() in un'istanza LineString con endpoint diversi  
 Nell'esempio seguente viene creato un `LineString``geometry` istanza. `STBoundary()`Restituisce il limite del `LineString`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, 2 0)', 0);  
SELECT @g.STBoundary().ToString();  
```  
  
### <a name="b-using-stboundary-on-a-linestring-instance-with-the-same-endpoints"></a>B. Utilizzo di STBoundary() in un'istanza LineString con gli stessi endpoint  
 Nell'esempio seguente viene creata un'istanza `LineString` valida con gli stessi endpoint. Tramite `STBoundary()` viene restituita un'istanza `GeometryCollection` vuota.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, -2 2, 0 0)', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
### <a name="c-using-stboundary-on-a-curvepolygon-instance"></a>C. Utilizzo di STBoundary() in un'istanza CurvePolygon  
 Nell'esempio seguente viene utilizzato `STBoundary()` in un'istanza `CurvePolygon` vuota. Tramite `STBoundary()` viene restituita un'istanza `CircularString`.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('CURVEPOLYGON(CIRCULARSTRING(0 0, 2 2, 0 2, -2 2, 0 0))', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
