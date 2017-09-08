---
title: LAT (tipo di dati geography) | Documenti Microsoft
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
- Lat
- Lat_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Lat method
ms.assetid: 051d66bc-04de-4c58-861c-760dc5b859b5
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 313419e50b1ff142cd9d47bddd93b1c8bdce2835
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="lat-geography-data-type"></a>Lat (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  La proprietà della latitudine del **geography** istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
.Lat  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo: **float**  
  
 Tipo CLR: **SqlDouble**  
  
## <a name="remarks"></a>Osservazioni  
 Nel modello OpenGIS Lat viene definita solo su **geography** istanze è costituito da un singolo punto. Questa proprietà restituirà NULL se **geography** istanze contengono più di un singolo punto. La proprietà è precisa e di sola lettura.  
  
## <a name="examples"></a>Esempi  
 In questo esempio viene creato un punto e ne viene restituita la latitudine.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.Lat;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
