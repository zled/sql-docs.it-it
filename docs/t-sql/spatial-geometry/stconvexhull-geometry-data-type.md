---
title: STConvexHull (tipo di dati geometry) | Documenti Microsoft
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
- STConvexHull (geometry Data Type)
- STConvexHull_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STConvexHull (geometry Data Type)
ms.assetid: 60a520a6-1a7c-486b-8d91-34401edf6233
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7bfd196565b33604a02a68b1380f676e7e730c45
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stconvexhull-geometry-data-type"></a>STConvexHull (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un oggetto che rappresenta la struttura convessa di una **geometry** istanza.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STConvexHull ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Osservazioni  
 `STConvexHull()`Restituisce il più piccolo poligono convesso che contiene il dato **geometry** istanza. **Punti** o **LineString** collineari restituiranno un'istanza dello stesso tipo dell'input.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato `STConvexHull()` per trovare la struttura convessa di un'istanza `Polygon``geometry` non convessa.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 1 1, 2 2, 2 0, 0 0))', 0);  
SELECT @g.STConvexHull().ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


