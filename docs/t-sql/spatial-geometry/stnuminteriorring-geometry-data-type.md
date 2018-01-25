---
title: STNumInteriorRing (tipo di dati geometry) | Documenti Microsoft
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
f1_keywords:
- STNumInteriorRing_TSQL
- STNumInteriorRing (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: STNumInteriorRing (geometry Data Type)
ms.assetid: 48e78948-5b14-41dd-85d1-169bba1c4195
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5af0f25fbab350aa89605c456c573113230680e3
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="stnuminteriorring-geometry-data-type"></a>STNumInteriorRing (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce il numero di anelli interni di un **Polygongeometry** istanza.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STNumInteriorRing ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **int**  
  
 Tipo CLR restituito: **SqlInt32**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituisce null se il **geometry** istanza non è un poligono.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `Polygon` e viene utilizzato `STNumInteriorRing()` per trovare il numero di anelli interni dell'istanza.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STNumInteriorRing();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

