---
title: STIsRing (tipo di dati geometry) | Documenti Microsoft
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
- STIsRing_TSQL
- STIsRing (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsRing (geometry Data Type)
ms.assetid: ea0063be-1c74-4cc4-ac6f-b65321ddfa54
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3417f5da487ea7de5d7c51820316dae3caf8bb0e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stisring-geometry-data-type"></a>STIsRing (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce 1 se un **geometry** istanza soddisfa i requisiti seguenti:
-   Si tratta di un **LineString** istanza.  
-   È chiusa.  
-   È semplice.  
-   Restituisce 0 se il **LineString** istanza non soddisfa i requisiti.  

 Per un **geometry** istanza sia chiusa e semplice, entrambi [stisclosed ()](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md) e [stissimple ()](../../t-sql/spatial-geometry/stissimple-geometry-data-type.md) devono restituire 1 quando sono richiamati sull'istanza. Per determinare il tipo di istanza di un **geometry**, utilizzare [stgeometrytype ()](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STIsRing ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituisce null se l'istanza non è un **LineString**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `LineString` e viene utilizzato `STIsRing()` per verificare se l'istanza è un anello.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0, 0 0)', 0);  
SELECT @g.STIsRing();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [STIsClosed &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md)   
 [STGeometryType &#40; tipo di dati geometry &#41;](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)   
 [STIsSimple &#40; tipo di dati geometry &#41;](../../t-sql/spatial-geometry/stissimple-geometry-data-type.md)   
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


