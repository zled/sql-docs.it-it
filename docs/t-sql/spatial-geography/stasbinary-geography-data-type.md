---
title: STAsBinary (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STAsBinary_TSQL
- STAsBinary (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STAsBinary method
ms.assetid: 99602a62-265d-4aa4-a8dc-92992ca55ba4
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c48fc48b7af524e980801a11ac2574f2091823a2
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stasbinary-geography-data-type"></a>STAsBinary (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce la rappresentazione di Open Geospatial Consortium (OGC) Well-Known Binary (WKB) di un **geography** istanza.  
  
 Questo **geography** metodo supportata dal tipo di dati **FullGlobe** istanze o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STAsBinary ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **varbinary (max)**  
  
 Tipo CLR restituito: **SqlBytes**  
  
## <a name="remarks"></a>Osservazioni  
 Il tipo OGC di un **geography** istanza può essere determinata richiamando [stgeometrytype ()](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md).  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente usa `STAsBinary()` per creare un `LineString``geography` istanza (-122,360, 47,656) a (-122,343, 47,656) dal testo. e viene restituito il risultato in formato WKB.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING( -122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STAsBinary();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geografia](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

