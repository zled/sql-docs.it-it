---
title: Z (tipo di dati geography) | Documenti Microsoft
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
- Z (geography Data Type)
- Z_(geography_Data_Type)_TSQL
dev_langs: TSQL
helpviewer_keywords: Z method
ms.assetid: 9abc79c5-43c9-4cc2-b37f-d2ecdec7c234
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: af88586a78cf9d77c21566f9ee1dd60a62be1f11
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="z-geography-data-type"></a>Z (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Valore Z (elevazione) dell'istanza. La semantica del valore di elevazione è definita dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.Z  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo: **float**  
  
 Tipo CLR: **SqlDouble**  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questa proprietà è null se il **geography** istanza non è un punto per qualsiasi **punto** istanza per cui non è impostata.  
  
 Questa proprietà è di sola lettura.  
  
 Le coordinate Z non vengono utilizzati in alcun calcolo eseguito dalla libreria né vengono trasferite ad alcun calcolo della libreria.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `Point` con valori Z (innalzamento) e M (misura) e viene utilizzato `Z` per recuperare il valore Z dell'istanza.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.Z;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [M &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/m-geography-data-type.md)   
 [AsTextZM &#40;tipo di dati geography&#41;](../../t-sql/spatial-geography/astextzm-geography-data-type.md)  
  
  
