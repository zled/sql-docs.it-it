---
title: MultiPoint | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: spatial
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 6d693f6d512e3862071fedbb2f190e68d3f73b2c
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39549071"
---
# <a name="multipoint"></a>MultiPoint
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Un **MultiPoint** è una raccolta di zero o più punti. Il limite di un'istanza **MultiPoint** è vuoto.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente è creata un'istanza `geometry MultiPoint` con SRID 23 e due punti: uno con le coordinate (2, 3), e l'altro con le coordinate (7, 8) e un valore Z di 9,5.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 Questa istanza `MultiPoint` può essere anche espressa utilizzando `STMPointFromText()` come mostrato di seguito.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPointFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 Nell'esempio seguente viene utilizzato il metodo `STGeometryN()` per recuperare una descrizione del primo punto nella raccolta.  
  
```  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Punto](../../relational-databases/spatial/point.md)   
 [Dati spaziali &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
