---
title: STIsClosed (tipo di dati geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIsClosed_TSQL
- STIsClosed (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsClosed (geometry Data Type)
ms.assetid: 14edbb22-df7b-4b8a-b16c-ac477a5d32c1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5be28fe6b1533c6920c83171130a2d4104784fe2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47779143"
---
# <a name="stisclosed-geometry-data-type"></a>STIsClosed (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce 1 se i punti di inizio e di fine dell'istanza **geometry** specificata sono gli stessi. Restituisce 1 per i tipi **geometrycollection** se ogni istanza **geometry** contenuta è chiusa. Restituisce 0 se l'istanza non è chiusa.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STIsClosed ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Questo metodo restituisce 0 se una figura di un'istanza **geometry** è costituita da punti o se l'istanza è vuota.  
  
 Tutte le istanze **Polygon** sono considerate chiuse.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `LineString` e viene utilizzato `STIsClosed()` per verificare se l'istanza `LineString` è chiusa.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STIsClosed();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

