---
title: STDifference (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STDifference_TSQL
- STDifference (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDifference (geography Data Type)
ms.assetid: 1cde5054-b91a-41bb-812a-08c9308738af
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8eeb7743ed17f9bd2bbd837b02357723cbb0f49e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38042509"
---
# <a name="stdifference-geography-data-type"></a>STDifference (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce un oggetto che rappresenta il set di punti di un'istanza **geography** che si trova all'esterno di un'altra istanza **geography**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STDifference ( other_geography )  
```  
  
## <a name="arguments"></a>Argomenti  
 *other_geography*  
 Altra istanza **geography** che indica i punti da rimuovere dall'istanza sulla quale viene richiamato STDifference().  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="exceptions"></a>Eccezioni  
 Questo metodo genera un'eccezione **ArgumentException** se l'istanza contiene un bordo opposto.  
  
## <a name="remarks"></a>Remarks  
 Questo metodo restituisce sempre Null se gli identificatori SRID delle istanze **geography** non corrispondono.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il set di possibili risultati restituito nel server è stato esteso alle istanze **FullGlobe**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta le istanze spaziali di dimensioni maggiori di un emisfero. Il risultato può contenere segmenti di arco circolare solo se le istanze di input contengono segmenti di arco circolare. Il metodo non è preciso.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-computing-the-difference-between-two-geography-instances"></a>A. Calcolo della differenza tra due istanze di geografia  
 L'esempio seguente usa `STDifference()` per calcolare la differenza tra due istanze **geography**.  
  
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
  
  
