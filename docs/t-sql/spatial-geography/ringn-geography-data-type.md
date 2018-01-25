---
title: RingN (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- RingN
- RingN_TSQL
dev_langs: TSQL
helpviewer_keywords: RingN method
ms.assetid: 30f47275-2727-4d22-bbec-c0c54bcb3ac2
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e08cc4d2a3359362b0e5bff28c2e18459863b120
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="ringn-geography-data-type"></a>RingN (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce l'anello specificato del **geography** istanza: `1 ≤ n ≤ NumRings()`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.RingN (expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È un **int** espressione compreso tra 1 e il numero di anelli in un' **poligono** istanza.  
  
## <a name="return-value"></a>Valore restituito  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 Se il valore dell'indice dell'anello  **n**  è minore di 1, questo metodo genera un **dell'eccezione ArgumentOutOfRangeException.** Il valore di indice dell'anello deve essere maggiore o uguale a 1 e deve essere minore o uguale al numero restituito da `NumRings()`.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio viene creata un'istanza `Polygon` con due anelli e viene restituito il secondo anello.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.RingN(2).ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [NumRings &#40;tipo di dati geography&#41;](../../t-sql/spatial-geography/numrings-geography-data-type.md)  
  
  
