---
title: Long (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Long_TSQL
- Long
dev_langs:
- TSQL
helpviewer_keywords:
- Long method
ms.assetid: bedbeced-70b8-4569-84f3-f86bfb04ce50
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 88b07b5ea327b3d35946991e5a776d9d0fdea8ad
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36243423"
---
# <a name="long-geography-data-type"></a>Long (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Proprietà della longitudine dell'istanza **geography**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.Long  
```  
  
## <a name="return-value"></a>Valore restituito  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **float**  
  
 Tipo CLR: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 Nel modello OpenGIS, la proprietà Long viene definita solo su istanze **geography** costituite da un unico punto. Questa proprietà restituirà Null se le istanze **geography** contengono più di un unico punto. La proprietà è precisa e di sola lettura.  
  
## <a name="examples"></a>Esempi  
 Questo esempio crea un'istanza **Point** e recupera la longitudine del punto.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.Long;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze geografiche](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
