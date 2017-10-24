---
title: STPointFromWKB (tipo di dati geometry) | Documenti Microsoft
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
- STPointFromWKB (geometry Data Type)
- STPointFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STPointFromWKB (geometry Data Type)
ms.assetid: 1157c172-2dc7-4393-bae6-b85406171a34
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e32527bb0878f21ae255d72ba715024fd05c031d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stpointfromwkb-geometry-data-type"></a>STPointFromWKB (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un **geometryPoint** istanza da una rappresentazione di Open Geospatial Consortium (OGC) Well-Known Binary (WKB).
  
## <a name="syntax"></a>Sintassi  
  
```  
  
STPointFromWKB ( 'WKB_point' , SRID )  
```  
  
## <a name="arguments"></a>Argomenti  
 *WKB_point*  
 Rappresentazione WKB del **geometryPoint** istanza da restituire. *WKB_point* è un **varbinary (max)** espressione.  
  
 *IDENTIFICATORE SRID*  
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
  
  


