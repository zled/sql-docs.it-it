---
title: IsValidDetailed (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 08/03/2017
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
- IsValidDetailed geometry
ms.assetid: 5a31e88a-ad7b-4ef7-b773-e2571f1cb3aa
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ecc088ca8a68406e9146ed1b74ff72c441cb235a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="isvaliddetailed-geometry-datatype"></a>IsValidDetailed (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Restituisce un messaggio che aiuta a identificare i problemi con un oggetto spaziale non valido. Quando l'oggetto non è valido, viene restituito solo il primo errore. Quando l'oggetto è valido, viene restituito il valore 24400.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.IsValidDetailed()  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **nvarchar (max)**  
  
 Tipo CLR restituito: **stringa**  
  
## <a name="remarks"></a>Osservazioni  
 Nella tabella seguente sono elencati i valori restituiti possibili:  
  
|Valore restituito|Description|  
|------------------|-----------------|  
|24400|Valido|  
|24401|Non valido, motivo sconosciuto.|  
|24402|Non valido perché il punto {0} è un punto isolato, che non è valido in questo tipo di oggetto.|  
|24403|Non valido perché vi sono coppie di bordi del poligono che si sovrappongono.|  
|24404|Non valido perché l'anello del poligono {0} interseca se stesso o un altro anello.|  
|24405|Non valido perché una parte dell'anello del poligono interseca se stessa o un altro anello.|  
|24406|Non valido perché la curva {0} degenera in un punto.|  
|24407|Non è valido perché {0} anello poligono viene compresso in una linea nel punto di \\{1 \\}.|  
|24408|Non valido perché l'anello del poligono {0} non è chiuso.|  
|24409|Non valido perché una parte dell'anello del poligono {0} si trova all'interno di un poligono.|  
|24410|Non valido perché l'anello {0} è il primo anello in un poligono di cui non costituisce l'anello esterno.|  
|24411|Non è valido perché l'anello {0} ricade di fuori di \\{1 \\} l'anello esterno del relativo poligono.|  
|24412|Non è valido perché non è connesso l'area interna di un poligono con anelli {0} e \\{1 \\}.|  
|24413|Non valido a causa di due bordi sovrapposti nella curva {0}.|  
|24414|Non è valido perché un bordo della curva {0} si sovrappone a un bordo della curva di \\{1 \\}.|  
|24415|Non valido perché in qualche poligono è presente una struttura dell'anello non valida.|  
|24416|Non è valido perché nella curva {0} il bordo che inizia nel punto \\{1 \\} è una linea o un arco degenere con punti finali opposti.|  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente di un oggetto spaziale non valido viene illustrato come la **isvaliddetailed ()** metodi si comporta.  
  
```tsql  
DECLARE @p GEOMETRY = 'Polygon((2 2, 4 4, 4 2, 2 4, 2 2))'  
SELECT @p.IsValidDetailed()  
--Returns: 24404: Not valid because polygon ring (1) intersects itself or some other ring.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geometria](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  


