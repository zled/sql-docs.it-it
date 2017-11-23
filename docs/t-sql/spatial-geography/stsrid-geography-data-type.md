---
title: STSrid (tipo di dati geography) | Documenti Microsoft
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
- STSrid (geography Data Type)
- STSrid_TSQL
dev_langs: TSQL
helpviewer_keywords: STSrid method
ms.assetid: 6b04f5a7-2e69-4d34-901e-b61ba6ca9c14
caps.latest.revision: "16"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0c8069515b1104f4989e717dff6ac30fb8441b12
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="stsrid-geography-data-type"></a>STSrid (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **STSrid** è un numero intero che rappresenta l'identificatore di riferimento spaziale (SRID) dell'istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STSrid  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo: **int**  
  
 Tipo CLR: **SqlInt32**  
  
## <a name="remarks"></a>Osservazioni  
 Questa proprietà può essere modificata.  
  
## <a name="examples"></a>Esempi  
 Nel primo esempio viene creata un'istanza `geography` con il valore dell'identificatore SRID uguale a 4326 (WGS84) e viene utilizzato `STSrid` per confermare l'identificatore SRID.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STSrid;  
```  
  
 Nel secondo esempio viene utilizzato `STSrid` per impostare il valore dell'identificatore SRID dell'istanza su 4267 (NAD27), quindi viene confermato il valore SRID modificato.  
  
```  
SET @g.STSrid = 4267;  
SELECT @g.STSrid;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geografia](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)   
 [Gli identificatori SRID &#40; Identificatori SRID &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
  
