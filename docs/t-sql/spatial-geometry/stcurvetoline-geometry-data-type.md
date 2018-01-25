---
title: STCurveToLine (tipo di dati geometry) | Documenti Microsoft
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
dev_langs: TSQL
helpviewer_keywords: STCurveToLine method (geometry)
ms.assetid: abc80b32-4152-4e10-b816-798b901e0ac5
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d5950ba5609fdd34008c051166f089cf3433890d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="stcurvetoline-geometry-data-type"></a>STCurveToLine (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Restituisce un'approssimazione poligonale di un' **geometry** istanza contenente i segmenti di arco circolare.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STCurveToLine ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Osservazioni  
 Restituisce un oggetto vuoto **GeometryCollection**istanza per vuoto **geometry** istanza variabili e restituisce **NULL** per non inizializzata **geometry** variabili.  
  
 L'approssimazione poligonale restituita dal metodo dipende il **geometry** istanza che viene utilizzata per chiamare il metodo:  
  
-   Restituisce un **LineString** istanza per un **CircularString** o **CompoundCurve** istanza.  
  
-   Restituisce un **poligono** istanza per un **CurvePolygon** istanza.  
  
-   Restituisce una copia del **geometry** istanza, se tale istanza non è un **CircularString**, **CompoundCurve**, o **CurvePolygon** istanza . Ad esempio, il `STCurveToLine` metodo restituisce un **punto** istanza per un **geometry** che è un **punto** istanza.  
  
 A differenza della specifica SQL/MM, il `STCurveToLine` metodo non utilizza i valori di coordinata z per calcolare l'approssimazione poligonale. Il metodo ignora qualsiasi coordinata z di valori presenti nel chiamante **geometry** istanza.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-an-uninitialized-geometry-variable-and-empty-instance"></a>A. Utilizzo di una variabile di geometria non inizializzata e di un'istanza vuota  
 Nell'esempio seguente, il primo **selezionare** istruzione utilizza l'oggetto non inizializzato **geometry** istanza per chiamare il `STCurveToLine` (metodo), mentre la seconda **selezionare** istruzione utilizza un oggetto vuoto **geometry** istanza. Di conseguenza, il metodo restituisce **NULL** alla prima istruzione e una **GeometryCollection** insieme per la seconda istruzione.  
  
```
 DECLARE @g geometry; 
 SET @g = @g.STCurveToLine(); 
 SELECT @g.STGeometryType(); 
 SET @g = geometry::Parse('LINESTRING EMPTY'); 
 SELECT @g.STGeometryType();
 ```  
  
### <a name="b-using-a-linestring-instance"></a>B. Utilizzo di un'istanza LineString  
 Il **selezionare** istruzione nell'esempio seguente viene utilizzato un **LineString** istanza per chiamare il metodo STCurveToLine. Di conseguenza, il metodo restituisce un **LineString** istanza.  
  
```
 DECLARE @g geometry; 
 SET @g = geometry::Parse('LINESTRING(1 3, 5 5, 4 3, 1 3)'); 
 SET @g = @g.STCurveToLine(); 
 SELECT @g.STGeometryType();
 ```  
  
### <a name="c-using-a-circularstring-instance"></a>C. Utilizzo di un'istanza CircularString  
 Il primo **selezionare** istruzione nell'esempio seguente viene utilizzato un **CircularString** istanza per chiamare il metodo STCurveToLine. Di conseguenza, il metodo restituisce un **LineString** istanza. Questo **selezionare** istruzione confronta inoltre le lunghezze delle due istanze sono pressoché identiche.  Infine, il secondo **selezionare** l'istruzione restituisce il numero di punti per ogni istanza.  Restituisce solo 5 punti per il **CircularString** istanza, ma 65 per il **LineString**istanza.  
  
```
 DECLARE @g1 geometry, @g2 geometry; 
 SET @g1 = geometry::Parse('CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0)'); 
 SET @g2 = @g1.STCurveToLine(); 
 SELECT @g1.STGeometryType() AS [G1 Type], @g2.STGeometryType() AS [G2 Type], @g1.STLength() AS [G1 Perimeter], @g2.STLength() AS [G2 Perimeter], @g2.ToString() AS [G2 Def]; 
 SELECT @g1.STNumPoints(), @g2.STNumPoints();
 ```  
  
### <a name="d-using-a-curvepolygon-instance"></a>D. Utilizzo di un'istanza CurvePolygon  
 Il **selezionare** istruzione nell'esempio seguente viene utilizzato un **CurvePolygon** istanza per chiamare il metodo STCurveToLine. Di conseguenza, il metodo restituisce un **poligono** istanza.  
  
```
 DECLARE @g1 geometry, @g2 geometry; 
 SET @g1 = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0))'); 
 SET @g2 = @g1.STCurveToLine(); 
 SELECT @g1.STGeometryType() AS [G1 Type], @g2.STGeometryType() AS [G2 Type];
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica dei tipi di dati spaziali](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [STLength &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stlength-geometry-data-type.md)   
 [STNumPoints &#40;geometry Data Type&#41; (STNumPoints &#40;tipo di dati geometry&#41;)](../../t-sql/spatial-geometry/stnumpoints-geometry-data-type.md)   
 [STGeometryType &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)  
  
  

