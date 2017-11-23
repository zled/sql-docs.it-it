---
title: STGeomFromText (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 07/30/2017
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
- STGeomFromText (geography Data Type)
- STGeomFromText_TSQL
dev_langs: TSQL
helpviewer_keywords:
- full globe
- STGeomFromText method
ms.assetid: 3717987b-77d8-4ccf-a1db-5a8016ac1083
caps.latest.revision: "17"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e781cdd50bd10711d181318cb584f6949828e19d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="stgeomfromtext-geography-data-type"></a>STGeomFromText (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
 [Metodi geography statici OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
