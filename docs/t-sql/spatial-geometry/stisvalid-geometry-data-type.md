---
title: STIsValid (tipo di dati geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIsValid (geometry Data Type)
- STIsValid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STIsValid (geometry Data Type)
ms.assetid: 6da39bea-0f67-4660-98fc-d7214f9b2138
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b3d22ecff8c4cc4598f6c991a3c695c5d098bff6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47700909"
---
# <a name="stisvalid-geometry-data-type"></a>STIsValid (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce true se il formato di un'istanza **geometry** è corretto, in base al relativo tipo OGC (Open Geospatial Consortium). Restituisce false se il formato di un'istanza **geometry** non è corretto.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STIsValid ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Il tipo OGC di un'istanza **geometry** può essere determinato richiamando [STGeometryType()](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] produce solo istanze **geometry** valide, ma consente l'archiviazione e il recupero di istanze non valide. Un'istanza valida che rappresenta lo stesso set di punti di qualsiasi istanza non valida può essere recuperata utilizzando il metodo `MakeValid()`.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `geometry` e viene utilizzato `STIsValid()` per verificare se l'istanza è valida.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STIsValid();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [STGeometryType &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)   
 [MakeValid &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/makevalid-geometry-data-type.md)   
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

