---
title: NumRings (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- NumRings_TSQL
- NumRings
dev_langs:
- TSQL
helpviewer_keywords:
- NumRings method
ms.assetid: 0e4e4fa2-b608-4cc4-98ba-0845ddb4214c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6a553dc687ec9f1aef15e1455e80106f3612dd9b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47750569"
---
# <a name="numrings-geography-data-type"></a>NumRings (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il numero totale di anelli in un'istanza **Polygon**. Nel tipo **geography** di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gli anelli esterni e interni non vengono distinti poiché qualsiasi anello può essere considerato come l'anello esterno.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.NumRings ()  
```  
  
## <a name="return-type"></a>Tipo restituito  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **int**  
  
 Tipo CLR restituito: **SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 Questo metodo restituirà Null se l'istanza non è **Polygon** e restituirà 0 se l'istanza è vuota. Il metodo è preciso.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio viene creata un'istanza `Polygon` con due anelli e viene confermata la presenza di due anelli per l'istanza stessa.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.NumRings();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze geografiche](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
