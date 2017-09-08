---
title: STGeometryN (tipo di dati geography) | Documenti Microsoft
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
- STGeometryN (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryN method
ms.assetid: 53755f69-cd50-475b-b3b8-a1a9157cf03a
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d5d11dc77ce692543068cba6739ef982bc8264c8
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stgeometryn-geography-data-type"></a>STGeometryN (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce un oggetto specificato **geography** elemento in un **GeometryCollection** o uno dei relativi sottotipi. Quando STGeometryN() viene utilizzato un sottotipo di un **GeometryCollection**, ad esempio **MultiPoint** o **MultiLineString**, questo metodo restituisce il **geography**  istanza se chiamato con N = 1.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STGeometryN ( expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È un **int** espressione compreso tra 1 e il numero di **geography** istanze di **GeometryCollection**.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituisce null se il parametro è maggiore del risultato di [stnumgeometries ()](../../t-sql/spatial-geography/stnumgeometries-geography-data-type.md) e genererà un **ArgumentOutOfRangeException** se il *espressione* il parametro è minore di 1.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creato un `MultiPoint``geography` istanza e viene utilizzato `STGeometryN()` per trovare la seconda `geography` istanza il **GeometryCollection**.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STGeometryN(2).ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geografia](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
