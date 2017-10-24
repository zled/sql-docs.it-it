---
title: STMPointFromWKB (tipo di dati geography) | Documenti Microsoft
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
- STMPointFromWKB (geography Data Type)
- STMPointFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STPointFromWKB method
ms.assetid: eeb7d806-3cbb-405d-8199-8b82282c53df
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e3ad3d12b350107cd6ce011b04f940f828559e79
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stmpointfromwkb-geography-data-type"></a>STMPointFromWKB (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un **geographyMultiPoint** istanza da una rappresentazione di Open Geospatial Consortium (OGC) Well-Known Binary (WKB).
  
## <a name="syntax"></a>Sintassi  
  
```  
  
STMPointFromWKB ( 'WKB_multipoint' , SRID )  
```  
  
## <a name="arguments"></a>Argomenti  
 *WKB_multipoint*  
 Rappresentazione WKB del **geographyMultiPoint** istanza da restituire. *WKB_multipoint* è un **varbinary (max)** espressione.  
  
 *IDENTIFICATORE SRID*  
 È un **int** fanno riferimento a espressioni che rappresenta l'ID (SRID) del **geographyMultiPoint** istanza da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
 Tipo OGC: **MultiPoint**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo genera un **FormatException** se l'input non è formattata correttamente.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `STMPointFromWKB()` per creare un'istanza `geography`.  
  
```  
DECLARE @g geography;   
SET @g = geography::STMPointFromWKB(0x0104000000020000000101000000D7A3703D0A975EC08716D9CEF7D347400101000000CBA145B6F3955EC08716D9CEF7D34740, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geografia statici OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  

