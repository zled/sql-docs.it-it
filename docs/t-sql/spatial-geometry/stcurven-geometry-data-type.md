---
title: STCurveN (tipo di dati geometry) | Documenti Microsoft
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
helpviewer_keywords: STCurveN method (geometry)
ms.assetid: 64adf1a1-3a41-41fb-b7d1-44390c3e4ea9
caps.latest.revision: "21"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c48fcaa75233ecc6fa14b8e1e0323078d8574379
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="stcurven-geometry-data-type"></a>STCurveN (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Restituisce la curva specificata da un **geometry** che è un **LineString**, **CircularString**, **CompoundCurve**, o  **MultiLineString**.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STCurveN ( curve_index )  
```  
  
## <a name="arguments"></a>Argomenti  
 *curve_index*  
 È un **int** espressione compreso tra 1 e il numero di curve nel **geometry** istanza.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="exceptions"></a>Eccezioni  
 Se *curve_index* < 1 una `ArgumentOutOfRangeException` viene generata un'eccezione.  
  
## <a name="remarks"></a>Osservazioni  
 **NULL** viene restituito quando si verifica una delle operazioni seguenti:  
  
-   il **geometry** istanza viene dichiarata ma non creare un'istanza  
  
-   il **geometry** istanza è vuota  
  
-   *curve_index* supera il numero di curve presenti il **geometry** istanza  
  
-   il **geometry** istanza è un **punto**, **MultiPoint**, **poligono**, **CurvePolygon**, o  **MultiPolygon**  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-stcurven-on-a-circularstring-instance"></a>A. Utilizzo di STCurves() in un'istanza CircularString  
 Nell'esempio seguente viene restituita la seconda curva in un'istanza `CircularString`:  
  
```
 DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Nell'esempio riportato in precedenza in questo argomento viene restituito:  
  
 `CIRCULARSTRING (3 6.3246, 0 7, -3 6.3246)`  
  
### <a name="b-using-stcurven-on-a-compoundcurve-instance-with-one-circularstring-instance"></a>B. Utilizzo di STCurveN() in un'istanza CompoundCurve con un'istanza CircularString  
 Nell'esempio seguente viene restituita la seconda curva in un'istanza `CompoundCurve`:  
  
```
 DECLARE @g geometry = 'COMPOUNDCURVE(CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Nell'esempio riportato in precedenza in questo argomento viene restituito:  
  
 `CIRCULARSTRING (3 6.3246, 0 7, -3 6.3246)`  
  
### <a name="c-using-stcurven-on-a-compoundcurve-instance-with-three-circularstring-instances"></a>C. Utilizzo di STCurveN() in un'istanza CompoundCurve con tre istanze CircularString  
 Nell'esempio seguente viene utilizzata un'istanza `CompoundCurve` che combina tre istanze `CircularString` separate nella stessa sequenza di curve dell'esempio precedente:  
  
```
 DECLARE @g geometry = 'COMPOUNDCURVE (CIRCULARSTRING (0 0, 1 2.1082, 3 6.3246), CIRCULARSTRING(3 6.3246, 0 7, -3 6.3246), CIRCULARSTRING(-3 6.3246, -1 2.1082, 0 0))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Nell'esempio riportato in precedenza in questo argomento viene restituito:  
  
 `CIRCULARSTRING (3 6.3246, 0 7, -3 6.3246)`  
  
 Si noti che i risultati sono gli stessi dei tre esempi precedenti. Indipendentemente dal formato WKT (well-known text) utilizzato per immettere la stessa sequenza di curve, i risultati restituiti da `STCurveN()` sono gli stessi quando viene utilizzata un'istanza `CompoundCurve`.  
  
### <a name="d-validating-the-parameter-before-calling-stcurven"></a>D. Convalida del parametro prima della chiamata a STCurveN()  
 Nell'esempio seguente viene illustrato come assicurarsi che `@n` sia valido prima di chiamare il `STCurveN()`metodo:  
  
```
 DECLARE @g geometry;  
 DECLARE @n int;  
 SET @n = 3;  
 SET @g = geometry::Parse('CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)');  
 IF @n >= 1 AND @n <= @g.STNumCurves()  
 BEGIN  
 SELECT @g.STCurveN(@n).ToString();  
 END
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [STNumCurves &#40; tipo di dati geometry &#41;](../../t-sql/spatial-geometry/stnumcurves-geometry-data-type.md)   
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

