---
title: STIsClosed (tipo di dati geometry) | Documenti Microsoft
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
- STIsClosed_TSQL
- STIsClosed (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsClosed (geometry Data Type)
ms.assetid: 14edbb22-df7b-4b8a-b16c-ac477a5d32c1
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1fca12de9a05ff424532fa488fda7a306b8a9c37
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stisclosed-geometry-data-type"></a>STIsClosed (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce 1 se i punti iniziale e finale di dato **geometry** sono gli stessi dell'istanza. Restituisce 1 per **geometrycollection** tipi se ognuno contenuto **geometry** istanza è chiusa. Restituisce 0 se l'istanza non è chiusa.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STIsClosed ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituisce 0 se eventuali cifre di un **geometry** istanza sono punti, o se l'istanza è vuota.  
  
 Tutti **poligono** istanze sono considerate chiuse.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `LineString` e viene utilizzato `STIsClosed()` per verificare se l'istanza `LineString` è chiusa.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STIsClosed();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


