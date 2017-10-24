---
title: NumRings (tipo di dati geography) | Documenti Microsoft
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
- NumRings_TSQL
- NumRings
dev_langs:
- TSQL
helpviewer_keywords:
- NumRings method
ms.assetid: 0e4e4fa2-b608-4cc4-98ba-0845ddb4214c
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3a27cb4953f8ca0ca51ec6d3fdef80ae27dd976a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="numrings-geography-data-type"></a>NumRings (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il numero totale di anelli in un' **poligono** istanza. Nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **geography** digitare, esterna e anelli interni non vengono distinti poiché qualsiasi anello può essere considerato l'anello esterno.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.NumRings ()  
```  
  
## <a name="return-type"></a>Tipo restituito  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **int**  
  
 Tipo CLR restituito: **SqlInt32**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituirà NULL se non è un **poligono** istanza e viene restituito 0 se l'istanza è vuota. Il metodo è preciso.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio viene creata un'istanza `Polygon` con due anelli e viene confermata la presenza di due anelli per l'istanza stessa.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.NumRings();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  

