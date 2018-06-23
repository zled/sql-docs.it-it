---
title: MultiLineString | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MultiLineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 95deeefe-d6c5-4a11-b347-379e4486e7b7
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e87912fc00924698bf2fe735c0bd9ce9433cdb1e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069351"
---
# <a name="multilinestring"></a>MultiLineString
  Un `MultiLineString` è una raccolta di zero o più `geometry` oppure **geographyLineString** istanze.  
  
## <a name="multilinestring-instances"></a>Istanze MultiLineString  
 Nella figura seguente vengono illustrati esempi di `MultiLineString` istanze.  
  
 ![Esempi di istanze di geometria MultiLineString](../../database-engine/media/multilinestring.gif "Esempi di istanze di geometria MultiLineString")  
  
 Come indicato nell'illustrazione:  
  
-   Figura 1 è un semplice `MultiLineString` istanza il cui limite è i quattro endpoint dei due `LineString` elementi.  
  
-   La figura 2 è un'istanza di tipo semplice `MultiLineString` perché si intersecano solo gli endpoint degli elementi `LineString`. Il limite è rappresentato dai due endpoint non sovrapposti.  
  
-   La figura 3 è un'istanza di tipo non semplice `MultiLineString` perché l'interno di uno dei suoi elementi `LineString` è intersecato. Il limite di questa `MultiLineString` istanza è i quattro endpoint.  
  
-   La figura 4 rappresenta un'istanza di tipo non semplice, non chiuso `MultiLineString`.  
  
-   La figura 5 rappresenta un'istanza di tipo semplice, non chiuso `MultiLineString`. Non è chiusa perché il relativo `LineStrings` elementi non sono chiusi. È semplice perché nessuna delle parti interne di uno qualsiasi del `LineStrings` istanze si intersecano.  
  
-   Figura 6 è un semplice chiusa `MultiLineString` istanza. È chiusa perché tutti i suoi elementi sono chiusi. È semplice perché nessuno dei suoi elementi si interseca con le parti interne.  
  
### <a name="accepted-instances"></a>Istanze accettate  
 Per un `MultiLineString` essere accettata deve essere vuota o comprendere esclusivamente `LineString` istanze accettate. Per ulteriori informazioni su accettato `LineString` istanze, vedere [LineString](../spatial/linestring.md). Negli esempi seguenti vengono illustrate alcune istanze `MultiLineString` accettate.  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
```  
  
 Nell'esempio seguente genera una `System.FormatException` perché la seconda `LineString` istanza non è valida.  
  
```  
DECLARE @g geometry = 'MULTILINESTRING((1 1, 3 5),(-5 3))';  
```  
  
### <a name="valid-instances"></a>Istanze valide  
 Per un `MultiLineString` istanza sia valida deve soddisfare i criteri seguenti:  
  
1.  Tutte le istanze che comprendono l'istanza `MultiLineString` devono essere istanze `LineString` valide.  
  
2.  Due istanze `LineString` che comprendono l'istanza di `MultiLineString` possono sovrapporsi a un intervallo. Le istanze di `LineString` possono solo intersecarsi oppure toccarsi reciprocamente o con altre istanze di `LineString` in un numero finito di punti.  
  
 Nell'esempio seguente vengono indicate tre istanze `MultiLineString` valide e un'istanza `MultiLineString` non valida.  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` non è valido perché la seconda `LineString` istanza si sovrappone al primo `LineString` istanza a un intervallo. Si toccano in un numero infinito di punti.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente crea un'istanza `geometry``MultiLineString` che contiene due elementi `LineString` con SRID 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
```  
  
 Per creare un'istanza di questa istanza con un diverso SRID, utilizzare `STGeomFromText()` o `STMLineStringFromText()`. È anche possibile utilizzare `Parse()` e quindi modificare l'identificatore SRID, come mostrato dall'esempio seguente.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
SET @g.STSrid = 13;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [STLength &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)   
 [STIsClosed &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)   
 [LineString](../spatial/linestring.md)   
 [Dati spaziali &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)  
  
  
