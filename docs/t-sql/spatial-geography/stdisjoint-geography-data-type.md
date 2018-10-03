---
title: STDisjoint (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STDisjoint (geography Data Type)
- STDisjoint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STDisjoint
ms.assetid: 98328a02-e018-47d6-aa93-de162b8aef62
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 57071fc6530f8fdcb6d2a0eab83fea1bf43ac42e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687331"
---
# <a name="stdisjoint-geography-data-type"></a>STDisjoint (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce 1 se un'istanza **geography** è disgiunta a livello spaziale da un'altra istanza **geography**. In caso contrario, restituisce 0.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STDisjoint ( other_geography )  
```  
  
## <a name="arguments"></a>Argomenti  
 *other_geography*  
 Altra istanza **geography** da confrontare con l'istanza sulla quale viene chiamato STDisjoint().  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Due istanze **geography** sono disgiunte se l'intersezione dei relativi set di punti è vuota.  
  
 Questo metodo restituisce sempre Null se gli identificatori SRID delle istanze **geography** non corrispondono.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato `STDisjoint()` per verificare se due istanze `geography` sono disgiunte a livello spaziale.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SET @h = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.STDisjoint(@h);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze geografiche](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
