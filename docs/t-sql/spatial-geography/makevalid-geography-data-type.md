---
title: MakeValid (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- MakeValid method (geography)
ms.assetid: f67038e3-4f62-4465-994e-e95ac27d8ada
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b7571fc6c82bf5fc6e2fb36a0d4d37951fd24449
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="makevalid-geography-data-type"></a>MakeValid (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Converte un **geography** istanza che non è valido in un oggetto valido **geography** istanza con un tipo Open Geospatial Consortium (OGC) valido.  
  
 Se un oggetto di input restituisce False per stisvalid (), `MakeValid()` Converte l'istanza non è valido a un'istanza valida.  
  
 Metodo supportata dal tipo di dati geography **FullGlobe** istanze o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.MakeValid ()  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo potrebbe modificare il tipo di **geography** istanza. Inoltre, i punti di un **geography** istanza potrebbe spostare leggermente. Risultati di alcuni metodi, ad esempio NumPoint() potrebbero cambiare.  
  
 Nei casi in cui l'istanza spaziale non valida intersechi l'equatore e ha un EnvelopeAngle() = 180, un **FullGlobe** istanza verrà restituita. Il `MakeValid()` **geography** metodo con tipo di dati verrà effettuato il miglior tentativo di restituire istanze valide, ma i risultati non sono garantiti accurati o precisi.  
  
> [!NOTE]  
>  È possibile archiviare gli oggetti non validi nel database. I metodi che possono essere eseguiti sulle istanze non valide (istanze per cui stisvalid () restituiscono False) sono metodi che controllano la validità o consentono l'esportazione: stisvalid (), MakeValid (), stastext (), STAsBinary(), ToString (), AsTextZM() e AsGml().  
  
 Il metodo non è preciso.  
  
## <a name="examples"></a>Esempi  
 Nel primo esempio viene creata un'istanza `LineString` non valida che si sovrappone e viene utilizzato `STIsValid()` per confermare che tale istanza non è valida. Tramite `STIsValid()` viene restituito il valore 0 per un'istanza non valida.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(0 2, 1 1, 1 0, 1 1, 2 2)', 4326);  
SELECT @g.STIsValid();  
```  
  
 Nel secondo esempio viene utilizzato `MakeValid()` per rendere valida l'istanza e per verificarne l'effettiva validità. Tramite `STIsValid()` viene restituito il valore 1 per un'istanza valida.  
  
```  
SET @g = @g.MakeValid();  
SELECT @g.STIsValid();  
```  
  
 Nel terzo esempio viene verificato il modo in cui l'istanza è stata modificata per renderla valida.  
  
```  
SELECT @g.ToString();  
```  
  
 In questo esempio, quando l'istanza `LineString` è selezionata, i valori vengono restituiti come un'istanza `MultiLineString` valida.  
  
```  
MULTILINESTRING ((0 2, 1 1, 2 2), (1 1, 1 0))  
```  
  
## <a name="see-also"></a>Vedere anche  
 [STIsValid &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)   
 [Metodi estesi sulle istanze geografiche](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
