---
title: STArea (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- STArea (geography Data Type)
- STArea_TSQL
dev_langs: TSQL
helpviewer_keywords: STArea method
ms.assetid: cfc0b0e0-7fde-431a-863f-d13f3b1b1bef
caps.latest.revision: "16"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4466e800b22996068bfb288b8800541ef6e96f7c
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="starea-geography-data-type"></a>STArea (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce l'area della superficie totale di un **geography** istanza. Per STArea() vengono restituiti come quadrato dell'unità di misura utilizzata dall'identificatore SRID del **geography** istanza; ad esempio, se l'identificatore SRID dell'istanza è 4326, STArea() restituisce risultati in metri quadrati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **float**  
  
 Tipo CLR restituito: **SqlDouble**  
  
## <a name="remarks"></a>Osservazioni  
 STArea() restituisce 0 se un **geography** istanza contiene solo figure 0 e 1-dimensioni o se è vuota.  
  
> [!NOTE]  
>  Metodi di **geography** che producono una metrica restituire valore avrà risultati diversi basati sull'identificatore SRID dell'istanza utilizzato nel metodo del tipo di dati. Per ulteriori informazioni sugli identificatori SRID, vedere [gli identificatori di riferimento spaziale &#40; Identificatori SRID &#41; ](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente usa `STArea()` per creare un `Polygon``geography` istanza e viene calcolata l'area del poligono.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STArea();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze geografiche](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
