---
title: Point (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Point
- Point_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Point method
- Point (geography Data Type)
ms.assetid: 0dc6f422-7aae-4016-b7f4-3289fa8f989c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4de164536b75684d8c019a9f93db4a9b21415650
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759809"
---
# <a name="point-geography-data-type"></a>Point (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Costruisce un'istanza **geography** che rappresenta un'istanza **Point** dai relativi valori di latitudine e longitudine e un identificatore SRID.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Point ( Lat, Long, SRID )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Lat*  
 Espressione **float** che rappresenta la coordinata X dell'istanza **Point** da generare.  
  
 *Long*  
 Espressione **float** che rappresenta la coordinata Y dell'istanza **Point** da generare. Per altre informazioni sui valori validi di latitudine e longitudine, vedere [Point](../../relational-databases/spatial/point.md).  
  
 *SRID*  
 Espressione **int** che rappresenta l'identificatore SRID dell'istanza **geography** da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
> [!NOTE]  
>  Gli argomenti del metodo Point (tipo di dati geography) hanno coordinate inverse rispetto a WKT.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `Point()` per creare un'istanza `geography`.  
  
```  
DECLARE @g geography;   
SET @g = geography::Point(47.65100, -122.34900, 4326)  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi geography statici estesi](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
