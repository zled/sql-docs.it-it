---
title: STPointFromWKB (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 08/03/2017
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
- STPointFromWKB (geometry Data Type)
- STPointFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STPointFromWKB (geometry Data Type)
ms.assetid: 1157c172-2dc7-4393-bae6-b85406171a34
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cbc2b0ece517930a19c6d99aa1220b2294aaf77d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="stpointfromwkb-geometry-data-type"></a>STPointFromWKB (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un **geometryPoint** istanza da una rappresentazione di Open Geospatial Consortium (OGC) Well-Known Binary (WKB).
  
## <a name="syntax"></a>Sintassi  
  
```  
  
STPointFromWKB ( 'WKB_point' , SRID )  
```  
  
## <a name="arguments"></a>Argomenti  
 *WKB_point*  
 Rappresentazione WKB del **geometryPoint** istanza da restituire. *WKB_point* è un **varbinary (max)** espressione.  
  
 *SRID*  
 È un **int** fanno riferimento a espressioni che rappresenta l'ID (SRID) del **geometryPoint** istanza da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
 Tipo OGC: **punto**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo genererà un **FormatException** se l'input non è formattata correttamente.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `STPointFromWKB()` per creare un'istanza `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::STPointFromWKB(0x010100000000000000000059400000000000005940, 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geometria statici OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

