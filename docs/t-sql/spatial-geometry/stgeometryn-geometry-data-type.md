---
title: STGeometryN (tipo di dati geometry) | Documenti Microsoft
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
- STGeometryN_TSQL
- STGeometryN (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: STGeometryN (geometry Data Type)
ms.assetid: 348c7047-3442-4590-8879-fe841e79058c
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ac3ec091d949bec3f2f02a2e2cfd472d2e70aec9
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="stgeometryn-geometry-data-type"></a>STGeometryN (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce una geometria specificata in un **raccolta di geometrie**.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STGeometryN ( expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È un **int** espressione compreso tra 1 e il numero di **geometry** istanze di **geometrycollection**.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituisce **null** se il parametro è maggiore del risultato di `STNumGeometries()` e genererà un **ArgumentOutOfRangeException** se il *espressione* il parametro è minore di 1.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creato un `MultiPoint``geometry collection` e utilizza `STGeometryN()` per trovare la seconda `geometry` istanza della raccolta.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT(0 0, 13.5 2, 7 19)', 0);  
SELECT @g.STGeometryN(2).ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

