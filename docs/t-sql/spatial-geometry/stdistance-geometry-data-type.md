---
title: STDistance (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STDistance_TSQL
- STDistance (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDistance (geometry Data Type)
ms.assetid: ac815bc7-5342-4cc4-af40-c80a1c4c8b68
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4e6219da2655b6e190905166e6d650754381ae43
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="stdistance-geometry-data-type"></a>STDistance (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce la distanza più breve tra un punto in un **geometry** istanza e un punto in un altro **geometry** istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STDistance ( other_geometry )  
```  
  
## <a name="arguments"></a>Argomenti  
 *other_geometry*  
 Un altro **geometry** istanza da cui misurare la distanza tra l'istanza sulla quale `STDistance()` viene richiamato. Se *other_geometry* è un set vuoto, `STDistance()` restituisce null.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **float**  
  
 Tipo CLR restituito: **SqlDouble**  
  
## <a name="remarks"></a>Osservazioni  
 `STDistance()`Restituisce sempre null se gli ID di riferimento spaziale (SRID) del **geometry** istanze non corrispondono.  
  
## <a name="examples"></a>Esempi  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 2 0, 2 2, 0 2, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POINT(10 10)', 0);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli indici spaziali](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
