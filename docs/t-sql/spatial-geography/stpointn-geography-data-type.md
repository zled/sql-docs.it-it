---
title: STPointN (tipo di dati geography) | Documenti Microsoft
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
- STPointN_TSQL
- STPointN (geography Data Type)
dev_langs: TSQL
helpviewer_keywords: STPointN method
ms.assetid: 47670feb-b9e0-4b4b-af83-b9bba7da66ac
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0169852c4b7512ec3001875cba423bc93e53125e
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="stpointn-geography-data-type"></a>STPointN (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il punto specificato in un **geography** istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STPointN ( expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È un **int** espressione compreso tra 1 e il numero di punti di **geography** istanza.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
 Aprire tipo Geospatial Consortium (OGC): **punto**  
  
## <a name="remarks"></a>Osservazioni  
 Se un **geography** istanza è creata dall'utente, STPointN() restituisce il punto specificato da *espressione* ordinando i punti nell'ordine in cui sono stati originalmente immessi.  
  
 Se un **geography** istanza viene costruita dal sistema, STPointN() restituisce il punto specificato da *espressione* ordinando tutti i punti nello stesso ordine sarebbero output: innanzitutto in base  **Geography** istanza, quindi in base all'anello all'interno dell'istanza (se appropriato), quindi dal punto all'interno dell'anello. Questo ordine è deterministico.  
  
 Se questo metodo viene chiamato con un valore minore di 1, viene generata una **ArgumentOutOfRangeException**.  
  
 Se questo metodo viene chiamato con un valore maggiore del numero di punti nell'istanza, restituisce Null.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `LineString` e viene utilizzato `STPointN()` per recuperare il secondo punto della descrizione dell'istanza.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STPointN(2).ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze geografiche](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
