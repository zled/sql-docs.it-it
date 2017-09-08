---
title: STPointFromText (tipo di dati geography) | Documenti Microsoft
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
- STPointFromText (geography Data Type)
- STPointFromText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STPointFromText method
ms.assetid: e5fe54dc-0007-4631-8dde-7ae4d4c41f6e
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1b887aa5f33d40b047a81837ea91bfff8ecca7d1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stpointfromtext-geography-data-type"></a>STPointFromText (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un **geography** istanza di una rappresentazione di Open Geospatial Consortium (OGC) Well-Known Text (WKT), integrata con qualsiasi valore Z (innalzamento) e M (misura) appartenente all'istanza.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
STPointFromText ( 'point_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Argomenti  
 *point_tagged_text*  
 È la rappresentazione WKT del **geographyPoint** istanza da restituire. *point_tagged_text* è un **nvarchar (max)** espressione.  
  
 *IDENTIFICATORE SRID*  
 È un **int** fanno riferimento a espressioni che rappresenta l'ID (SRID) del **geographyPoint** istanza da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
 Tipo OGC: **punto**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo genera un **FormatException** se l'input non è formattata correttamente.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `STPointFromText()` per creare un'istanza `geography`.  
  
```  
DECLARE @g geography;  
SET @g = geography::STPointFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geografia statici OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  

