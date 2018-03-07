---
title: Parse (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Parse method
- Parse (geography Data Type)
ms.assetid: 21c402fa-fd0f-4d09-a097-49cee0316d4e
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c29c43af7034f86fa993fc5f12046200216ec57f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="parse-geography-data-type"></a>Parse (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un **geography** istanza da una rappresentazione di Open Geospatial Consortium (OGC) Well-Known Text (WKT). Parse () è equivalente a [STGeomFromText](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md), ad eccezione del fatto che presuppone un ID (SRID) di 4326 come parametro di riferimento spaziale. All'input possono appartenere valori Z (innalzamento) e M (misura) facoltativi.
  
Questo **geography** metodo supportata dal tipo di dati **FullGlobe** istanze o le istanze spaziali con dimensioni maggiori di un emisfero.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Parse ( 'geography_tagged_text' )  
```  
  
## <a name="arguments"></a>Argomenti  
 *geography_tagged_text*  
 È la rappresentazione WKT del **geography** istanza da restituire. *geography_tagged_text* è un **nvarchar** espressione.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 Il tipo OGC del **geography** istanza restituita dalla `Parse()` è impostato sull'input WKT corrispondente.  
  
 La stringa 'Null' verrà interpretata come un valore null **geography** istanza.  
  
 Questo metodo genererà **ArgumentException** se l'input contiene un bordo opposto.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `Parse()` per creare un'istanza `geography`.  
  
```  
DECLARE @g geography;   
SET @g = geography::Parse('LINESTRING(-122.360 47.656, -122.343 47.656)');  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geografia statici estesi](../../t-sql/spatial-geography/extended-static-geography-methods.md)   
 [STGeomFromText &#40;tipo di dati geography&#41;](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md)  
  
  
