---
title: Null (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Null (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- Null (geography Data Type)
- Null method
ms.assetid: bb464b06-86e0-4b8b-ad78-04bd33b6069c
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 06661e5a6f182e47839780ea77cb60dfd20ca2eb
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36245733"
---
# <a name="null-geography-data-type"></a>Null (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Proprietà di sola lettura che restituisce un'istanza Null del tipo **geography**.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Null  
```  
  
## <a name="arguments"></a>Argomenti  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Tipo CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene recuperata un'istanza `geography` Null.  
  
```  
DECLARE @g geography;   
SET @g = geography::[Null];  
SELECT @g  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi geography statici estesi](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
