---
title: STNumCurves (tipo di dati geography) | Documenti Microsoft
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
- STNumCurves
- STNumCurves_TSQL
dev_langs: TSQL
helpviewer_keywords: STNumCurves method (geography)
ms.assetid: e98a56c2-8496-4dfd-9b37-7f3c4ca9b2b5
caps.latest.revision: "10"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b7baccab2b0087fdb2ae90f5b212b4d820919d25
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="stnumcurves-geography-data-type"></a>STNumCurves (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce il numero di curve in una matrice unidimensionale **geography** istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STNumCurves()  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 I tipi di dati spaziali unidimensionali includono **LineString**, **CircularString**, e **CompoundCurve**. Un oggetto vuoto unidimensionale **geography** istanza restituisce 0.  
  
 `STNumCurves`() funziona solo su tipi semplici; non funziona con **geography** come raccolte **MultiLineString**. **NULL** viene restituito quando il **geography** istanza non è un tipo di dati unidimensionale.  
  
 **Null** viene restituito per non inizializzata **geography** istanze.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-stnumcurves-on-a-circularstring-instance"></a>A. Utilizzo di STNumCurves() in un'istanza CircularString  
 Nell'esempio seguente viene illustrato come ottenere il numero di curve in un'istanza `CircularString`:  
  
```
 DECLARE @g geography; 
 SET @g = geography::Parse('CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');  
 SELECT @g.STNumCurves();
 ```  
  
### <a name="b-using-stnumcurves-on-a-compoundcurve-instance"></a>B. Utilizzo di STNumCurves() in un'istanza CompoundCurve  
 Nell'esempio seguente viene utilizzato `STNumCurves()` per restituire il numero di curve in un'istanza `CompoundCurve`.  
  
```
 DECLARE @g geography;  
 SET @g = geography::Parse('COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))');  
 SELECT @g.STNumCurves();
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica dei tipi di dati spaziali](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [Metodi OGC sulle istanze geografiche](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
