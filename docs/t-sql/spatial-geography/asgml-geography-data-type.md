---
title: AsGml (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AsGml_(geography_Data_Type)_TSQL
- AsGml
- AsGml_TSQL
- AsGml (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- AsGml method
ms.assetid: 67795c64-d8d3-48dc-93ef-3c8a9274deb6
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f5c13754e9d889245e667dcf377ee158fb500aa
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
#  <a name="asgml---geography-data-type"></a>AsGml - tipo di dati geography
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce la rappresentazione di Geography Markup Language (GML) di un **geography** istanza.  
  
 Per ulteriori informazioni su Geography Markup Language, vedere la specifica Open Geospatial Consortium: [OGC Specifications, Geography Markup Language.](http://go.microsoft.com/fwlink/?LinkId=93629)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.AsGml ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **xml**  
  
 Tipo CLR restituito: **SqlXml**  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `LineString` e viene utilizzato `AsGML()` per restituire la descrizione GML dell'istanza.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.AsGml();  
```  
  
 Questo metodo restituisce la descrizione come istanza `LineString`.  
  
```  
<LineString xmlns="http://www.opengis.net/gml"><posList>47.656 -122.36 47.656 -122.343</posList></LineString>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
