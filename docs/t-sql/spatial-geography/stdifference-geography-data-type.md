---
title: STDifference (tipo di dati geography) | Documenti Microsoft
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
- STDifference_TSQL
- STDifference (geography Data Type)
dev_langs: TSQL
helpviewer_keywords: STDifference (geography Data Type)
ms.assetid: 1cde5054-b91a-41bb-812a-08c9308738af
caps.latest.revision: "20"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9898254d43c4586f787d5e7eb68e457137be5554
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="stdifference-geography-data-type"></a>STDifference (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce un oggetto che rappresenta il punto impostato da uno **geography** istanza che si trova di fuori di un altro **geography** istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STDifference ( other_geography )  
```  
  
## <a name="arguments"></a>Argomenti  
 *other_geography*  
 Un altro **geography** istanza che indica i punti da rimuovere dall'istanza in cui viene richiamato stdifference ().  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="exceptions"></a>Eccezioni  
 Questo metodo genera un **ArgumentException** se l'istanza contiene un bordo opposto.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituisce sempre null se gli identificatori di riferimento spaziale (SRID) del **geography** istanze non corrispondono.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il set di risultati possibili restituito nel server è stato esteso per **FullGlobe** istanze. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta le istanze spaziali di dimensioni maggiori di un emisfero. Il risultato può contenere segmenti di arco circolare solo se le istanze di input contengono segmenti di arco circolare. Il metodo non è preciso.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-computing-the-difference-between-two-geography-instances"></a>A. Calcolo della differenza tra due istanze di geografia  
 L'esempio seguente usa `STDifference()` per calcolare la differenza tra due **geography** istanze.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STDifference(@h).ToString();  
```  
  
### <a name="b-using-a-fullglobe-with-stdifference"></a>B. Utilizzo di FullGlobe con STDifference()  
 Nell'esempio seguente viene utilizzata l'istanza `FullGlobe`. Il primo risultato è un oggetto `GeometryCollection` vuoto e il secondo è un'istanza `Polygon`. `STDifference()` restituisce un oggetto `GeometryCollection` vuoto quando il parametro è un'istanza `FullGlobe`. Ogni punto in un'istanza `geography` di chiamata è contenuto in un'istanza `FullGlobe`.  
  
```
 DECLARE @g geography = 'POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 DECLARE @h geography = 'FULLGLOBE';  
 SELECT @g.STDifference(@h).ToString(),  
 @h.STDifference(@g).ToString();
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze geografiche](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
