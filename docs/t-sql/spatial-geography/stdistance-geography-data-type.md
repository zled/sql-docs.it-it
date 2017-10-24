---
title: STDistance (tipo di dati geography) | Documenti Microsoft
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
- STDistance_TSQL
- STDistance (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDistance method
ms.assetid: 063d8722-e019-4d3d-8fcf-dbf5325823e7
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f79891d789938a6f4615c0e4be9cc3ba5d361f1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stdistance-geography-data-type"></a>STDistance (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce la distanza più breve tra un punto in un **geography** istanza e un punto in un altro **geography** istanza.  
  
> [!NOTE]  
>  `STDistance()`Restituisce il più breve **LineString** tra due tipi di geografia. È un'approssimazione della distanza geodetica. La deviazione di `STDistance()` in modelli di terra comuni dalla distanza Geodetica esatta non deve superare. 25%. In tal modo si evitano confusioni sulle differenze minime tra lunghezza e distanza nei tipi geodetici.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STDistance ( other_geography )  
```  
  
## <a name="arguments"></a>Argomenti  
 *other_geography*  
 Un altro **geography** istanza da cui misurare la distanza tra l'istanza in cui viene richiamato stdistance (). Se *other_geography* stdistance () è vuota, restituisce null.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **float**  
  
 Tipo CLR restituito: **SqlDouble**  
  
## <a name="remarks"></a>Osservazioni  
 Stdistance () restituisce sempre null se gli ID di riferimento spaziale (SRID) del **geography** istanze non corrispondono.  
  
> [!NOTE]  
>  Metodi di **geography** tipo di dati che calcolano un'area o una distanza restituiranno risultati diversi in base all'identificatore SRID dell'istanza utilizzato nel metodo.   Per ulteriori informazioni sugli identificatori SRID, vedere [gli identificatori di riferimento spaziale &#40; Identificatori SRID &#41; ](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene individuata la distanza tra due **geography** istanze.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SET @h = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geografia](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

