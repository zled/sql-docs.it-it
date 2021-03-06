---
title: InstanceOf (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- InstanceOf
- InstanceOf_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- InstanceOf method
ms.assetid: 1eaed0e4-1c72-45a9-9926-5b513335cf33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 33de78007a5d9fb199debff7f0dceb0cb56a2dd5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47807959"
---
# <a name="instanceof-geography-data-type"></a>InstanceOf (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Verifica se l'istanza **geography** corrisponde al tipo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.InstanceOf ( 'geography_type')  
```  
  
## <a name="arguments"></a>Argomenti  
 *geography_type*  
 Stringa **nvarchar(4000)** che specifica uno dei 16 tipi esposti nella gerarchia del tipo **geography**.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Restituisce 1 se il tipo di un'istanza **geography** corrisponde al tipo specificato o se il tipo specificato è un predecessore del tipo di istanza. In caso contrario, restituisce 0.  
  
 Questo metodo con tipo di dati **geography** supporta le istanze **FullGlobe** o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
 L'input per il metodo deve essere uno dei seguenti: Geometry, Point, Curve, LineString, CircularString, Surface, Polygon, CurvePolygon, **GeometryCollection**, **MultiSurface**, **MultiPolygon, MultiCurve, MultiLineString**, **MultiPoint** o **FullGlobe**.  
  
 Questo metodo genera un'eccezione `ArgumentException` se per l'input viene utilizzata una qualsiasi altra stringa.  
  
 Il metodo non è preciso.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `MultiPoint` e viene utilizzato `InstanceOf()` per verificare se l'istanza è di tipo `GeometryCollection`.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze geografiche](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
