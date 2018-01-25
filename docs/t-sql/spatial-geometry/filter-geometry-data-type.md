---
title: Filtro (tipo di dati geometry) | Documenti Microsoft
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
- Filter
- Filter_TSQL
- Filter (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: Filter method
ms.assetid: 3d629a39-157e-4159-a3ca-a3c2e0ed4160
caps.latest.revision: "10"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e09f4ac5d6d4ecaf32f6b500aee9a3a50c772c02
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="filter-geometry-data-type"></a>Filter (tipo di dati geometrico)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Un metodo che offre un metodo rapido indice intersezione basato solo per determinare se un **geometry** istanza interseca un'altra **geometry** istanza, supponendo che un indice sia disponibile.
  
Restituisce 1 se un **geometry** istanza interseca potenzialmente un'altra **geometry** istanza. Questo metodo può produrre un risultato falso positivo e il risultato esatto può dipendere dal piano. Restituisce un valore esatto 0 (risultato vero positivo) se è presente alcuna intersezione di **geometry** istanze trovate.
  
In casi in cui un indice non è disponibile o non viene utilizzato il metodo restituirà gli stessi valori **stintersects ()** quando viene chiamato con gli stessi parametri.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.Filter ( other_geometry )  
```  
  
## <a name="arguments"></a>Argomenti  
 *other_geometry*  
 Un altro **geometry** istanza da confrontare con l'istanza in cui viene richiamato Filter().  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo non è deterministico e non è preciso.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato `Filter()` per determinare se due istanze `geometry` si intersecano.  
  
```  
CREATE TABLE sample (id int primary key, g geometry);  
GO  
INSERT INTO sample VALUES  
   (0, geometry::Point(0, 0, 0)),  
   (1, geometry::Point(0, 1, 0)),  
   (2, geometry::Point(0, 2, 0)),  
   (3, geometry::Point(0, 3, 0)),  
   (4, geometry::Point(0, 4, 0));  
  
CREATE SPATIAL INDEX sample_idx ON sample(g)  
WITH (bounding_box = (-8000, -8000, 8000, 8000));  
GO  
SELECT id  
FROM sample   
WHERE g.Filter(geometry::Parse('POLYGON((-1 -1, 1 -1, 1 1, -1 1, -1 -1))')) = 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geometria](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [STIntersects &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stintersects-geometry-data-type.md)  
  
  

