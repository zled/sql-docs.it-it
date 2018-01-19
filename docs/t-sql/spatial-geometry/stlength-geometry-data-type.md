---
title: STLength (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 08/03/2017
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
- STLength_TSQL
- STLength (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: STLength (geometry Data Type)
ms.assetid: e34dc620-2a65-4248-b099-fff91830ab98
caps.latest.revision: "20"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9c3b702d6c27947a8fb01e18cd077a82bde7d1d8
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="stlength-geometry-data-type"></a>STLength (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce la lunghezza totale degli elementi in un **geometry** istanza.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STLength ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **float**  
  
 Tipo CLR restituito: **SqlDouble**  
  
## <a name="remarks"></a>Osservazioni  
 Se un **geometry** istanza è chiusa, la lunghezza viene calcolata come lunghezza totale lungo l'istanza; la lunghezza di qualsiasi poligono è il relativo perimetro e la lunghezza di un punto è 0. La lunghezza di qualsiasi **geometrycollection** tipo è la somma delle lunghezze delle contenute **geometry** istanze.  
  
 STLength() può essere utilizzato con oggetti LineString validi e non validi. In genere, un oggetto LineString non è valido a causa di segmenti sovrapposti dovuti ad anomalie, ad esempio tracce GPS imprecise. STLength() non rimuove i segmenti sovrapposti o non validi, i quali vengono inclusi nel valore di lunghezza restituito. È possibile rimuovere i segmenti sovrapposti da un oggetto LineString con il metodo MakeValid().  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `LineString` e viene utilizzato `STLength()` per trovare la lunghezza dell'istanza.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STLength();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

