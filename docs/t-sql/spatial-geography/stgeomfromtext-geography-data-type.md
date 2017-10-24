---
title: STGeomFromText (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STGeomFromText (geography Data Type)
- STGeomFromText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full globe
- STGeomFromText method
ms.assetid: 3717987b-77d8-4ccf-a1db-5a8016ac1083
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bdd52d6a9dc928d47db871ec9a84648797e64fe8
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stgeomfromtext-geography-data-type"></a>STGeomFromText (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un **geography** istanza di una rappresentazione di Open Geospatial Consortium (OGC) Well-Known Text (WKT), integrata con qualsiasi valore Z (innalzamento) e M (misura) appartenente all'istanza.
  
Questo **geography** metodo supportata dal tipo di dati **FullGlobe** istanze o le istanze spaziali con dimensioni maggiori di un emisfero.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
STGeomFromText ( 'geography_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Argomenti  
 *geography_tagged_text*  
 È la rappresentazione WKT del **geography** istanza da restituire. *geography_tagged_text* è un **nvarchar (max)** espressione.  
  
 *IDENTIFICATORE SRID*  
 È un **int** fanno riferimento a espressioni che rappresenta l'ID (SRID) del **geography** istanza da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 Il tipo OGC del **geography** istanza restituita dalla stgeomfromtext () è impostato per l'input WKT corrispondente.  
  
 Questo metodo genererà un' **ArgumentException** se l'input contiene un bordo opposto.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `STGeomFromText()` per creare un'istanza `geography`.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geografia statici OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  

