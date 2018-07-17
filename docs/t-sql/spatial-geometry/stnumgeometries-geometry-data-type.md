---
title: STNumGeometries (tipo di dati geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
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
ms.openlocfilehash: 7a34980aaad2ed7e78cb6b5058d792dd608d176f
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36252003"
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
  
  

