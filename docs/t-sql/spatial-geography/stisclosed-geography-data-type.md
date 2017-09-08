---
title: STIsClosed (tipo di dati geography) | Documenti Microsoft
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
- STIsClosed (geography Data Type)
- STIsClosed_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STIsClosed method
ms.assetid: eba1643f-07c4-4500-8643-b7e90f908147
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5926dd4be979793fc164e84752a4b456e42565a3
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stisclosed-geography-data-type"></a>STIsClosed (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce 1 se i punti iniziale e finale di dato **geography** sono gli stessi dell'istanza. Restituisce 1 per **geography** tipi di raccolta se ogni contenuti **geography** istanza è chiusa. Restituisce 0 se l'istanza non è chiusa.  
  
 Questo **geography** metodo supportata dal tipo di dati **FullGlobe** istanze o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STIsClosed ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituisce 0 se qualche figura di un **geography** istanza sono punti, o se l'istanza è vuota.  
  
 Questo metodo restituisce true se un **FullGlobe** istanza è un **poligono** o di altro tipo di istanza.  
  
 Tutti **poligono** istanze sono considerate chiuse.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `Polygon` e viene utilizzato `STIsClosed()` per verificare se l'istanza `Polygon` è chiusa.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STIsClosed();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geografia](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
