---
title: STNumGeometries (tipo di dati geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d237641d719df7c9549896ea12218e2de49d1fd8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="stnumgeometries-geometry-data-type"></a>STNumGeometries (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce il numero di geometrie che costituiscono un'istanza **geometry**.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STNumGeometries ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **int**  
  
 Tipo CLR restituito: **SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 Questo metodo restituisce 1 se l'istanza **geometry** non è un'istanza **MultiPoint**, **MultiLineString**, **MultiPolygon** o **GeometryCollection** e 0 se l'istanza **geometry** è vuota.  
  
> [!NOTE]  
>  Se in **GeometryCollection** sono presenti elementi vuoti annidati, `STNumGeometries()` non restituirà 0. Sebbene gli elementi presenti nell'istanza **GeometryCollection** siano vuoti, l'istanza stessa non è un set vuoto.  
  
  

