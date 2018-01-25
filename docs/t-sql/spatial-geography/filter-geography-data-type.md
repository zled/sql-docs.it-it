---
title: Filtro (tipo di dati geography) | Documenti Microsoft
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
- Filter
- Filter_TSQL
- Filter (geography Data Type)
dev_langs: TSQL
helpviewer_keywords: Filter method
ms.assetid: 82a8f54a-3a47-4e20-b13a-b148029c5448
caps.latest.revision: "10"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dd3ca8cc7e9e61cec96075b367e1ad7407179e21
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="filter-geography-data-type"></a>Filter (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Un metodo che offre un metodo rapido indice intersezione basato solo per determinare se un **geography** istanza interseca un'altra **geography** istanza, supponendo che un indice sia disponibile.  
  
 Restituisce 1 se un **geography** istanza interseca potenzialmente un'altra **geography** istanza. Questo metodo può produrre un risultato falso positivo e il risultato esatto può dipendere dal piano. Restituisce un valore esatto 0 (risultato vero positivo) se è presente alcuna intersezione di **geography** istanze trovate.  
  
 In casi in cui un indice non è disponibile o non viene utilizzato il metodo restituirà gli stessi valori **stintersects ()** quando viene chiamato con gli stessi parametri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.Filter ( other_geography )  
```  
  
## <a name="arguments"></a>Argomenti  
 *other_geography*  
 Un altro **geography** istanza da confrontare con l'istanza in cui viene richiamato Filter().  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo non è deterministico e non è preciso.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato `Filter()` per determinare se due istanze `geography` si intersecano.  
  
```  
CREATE TABLE sample (id int primary key, g geography);  
INSERT INTO sample VALUES  
   (0, geography::Point(45, -120, 4326)),  
   (1, geography::Point(45, -120.1, 4326)),  
   (2, geography::Point(45, -120.2, 4326)),  
   (3, geography::Point(45, -120.3, 4326)),  
   (4, geography::Point(45, -120.4, 4326));  
  
CREATE SPATIAL INDEX sample_idx on sample(g);  
SELECT id  
FROM sample   
WHERE g.Filter(geography::Parse(  
   'POLYGON((-120.1 44.9, -119.9 44.9, -119.9 45.1, -120.1 45.1, -120.1 44.9))')) = 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [STIntersects &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/stintersects-geography-data-type.md)  
  
  
