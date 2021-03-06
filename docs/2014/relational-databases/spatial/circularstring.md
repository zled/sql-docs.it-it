---
title: CircularString | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 9fe06b03-d98c-4337-9f89-54da98f49f9f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 75845ceafbf776eb15a30b3289de97573109c4d8
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018192"
---
# <a name="circularstring"></a>CircularString
  `CircularString` è una raccolta di zero o più segmenti di arco circolare continui. Un segmento di arco circolare è un segmento curvo definito da tre punti su un piano bidimensionale. Il primo punto non può corrispondere al terzo punto. Se tutti e tre i punti di un segmento di arco circolare sono collineari, il segmento di arco verrà gestito come un segmento di linea.  
  
> [!IMPORTANT]  
>  Per una descrizione dettagliata ed esempi delle nuove funzionalità spaziali introdotte in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], tra cui la `CircularString` sottotipo, scaricare il white paper [nuove funzionalità spaziali in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=226407).  
  
## <a name="circularstring-instances"></a>Istanze CircularString  
 Nel disegno seguente vengono illustrate le istanze `CircularString` valide:  
  
 ![](../../database-engine/media/5ff17e34-b578-4873-9d33-79500940d0bc.png "5ff17e34-b578-4873-9d33-79500940d0bc")  
  
### <a name="accepted-instances"></a>Istanze accettate  
 Oggetto `CircularString` istanza viene accettata se è vuota o contiene un numero dispari di punti, n, dove n > 1. Le istanze `CircularString` seguenti vengono accettate.  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';  
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';  
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 2 0, 1 1)';  
```  
  
 In `@g3` viene illustrato che l'istanza `CircularString` può essere accettata, ma non è valida. La dichiarazione dell'istanza CircularString seguente non viene accettata. Questa dichiarazione genera un'eccezione `System.FormatException`.  
  
```  
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1)';  
```  
  
### <a name="valid-instances"></a>Istanze valide  
 Un'istanza `CircularString` valida deve essere vuota o disporre degli attributi seguenti:  
  
-   Deve contenere almeno un segmento di arco circolare, cioè avere un minimo di tre punti.  
  
-   L'ultimo endpoint per ogni segmento di arco circolare nella sequenza, a eccezione dell'ultimo segmento, deve essere il primo endpoint per il segmento successivo nella sequenza.  
  
-   Deve contenere un numero di punti dispari.  
  
-   Non deve sovrapporsi a un intervallo.  
  
-   Anche se è possibile che le istanze `CircularString` contengano segmenti di linea, questi ultimi devono essere definiti da tre punti collineari.  
  
 Nell'esempio seguente vengono illustrate le istanze `CircularString` valide.  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';  
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';  
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1, 0 1)';  
DECLARE @g4 geometry = 'CIRCULARSTRING(1 1, 2 2, 2 2)';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(),@g4.STIsValid();  
```  
  
 Un'istanza `CircularString` deve contenere almeno due segmenti di arco circolare per definire un cerchio completo. In un'istanza `CircularString` non può essere utilizzato un singolo segmento di arco circolare, ad esempio (1 1, 3 1, 1 1), per definire un cerchio completo. Utilizzare (1 1, 2 2, 3 1, 2 0, 1 1) per definire il cerchio.  
  
 Nell'esempio seguente vengono illustrate le istanze CircularString non valide.  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING(1 1, 2 0, 1 1)';  
DECLARE @g2 geometry = 'CIRCULARSTRING(0 0, 0 0, 0 0)';  
SELECT @g1.STIsValid(), @g2.STIsValid();  
```  
  
### <a name="instances-with-collinear-points"></a>Istanze con punti collineari  
 Nei casi seguenti un segmento di arco circolare sarà considerato come un segmento di linea:  
  
-   Quando tutti e i tre punti sono collineari, ad esempio, (1 3, 4 4, 7 5).  
  
-   Quando il primo punto e il punto medio sono gli stessi, ma il terzo punto è diverso, ad esempio, (1 3, 1 3, 7 5).  
  
-   Quando il punto medio e l'ultimo punto sono gli stessi, ma il primo punto è diverso, ad esempio, (1 3, 4 4, 4 4).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-instantiating-a-geometry-instance-with-an-empty-circularstring"></a>A. Creazione di un'istanza Geometry con un'istanza CircularString vuota  
 In questo esempio viene illustrato come creare un'istanza `CircularString` vuota:  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CIRCULARSTRING EMPTY');  
```  
  
### <a name="b-instantiating-a-geometry-instance-using-a-circularstring-with-one-circular-arc-segment"></a>B. Creazione di un'istanza Geometry utilizzando un'istanza CircularString con un segmento di arco circolare  
 Nell'esempio seguente viene illustrato come creare un'istanza `CircularString` con un solo segmento di arco circolare (mezzo cerchio):  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry:: STGeomFromText('CIRCULARSTRING(2 0, 1 1, 0 0)', 0);  
SELECT @g.ToString();  
```  
  
### <a name="c-instantiating-a-geometry-instance-using-a-circularstring-with-multiple-circular-arc-segments"></a>C. Creazione di un'istanza Geometry utilizzando un'istanza CircularString con più segmenti di arco circolare  
 Nell'esempio seguente viene illustrato come creare un'istanza `CircularString` con più di un segmento di arco circolare (cerchio completo):  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CIRCULARSTRING(2 1, 1 2, 0 1, 1 0, 2 1)');  
SELECT 'Circumference = ' + CAST(@g.STLength() AS NVARCHAR(10));    
```  
  
 Viene prodotto l'output seguente:  
  
```  
Circumference = 6.28319  
```  
  
 Confrontare l'output quando viene utilizzata `LineString` anziché `CircularString`:  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(2 1, 1 2, 0 1, 1 0, 2 1)', 0);  
SELECT 'Perimeter = ' + CAST(@g.STLength() AS NVARCHAR(10));  
```  
  
 Viene prodotto l'output seguente:  
  
```  
Perimeter = 5.65685  
```  
  
 Si noti che il valore per il `CircularString` esempio è vicino 2∏, ovvero la circonferenza del cerchio effettiva.  
  
### <a name="d-declaring-and-instantiating-a-geometry-instance-with-a-circularstring-in-the-same-statement"></a>D. Dichiarazione e creazione di un'istanza Geometry utilizzando un'istanza CircularString nella stessa istruzione  
 In questo frammento viene illustrato come dichiarare e creare un'istanza `geometry` con un'istanza `CircularString` nella stessa istruzione:  
  
```tsql  
DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
```  
  
### <a name="e-instantiating-a-geography-instance-with-a-circularstring"></a>E. Creazione di un'istanza Geometry con un'istanza CircularString  
 Nell'esempio seguente viene illustrato come dichiarare e creare un'istanza `geography` con un'istanza `CircularString`:  
  
```tsql  
DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
```  
  
### <a name="f-instantiating-a-geometry-instance-with-a-circularstring-that-is-a-straight-line"></a>F. Creazione di un'istanza Geometry con un'istanza CircularString che corrisponde a una linea retta  
 Nell'esempio seguente viene illustrato come creare un'istanza `CircularString` che corrisponde a una linea retta:  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('CIRCULARSTRING(0 0, 1 2, 2 4)', 0);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica dei tipi di dati spaziali](spatial-data-types-overview.md)   
 [CompoundCurve](compoundcurve.md)   
 [MakeValid &#40;tipo di dati geography&#41;](/sql/t-sql/spatial-geography/makevalid-geography-data-type)   
 [MakeValid &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type)   
 [STIsValid &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)   
 [STIsValid &#40;tipo di dati geography&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type)   
 [STLength &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)   
 [STStartPoint &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)   
 [STEndpoint &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type)   
 [STPointN &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)   
 [STNumPoints &#40;geometry Data Type&#41; (STNumPoints &#40;tipo di dati geometry&#41;)](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type)   
 [STIsRing &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type)   
 [STIsClosed &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)   
 [STPointOnSurface &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)   
 [LineString](linestring.md)  
  
  
