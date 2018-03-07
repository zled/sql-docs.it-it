---
title: AsTextZM (tipo di dati geography) | Documenti Microsoft
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
- AsTextZM (geography Data Type)
- AsTextZM_TSQL
- AsTextZM
- AsTextZM_(geography_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- AsTextZM method
ms.assetid: e9dc27f6-e945-4457-8498-7644db34008e
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 95a5af7ee424ddc4413c41aa16404c0491adff4c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="astextzm-geography-data-type"></a>AsTextZM (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce la rappresentazione di Open Geospatial Consortium (OGC) Well-Known Text (WKT) di un **geography** istanza integrata con qualsiasi **Z** (innalzamento) e **M** (misura) valori appartenente all'istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.AsTextZM ()  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **nvarchar (max)**  
  
 Tipo CLR restituito: **SqlChars**  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creato un `Point` istanza contenente **Z** (innalzamento) e **M** valori (misura). `STAsText()`Seleziona i valori WKT, (-122.34900 47.65100); `AsTextZM()` seleziona gli stessi valori WKT e restituisce i valori per **Z** e **M**, generando (-122.34900 47.65100 10.3 12).  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.STAsText();  
SELECT @g.AsTextZM();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [M &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/m-geography-data-type.md)   
 [Z &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/z-geography-data-type.md)  
  
  
