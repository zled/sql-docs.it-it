---
title: STNumGeometries (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STNumGeometries (geometry Data Type)
- STNumGeometries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumGeometries (geometry Data Type)
ms.assetid: 9402b03d-3039-42ca-ac59-f96b7f1a48de
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c8ca87eeff2f807b55754d9d9adf19ebf03a4fd8
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stnumgeometries-geometry-data-type"></a>STNumGeometries (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce il numero di geometrie che costituiscono un **geometry** istanza.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STNumGeometries ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **int**  
  
 Tipo CLR restituito: **SqlInt32**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo restituisce 1 se il **geometry** istanza non è un **MultiPoint**, **MultiLineString**, **MultiPolygon**, o  **GeometryCollection** istanza e 0 in caso di **geometry** istanza è vuota.  
  
> [!NOTE]  
>  Se un **GeometryCollection** include nidificati gli elementi vuoti, `STNumGeometries()` non restituirà 0. Anche se gli elementi di **GeometryCollection** istanza sono vuoti, l'istanza non è un set vuoto.  
  
  


