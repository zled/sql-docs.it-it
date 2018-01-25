---
title: STCurveN (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STCurveN
- STCurveN_TSQL
dev_langs: TSQL
helpviewer_keywords: STCurveN method (geography)
ms.assetid: 99ef7100-2c4b-4f07-8d66-b343da94b023
caps.latest.revision: "16"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 59709f07fa84c24942ed14a8f8af7e776643913f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="stcurven-geography-data-type"></a>STCurveN (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce la curva specificata da un **geography** che è un **LineString**, **CircularString**, o **CompoundCurve**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STCurveN( n )  
```  
  
## <a name="arguments"></a>Argomenti  
 *n*  
 È un **int** espressione compreso tra 1 e il numero di curve nel **geography** istanza.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="exceptions"></a>Eccezioni  
 Se n < 1 una **ArgumentOutOfRangeException** viene generata un'eccezione.  
  
## <a name="remarks"></a>Osservazioni  
 **NULL** viene restituito quando si verifica i criteri seguenti.  
  
-   Il **geography** istanza viene dichiarata, ma non viene creata un'istanza  
  
-   Il **geography** istanza è vuota  
  
-   n supera il numero di curve presenti il **geography** istanza (vedere [STNumCurves &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/stnumcurves-geography-data-type.md)  
  
-   La dimensione per la **geography** istanza non è uguale (vedere [STDimension &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/stdimension-geography-data-type.md)  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-stcurven-on-a-circularstring"></a>A. Utilizzo di STCurveN() in CircularString  
 Nell'esempio seguente viene restituita la seconda curva in un **CircularString** istanza:  
  
```
 DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Nell'esempio viene restituito.  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
### <a name="b-using-stcurven-on-a-compoundcurve"></a>B. Utilizzo di STCurveN() in CompoundCurve  
 Nell'esempio seguente viene restituita la seconda curva in un **CompoundCurve** istanza:  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Nell'esempio viene restituito.  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
### <a name="c-using-stcurven-on-a-compoundcurve-containing-three-circularstrings"></a>C. Utilizzo di STCurveN() in un'istanza CompoundCurve che contiene tre istanze CircularString  
 Nell'esempio seguente viene utilizzato un **CompoundCurve** istanza che combina tre separato **CircularString** curva di istanze nella stessa sequenza all'esempio precedente:  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE (CIRCULARSTRING (-122.358 47.653, -122.348 47.649, -122.348 47.658), CIRCULARSTRING(-122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Nell'esempio viene restituito.  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
 `STCurveN()` restituisce gli stessi risultati indipendentemente dal formato Well-Known Text (WKT) utilizzato.  
  
### <a name="d-testing-for-validity-before-calling-stcurve"></a>D. Verifica della validità prima della chiamata a STCurve()  
 Nell'esempio seguente viene illustrato come assicurarsi che  *n*  sia valido prima di chiamare il metodo stcurven ():  
  
```
 DECLARE @g geography;  
 DECLARE @n int;  
 SET @n = 2;  
 SET @g = geography::Parse('LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');  
 IF @n >= 1 AND @n <= @g.STNumCurves()  
 BEGIN  
 SELECT @g.STCurveN(@n).ToString();  
 END
  ```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze geografiche](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
