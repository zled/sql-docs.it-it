---
title: STIntersects (tipo di dati geometry) | Documenti Microsoft
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
- STIntersects (geometry Data Type)
- STIntersects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STIntersects (geometry Data Type)
ms.assetid: 7c18f5be-5a29-422e-8ca7-d8a5f38e03f5
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: feef169a9108efd3b76afd4fe1d5b26b904a81ab
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stintersects-geometry-data-type"></a>STIntersects (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce 1 se un **geometry** istanza interseca un'altra **geometry** istanza. In caso contrario, restituisce 0.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STIntersects ( other_geometry )  
```  
  
## <a name="arguments"></a>Argomenti  
 *other_geometry*  
 Un altro **geometry** istanza da confrontare con l'istanza sulla quale `STIntersects()` viene richiamato.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituisce sempre null se gli ID di riferimento spaziale (SRID) del **geometry** istanze non corrispondono.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato `STIntersects()` per determinare se due istanze `geometry` si intersecano.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 2 0, 4 2)', 0);  
SET @h = geometry::STGeomFromText('POINT(1 1)', 0);  
SELECT @g.STIntersects(@h);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli indici spaziali](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


