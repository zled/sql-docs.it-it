---
title: IsValidDetailed (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IsValidDetailed_TSQL
- IsValidDetailed
dev_langs:
- TSQL
helpviewer_keywords:
- IsValidDetailed geography
ms.assetid: f5f0b753-c825-43ce-987d-98655d8d8702
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9a20f55565e5cd5cf0eecdb55fdd8fe6cf4e3aa1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33062608"
---
# <a name="isvaliddetailed-geography-data-type"></a>IsValidDetailed (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce un messaggio che aiuta a identificare i problemi con un oggetto spaziale non valido. Quando l'oggetto non è valido, viene restituito solo il primo errore. Quando l'oggetto è valido, viene restituito il valore 24400.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.IsValidDetailed()  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **nvarchar(max)**  
  
 Tipo CLR restituito: **string**  
  
## <a name="remarks"></a>Remarks  
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
|24407|Non valido perché l'anello del poligono {0} si comprime in una linea nel punto {1}.|  
|24408|Non valido perché l'anello del poligono {0} non è chiuso.|  
|24409|Non valido perché una parte dell'anello del poligono {0} si trova all'interno di un poligono.|  
|24410|Non valido perché l'anello {0} è il primo anello in un poligono di cui non costituisce l'anello esterno.|  
|24411|Non valido perché l'anello {0} si trova al di fuori dell'anello esterno {1} del relativo poligono.|  
|24412|Non valido perché l'interno di un poligono con gli anelli {0} e {1} non è connesso.|  
|24413|Non valido a causa di due bordi sovrapposti nella curva {0}.|  
|24414|Non valido perché un bordo della curva {0} si sovrappone a un bordo della curva {1}.|  
|24415|Non valido perché in qualche poligono è presente una struttura dell'anello non valida.|  
|24416|Non valido perché nella curva {0} il bordo che inizia al punto {1} è una linea o un arco degenerato con estremità diametralmente opposte.|  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente di oggetto spaziale non valido illustra il comportamento del metodo **IsValidDetailed()**.  
  
```sql  
DECLARE @p GEOGRAPHY = 'Polygon((2 2, 4 4, 4 2, 2 4, 2 2))'  
SELECT @p.IsValidDetailed()  
--Returns: 24409: Not valid because some portion of polygon ring (1) lies in the interior of a polygon.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze geografiche](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
