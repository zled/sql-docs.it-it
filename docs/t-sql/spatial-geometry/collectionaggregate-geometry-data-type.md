---
title: CollectionAggregate (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 08/03/2017
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
dev_langs:
- TSQL
helpviewer_keywords:
- CollectionAggregate method (geometry)
ms.assetid: b7c85d59-c841-4b7f-9d46-8b4b7f2a3afe
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5beba14806fb387c9004ec0b7992e2869d88d4dc
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="collectionaggregate-geometry-data-type"></a>CollectionAggregate (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Crea un **GeometryCollection** istanza da un set di **geometry** tipi.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CollectionAggregate ( geometry_operand )  
```  
  
## <a name="arguments"></a>Argomenti  
 *geometry_operand*  
 È un **geometry** colonna di tabella di tipo che rappresenta un set di **geometry** oggetti da includere nel **GeometryCollection** istanza.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
## <a name="exceptions"></a>Eccezioni  
 Genera un'eccezione `FormatException` in presenza di valori di input non validi. Vedere [STIsValid &#40; tipo di dati geometry &#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)  
  
## <a name="remarks"></a>Osservazioni  
 Metodo **null** quando l'input è vuoto o l'input dispone di SRID diversi. Vedere [identificatori SRID &#40; Identificatori SRID &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
 Metodo ignora **null** input.  
  
> [!NOTE]  
>  Metodo **null** se tutti i valori immessi sono **null**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita un'istanza `GeometryCollection` che contiene `CurvePolygon` e `Polygon`.  
  
 ```
 -- Setup table variable for CollectionAggregate example  
 DECLARE @Geom TABLE  
 (  
 shape geometry,  
 shapeType nvarchar(50)  
 )  
 INSERT INTO @Geom(shape,shapeType) VALUES('CURVEPOLYGON(CIRCULARSTRING(2 3, 4 1, 6 3, 4 5, 2 3))', 'Circle'),  
 ('POLYGON((1 1, 4 1, 4 5, 1 5, 1 1))', 'Rectangle');  
 -- Perform CollectionAggregate on @Geom.shape column  
 SELECT geometry::CollectionAggregate(shape).ToString()  
 FROM @Geom;
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geometria statici estesi](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

