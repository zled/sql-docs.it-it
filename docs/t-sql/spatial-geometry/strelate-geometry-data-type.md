---
title: STRelate (tipo di dati geometry) | Documenti Microsoft
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
- STRelate (geometry Data Type)
- STRelate_TSQL
dev_langs: TSQL
helpviewer_keywords: STRelate (geometry Data Type)
ms.assetid: 9dcb5f58-35ab-4bb3-86ee-2d29eefba6d3
caps.latest.revision: "19"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bbda0b7d41dcf979afd23dba651b20513ea1b193
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="strelate-geometry-data-type"></a>STRelate (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce 1 se un **geometry** istanza è correlata a un'altra **geometry** istanza, in cui la relazione è definita da un valore di una matrice di modello Dimensionally Extended 9 Intersection Model (DE-9IM); in caso contrario , restituisce 0.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STRelate ( other_geometry, intersection_pattern_matrix )  
```  
  
## <a name="arguments"></a>Argomenti  
 *other_geometry*  
 Un altro **geometry** istanza da confrontare con l'istanza sulla quale `STRelate()` viene richiamato.  
  
 *intersection_pattern_matrix*  
 È una stringa di tipo **nchar(9)** codifica valori accettabili per il dispositivo a matrice del modello DE-9IM tra i due **geometry** istanze.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituisce sempre null se gli ID di riferimento spaziale (SRID) del **geometry** istanze non corrispondono. Questo metodo genererà un' **ArgumentException** se la matrice non è corretta.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente usa `STRelate()` per verificare se due **geometry** istanze spaziali non contiguo utilizzando un modello DE-9IM esplicito.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 2 0, 4 2)', 0);  
SET @h = geometry::STGeomFromText('POINT(5 5)', 0);  
SELECT @g.STRelate(@h, 'FF*FF****');  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
