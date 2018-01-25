---
title: STLineFromText (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 07/30/2017
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
- STLineFromText (geography Data Type)
- STLineFromText_TSQL
dev_langs: TSQL
helpviewer_keywords: STLineFromText method
ms.assetid: e0c05bde-077d-4ce2-b4ec-8861db9b996d
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ace48b5cfc8be18c0867bb1c0fc43d7e09d8a9e5
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="stlinefromtext-geography-data-type"></a>STLineFromText (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un **geography** istanza di una rappresentazione di Open Geospatial Consortium (OGC) Well-Known Text (WKT), integrata con qualsiasi valore Z (innalzamento) e M (misura) appartenente all'istanza.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
STLineFromText ( 'linestring_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Argomenti  
 *linestring_tagged_text*  
 È la rappresentazione WKT del **geographyLineString** istanza da restituire. *linestring_tagged_text* è un **nvarchar (max)** espressione.  
  
 *SRID*  
 È un **int** fanno riferimento a espressioni che rappresenta l'ID (SRID) del **geographyLineString** istanza da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
 Tipo OGC: **LineString**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo genera un **FormatException** se l'input non è formattata correttamente.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `STLineFromText()` per creare un'istanza `geography`.  
  
```  
DECLARE @g geography;  
SET @g = geography::STLineFromText('LINESTRING(-122.360 47.656, -122.343 47.656 )', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi geography statici OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
