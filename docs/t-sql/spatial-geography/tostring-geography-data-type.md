---
title: ToString (tipo di dati geography) | Documenti Microsoft
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
- ToString (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- ToString method
ms.assetid: 045c12fa-8fc6-441a-9500-7021cb4ff13e
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 34e028dcd1a9fd141d0771e1b410d469d6dbd47c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="tostring-geography-data-type"></a>ToString (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce la rappresentazione di Open Geospatial Consortium (OGC) Well-Known Text (WKT) di un **geography** istanza integrata con qualsiasi valore Z (innalzamento) e M (misura) appartenente all'istanza.  
  
 Metodo supportata dal tipo di dati geography **FullGlobe** istanze o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.ToString ()  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **nvarchar (max)**  
  
 Tipo CLR restituito: **SqlString**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituisce la stringa "Null" se viene chiamato su istanze Null. In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], il set di risultati possibili nel server è stato esteso per **FullGlobe** istanze. Questo metodo restituirà lo stesso valore di `AsTextZM()`.  
  
 Il metodo non è preciso.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata una `LineString` istanza e viene utilizzato `ToString()` per restituire la descrizione di testo dell'istanza.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [AsTextZM &#40;tipo di dati geography&#41;](../../t-sql/spatial-geography/astextzm-geography-data-type.md)  
  
  
