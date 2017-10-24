---
title: STWithin (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STWithin method (geography)
ms.assetid: 6fc745cc-7976-418a-a89a-c267e64ab3a2
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c0347f3ceb94b52aab11378dbb058dd49b60e7b1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stwithin-geography-data-type"></a>STWithin (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce 1 se un **geography** istanza è spazialmente all'interno di altra **geography** istanza; in caso contrario, restituisce 0.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STWithin ( other_geography )  
```  
  
## <a name="arguments"></a>Argomenti  
 *other_geography*  
 Un altro **geography** istanza da confrontare con l'istanza sulla quale `STWithin()` viene richiamato.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituisce sempre null se gli ID di riferimento spaziale (SRID) del **geography** istanze non corrispondono.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato `STWithin()` per verificare se per due istanze `geography` la prima è completamente all'interno della seconda.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::Parse('POLYGON ((-120.533 46.566, -118.283 46.1, -122.3 47.45, -120.533 46.566))');  
SET @h = geography::Parse('CURVEPOLYGON (COMPOUNDCURVE (CIRCULARSTRING (-122.200928 47.454094, -122.810669 47.00648, -122.942505 46.687131, -121.14624 45.786679, -119.119263 46.183634), (-119.119263 46.183634, -119.273071 47.107523), CIRCULARSTRING (-119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)))');  
SELECT @g.STWithin(@h);  
```  
  
  

