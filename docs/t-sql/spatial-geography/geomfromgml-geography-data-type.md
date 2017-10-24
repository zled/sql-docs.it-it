---
title: GeomFromGML (tipo di dati geography) | Documenti Microsoft
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
- GeomFromGML_TSQL
- GeomFromGML
dev_langs:
- TSQL
helpviewer_keywords:
- GeomFromGML (geography Data Type)
- GeomFromGML method
ms.assetid: 470d0997-3cb0-4d34-9a45-b332fe432b14
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ec0d21afb92b000f29fb91c4e3b848b4881b99c7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="geomfromgml-geography-data-type"></a>GeomFromGML (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Costruisce un **geography** data una rappresentazione istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] subset di Geography Markup Language (GML).
  
Per ulteriori informazioni su GML, vedere le seguenti specifiche Open Geospatial Consortium: [OGC Specifications, Geography Markup Language](http://go.microsoft.com/fwlink/?LinkId=93629)
  
Questo **geography** metodo supportata dal tipo di dati **FullGlobe** istanze o le istanze spaziali con dimensioni maggiori di un emisfero.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
GeomFromGml ( GML_input, SRID )  
```  
  
## <a name="arguments"></a>Argomenti  
 *GML_input*  
 Input XML da cui GML restituirà un valore.  
  
 *IDENTIFICATORE SRID*  
 È un **int** fanno riferimento a espressioni che rappresenta l'ID (SRID) del **geography** istanza da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo genera un **FormatException** se l'input non è formattata correttamente.  
  
 Questo metodo genererà **ArgumentException** se l'input contiene un bordo opposto.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `GeomFromGml()` per creare un'istanza `geography`.  
  
```  
DECLARE @g geography;  
DECLARE @x xml;  
SET @x = '<LineString xmlns="http://www.opengis.net/gml"><posList>47.656 -122.36 47.656 -122.343</posList></LineString>';  
SET @g = geography::GeomFromGml(@x, 4326);  
SELECT @g.ToString();  
```  
  
 Nell'esempio seguente viene utilizzato il metodo `GeomFromGml()` per creare un'istanza `FullGlobe``geography`.  
  
```  
DECLARE @g geography;  
DECLARE @x xml;  
SET @x = '<FullGlobe xmlns="http://schemas.microsoft.com/sqlserver/2011/geography" />';  
SET @g = geography::GeomFromGml(@x, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geografia statici estesi](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  

