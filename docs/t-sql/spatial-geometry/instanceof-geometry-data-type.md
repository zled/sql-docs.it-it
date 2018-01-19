---
title: InstanceOf (tipo di dati geometry) | Documenti Microsoft
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
- InstanceOf
- InstanceOf_TSQL
dev_langs: TSQL
helpviewer_keywords: InstanceOf (geometry Data Type)
ms.assetid: fdea1248-29a4-4bab-a60d-a1b359b5e109
caps.latest.revision: "26"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 524e084112d2b9a8b7fe51188d50e9f518aba488
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="instanceof-geometry-data-type"></a>InstanceOf (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Un metodo che verifica se il **geometry** istanza corrisponde al tipo specificato. Restituisce 1 se il tipo di un **geometry** istanza corrisponde al tipo specificato, o se il tipo specificato è un predecessore del tipo di istanza; in caso contrario, restituisce 0.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.InstanceOf (geometry_type )  
```  
  
## <a name="arguments"></a>Argomenti  
 *geometry_type*  
 È un **nvarchar (4000)** specificando uno dei 15 tipi esposti nella stringa di **geometry** gerarchia dei tipi.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Osservazioni  
 L'input per il metodo deve essere uno dei seguenti: **Geometry**, **punto**, **curva**, **LineString**,  **CircularString**, **CompoundCurve**, **area**, **poligono**, **CurvePolygon**, **GeometryCollection**, **MultiSurface**, **MultiPolygon**, **MultiCurve**, **MultiLineString**, e **MultiPoint**. Questo metodo genera un **ArgumentException** se tutte le altre stringhe vengono utilizzate per l'input.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `MultiPoint` e viene utilizzato `InstanceOf()` per verificare se l'istanza è di tipo `GeometryCollection`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT(0 0, 13.5 2, 7 19)', 0);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geometria](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

