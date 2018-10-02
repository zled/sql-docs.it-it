---
title: STDimension (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STDimension (geography Data Type)
- STDimension_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STDimension method
ms.assetid: 4368b0f6-0678-4ade-87dc-b43d8b2e8d92
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 20103774beb936ede7ab6a3b56201230b18cbd3e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47801099"
---
# <a name="stdimension-geography-data-type"></a>STDimension (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce le dimensioni massime di un'istanza **geography**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STDimension ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **int**  
  
 Tipo CLR restituito: **SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 STDimension() restituisce -1 se l'istanza **geography** è vuota.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente usa `STDimension()` per creare una variabile di tabella per contenere le istanze `geography` e inserisce un valore `Point`, un valore `LineString` e un valore `Polygon`.  
  
```  
DECLARE @temp table ([name] varchar(10), [geom] geography);  
  
INSERT INTO @temp values ('Point', geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326));  
INSERT INTO @temp values ('LineString', geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326));  
INSERT INTO @temp values ('Polygon', geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
  
SELECT [name], [geom].STDimension() as [dim]  
FROM @temp;  
```  
  
 L'esempio restituisce quindi le dimensioni di ogni istanza `geography`.  
  
|NAME|dim|  
|----------|---------|  
|Punto|0|  
|LineString|1|  
|Polygon|2|  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze geografiche](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
