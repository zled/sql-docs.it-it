---
title: AsGml (tipo di dati geometry) | Documenti Microsoft
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
- AsGml(geometry_Data_Type)_TSQL
- AsGml
- AsGml(geometry Data Type)
- AsGml_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- AsGml (geometry Data Type)
ms.assetid: f6c2e130-05f3-4ef3-921b-d78b51437d48
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4a4ca0fcd5b8b7b4ffdb39d3201f7060efe18a74
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="asgml-geometry-data-type"></a>AsGml (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce la rappresentazione di Geography Markup Language (GML) di un **geometry** istanza.
  
Per ulteriori informazioni su Geography Markup Language, vedere la seguente specifica Open Geospatial Consortium:[OGC Specifications, Geography Markup Language.](http://go.microsoft.com/fwlink/?LinkId=93629)
  
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
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0)', 0)  
SELECT @g.AsGml();  
```  
  
 Questo metodo restituisce la descrizione come istanza `LineString`.  
  
```  
<LineString xmlns="http://www.opengis.net/gml">  
<posList>0 0 0 1 1 0</posList></LineString>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geometria](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  


