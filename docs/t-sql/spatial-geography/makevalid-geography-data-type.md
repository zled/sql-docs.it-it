---
title: MakeValid (tipo di dati geography) | Microsoft Docs
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

  Converte un'istanza **geography** non valida in un'istanza **geography** valida con un tipo OGC (Open Geospatial Consortium) valido.  
  
 Se un oggetto di input restituisce False per STIsValid(), `MakeValid()` converte l'istanza non valida in un'istanza valida.  
  
 Questo metodo con tipo di dati geography supporta le istanze **FullGlobe** o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.MakeValid ()  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Questo metodo potrebbe modificare il tipo dell'istanza **geography**. È anche possibile che si verifichi un leggero spostamento dei punti di un'istanza **geography**. I risultati di alcuni metodi come NumPoint() potrebbero essere modificati.  
  
 Se l'istanza spaziale non valida interseca l'equatore e dispone di EnvelopeAngle() = 180, verrà restituita un'istanza **FullGlobe**. Il metodo con tipo di dati **geography** `MakeValid()` prova a restituire istanze valide, ma non vi è garanzia che i risultati siano accurati o precisi.  
  
> [!NOTE]  
>  È possibile archiviare gli oggetti non validi nel database. I metodi che possono essere eseguiti sulle istanze non valide (istanze per cui STIsValid() restituisce False) sono metodi che controllano la validità o consentono l'esportazione: STIsValid(), MakeValid(), STAsText(), STAsBinary(), ToString(), AsTextZM() e AsGml().  
  
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
  
  
