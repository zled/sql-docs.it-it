---
title: Punto | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Point geometry subtype [SQL Server]
- geometry data type [SQL Server], spatial data
ms.assetid: 2a596ec4-8b2f-4962-bcb4-e5c8f77edad5
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e0bc6a80c1ce2fc6e9646114d5d5f856d89bdd04
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156892"
---
# <a name="point"></a>Punto
  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati spaziali, un `Point` è un oggetto 0-dimensionale che rappresenta un'unica posizione e può contenere valori Z (innalzamento) e M (misura).  
  
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
 [MultiPoint](multipoint.md)   
 [STX &#40;Tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/stx-geometry-data-type)   
 [STY &#40;Tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/sty-geometry-data-type)   
 [Dati spaziali &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  
