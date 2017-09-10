---
title: Punto (tipo di dati geometry) | Documenti Microsoft
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
- Point
- Point_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Point (geometry Data Type)
ms.assetid: 7a2e593a-4d4c-4214-b0c5-02d1ac46bc66
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e153b3bbaf18e6c4b69171e56f2fdae6965396a7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="point-geometry-data-type"></a>Point (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Costruisce un **geometry** istanza che rappresenta un **punto** istanza da valori X e Y e un identificatore SRID.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Point ( X, Y, SRID )  
```  
  
## <a name="arguments"></a>Argomenti  
 *X*  
 È un **float** espressione che rappresenta la coordinata X del **punto** in corso la generazione.  
  
 *Y*  
 È un **float** espressione che rappresenta la coordinata Y del **punto** in corso la generazione.  
  
 *IDENTIFICATORE SRID*  
 È un **int** fanno riferimento a espressioni che rappresenta l'ID (SRID) del **geometry** istanza da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `Point()` per creare un'istanza `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::Point(1, 10, 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geometria statici estesi](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  


