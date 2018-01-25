---
title: ShortestLineTo (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords: ShortestLineTo method (geometry)
ms.assetid: 39a2d0e4-4f93-4e94-a27e-6ad9537cfe74
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 08e83f7bb1993d3b55a48e5e3714c75d4bd33429
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="shortestlineto-geometry-data-type"></a>ShortestLineTo (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Restituisce un **LineString** istanza con due punti che rappresentano la distanza più breve tra le due **geometry** istanze. La lunghezza del **LineString** istanza restituita è la distanza tra i due **geometry** istanze.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.ShortestLineTo ( geometry_other )  
```  
  
## <a name="arguments"></a>Argomenti  
 *geometry_other*  
 Il secondo **geometry** istanza chiamante **geometry** istanza tenta di determinare la distanza più breve.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Osservazioni  
 Il metodo restituisce un **LineString** istanza con endpoint che si trovano sui bordi delle due pianificazioni **geometry** istanze da confrontare. La lunghezza del **LineString** restituiti corrisponde alla distanza minore tra i due **geometry** istanze. Un oggetto vuoto **LineString** istanza viene restituita quando le due **geometry** istanze si intersecano a vicenda.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-calling-shortestlineto-on-non-intersecting-instances"></a>A. Chiamata di ShortestLineTo() in istanze non intersecate  
 In questo esempio viene individuata la distanza più breve tra un'istanza `CircularString` e un'istanza `LineString` e viene restituita l'istanza `LineString` che collega i due punti:  
  
```
 DECLARE @g1 geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
 DECLARE @g2 geometry = 'LINESTRING(-4 7, 7 10, 3 7)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
### <a name="b-calling-shortestlineto-on-intersecting-instances"></a>B. Chiamata di ShortestLineTo() in istanze intersecate  
 In questo esempio viene restituita un'istanza `LineString` vuota perché l'istanza `LineString` interseca l'istanza `CircularString`:  
  
```
 DECLARE @g1 geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
 DECLARE @g2 geometry = 'LINESTRING(0 5, 7 10, 3 7)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [ShortestLineTo &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/shortestlineto-geography-data-type.md)  
  
  

