---
title: STMLineFromWKB (tipo di dati geometry) | Documenti Microsoft
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
- STMLineFromWKB (geometry Data Type)
- STMLineFromWKB_TSQL
dev_langs: TSQL
helpviewer_keywords: STMLineFromWKB (geometry Data Type)
ms.assetid: 00a8a8e7-11d6-47a0-b971-00e60f7877ce
caps.latest.revision: "17"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3d8b283da368ca98b851180e150ee125890984f3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="stmlinefromwkb-geometry-data-type"></a>STMLineFromWKB (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un **geometryMultiLineString** istanza da una rappresentazione di Open Geospatial Consortium (OGC) Well-Known Binary (WKB).
  
## <a name="syntax"></a>Sintassi  
  
```  
  
STMLineFromWKB ( 'WKB_multilinestring' , SRID )  
```  
  
## <a name="arguments"></a>Argomenti  
 *WKB_multilinestring*  
 Rappresentazione WKB del **geometryMultiLineString** istanza da restituire. *WKB_multilinestring* è un **varbinary (max)** espressione.  
  
 *IDENTIFICATORE SRID*  
 È un **int** fanno riferimento a espressioni che rappresenta l'ID (SRID) del **geometryMultiLineString** istanza da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
 Tipo OGC: **MultiLineString**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo genererà un **FormatException** se l'input non è formattata correttamente.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `STMLineFromWKB()` per creare un'istanza `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::STMLineFromWKB(0x0105000000020000000102000000020000000000000000005940000000000000594000000000000069400000000000006940010200000003000000000000000000084000000000000010400000000000001C40000000000000204000000000000024400000000000002440, 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geometria statici OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

