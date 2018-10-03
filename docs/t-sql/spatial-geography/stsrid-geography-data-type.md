---
title: STSrid (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STSrid (geography Data Type)
- STSrid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STSrid method
ms.assetid: 6b04f5a7-2e69-4d34-901e-b61ba6ca9c14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 20c59a05c19d55406e27043602d979b2db681729
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47712139"
---
# <a name="stsrid-geography-data-type"></a>STSrid (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **STSrid** è un Integer che rappresenta l'identificatore SRID dell'istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STSrid  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **int**  
  
 Tipo CLR: **SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 Questa proprietà può essere modificata.  
  
## <a name="examples"></a>Esempi  
 Nel primo esempio viene creata un'istanza `geography` con il valore dell'identificatore SRID uguale a 4326 (WGS84) e viene utilizzato `STSrid` per confermare l'identificatore SRID.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STSrid;  
```  
  
 Nel secondo esempio viene utilizzato `STSrid` per impostare il valore dell'identificatore SRID dell'istanza su 4267 (NAD27), quindi viene confermato il valore SRID modificato.  
  
```  
SET @g.STSrid = 4267;  
SELECT @g.STSrid;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geografia](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)   
 [Identificatori SRID &#40;Spatial Reference Identifier&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
  
