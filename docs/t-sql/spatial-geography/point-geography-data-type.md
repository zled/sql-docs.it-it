---
title: Point (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Point
- Point_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Point method
- Point (geography Data Type)
ms.assetid: 0dc6f422-7aae-4016-b7f4-3289fa8f989c
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7cefb6e199bbd4617b1fc2f6f71d9bb3997445dc
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="point-geography-data-type"></a>Point (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Costruisce un **geography** istanza che rappresenta un **punto** istanza da cui i valori di latitudine e longitudine e un SRID di ID di riferimento spaziale.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Point ( Lat, Long, SRID )  
```  
  
## <a name="arguments"></a>Argomenti  
 *LAT*  
 È un **float** espressione che rappresenta la coordinata x del **punto** in corso la generazione.  
  
 *Long*  
 È un **float** espressione che rappresenta la coordinata y del **punto** in corso la generazione. Per ulteriori informazioni sui valori di longitudine e latitudine validi, vedere [punto](../../relational-databases/spatial/point.md).  
  
 *IDENTIFICATORE SRID*  
 È un **int** che rappresenta l'identificatore SRID dell'espressione di **geography** istanza da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
> [!NOTE]  
>  Gli argomenti del metodo Point (tipo di dati geography) hanno coordinate inverse rispetto a WKT.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `Point()` per creare un'istanza `geography`.  
  
```  
DECLARE @g geography;   
SET @g = geography::Point(47.65100, -122.34900, 4326)  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geografia statici estesi](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  

