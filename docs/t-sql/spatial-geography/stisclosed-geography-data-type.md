---
title: STIsClosed (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STIsClosed (geography Data Type)
- STIsClosed_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STIsClosed method
ms.assetid: eba1643f-07c4-4500-8643-b7e90f908147
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 832e2a44f091e256350988c20410e05559aaa2ca
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36245373"
---
# <a name="stisclosed-geography-data-type"></a>STIsClosed (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce 1 se i punti di inizio e di fine dell'istanza **geography** specificata sono gli stessi. Restituisce 1 per i tipi relativi a una raccolta **geography** se ogni istanza **geography** contenuta è chiusa. Restituisce 0 se l'istanza non è chiusa.  
  
 Questo metodo con tipo di dati **geography** supporta le istanze **FullGlobe** o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STIsClosed ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Questo metodo restituisce 0 se una figura di un'istanza **geography** è costituita da punti o se l'istanza è vuota.  
  
 Questo metodo restituisce True se un'istanza **FullGlobe** è **Polygon** o un altro tipo di istanza.  
  
 Tutte le istanze **Polygon** sono considerate chiuse.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `Polygon` e viene utilizzato `STIsClosed()` per verificare se l'istanza `Polygon` è chiusa.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STIsClosed();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze geografiche](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
