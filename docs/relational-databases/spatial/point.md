---
title: Punto | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Point geometry subtype [SQL Server]
- geometry data type [SQL Server], spatial data
ms.assetid: 2a596ec4-8b2f-4962-bcb4-e5c8f77edad5
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3ab4b354292130b01c73f771c221a13b595bdbdc
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="point"></a>Punto
  Nei dati spaziali [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , un **punto** è un oggetto senza dimensioni che rappresenta una sola posizione e può contenere valori Z (innalzamento) e M (misura).  
  
## <a name="geography-data-type"></a>Tipo di dati geography  
 Il tipo Punto del tipo di dati geography rappresenta una singola posizione in cui *Lat* indica la latitudine e *Long* la longitudine. I valori di latitudine e longitudine vengono misurati in gradi. I valori della latitudine sono compresi sempre nell'intervallo [-90, 90], quelli al di fuori genereranno un'eccezione. I valori della longitudine sono compresi sempre nell'intervallo [-180, 180], quelli al fuori, per rientrare in tale intervallo, vengono arrotondati. Ad esempio, se il valore immesso per la longitudine è 190, verrà arrotondato a -170. *SRID* rappresenta l'ID di riferimento spaziale dell'istanza **geography** da restituire.  
  
## <a name="geometry-data-type"></a>Tipo di dati geometry  
 Il tipo Punto per il tipo di dati geometry rappresenta una singola posizione in cui *X* e *Y* rappresentano rispettivamente le coordinate X e Y del punto generato. *SRID* rappresenta l'ID di riferimento spaziale dell'istanza **geometry** da restituire.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente illustra come creare un'istanza `geometry Point`che rappresenta il punto (3, 4) con un SRID pari a 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT (3 4)', 0);  
```  
  
 L'esempio successivo illustra come creare un'istanza `geometry``Point` che rappresenta il punto (3, 4) con un valore Z (innalzamento) pari a 7, un valore M (misura) pari a 2,5 e SRID predefinito a 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 7 2.5)');  
```  
  
 L'esempio finale restituisce i valori X, Y, Z e M per l'istanza `geometry``Point` .  
  
```  
SELECT @g.STX;  
SELECT @g.STY;  
SELECT @g.Z;  
SELECT @g.M;  
```  
  
 I valori Z e M possono essere specificati in modo esplicito come NULL, così come mostrato nell'esempio seguente.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 NULL NULL)');  
```  
  
## <a name="see-also"></a>Vedere anche  
 [MultiPoint](../../relational-databases/spatial/multipoint.md)   
 [STX &#40;Tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stx-geometry-data-type.md)   
 [STY &#40;Tipo di dati geometry&#41;](../../t-sql/spatial-geometry/sty-geometry-data-type.md)   
 [Dati spaziali &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
