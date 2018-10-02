---
title: STNumGeometries (tipo di dati geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STNumGeometries (geometry Data Type)
- STNumGeometries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumGeometries (geometry Data Type)
ms.assetid: 9402b03d-3039-42ca-ac59-f96b7f1a48de
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1c48a3560f960c90e8426a67e5b1b85af933d2ba
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47804695"
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
  
  

