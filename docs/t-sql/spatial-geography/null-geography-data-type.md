---
title: Null (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 48df84157bf4b54c45c734cdc9338a95fc1b13ab
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="null-geography-data-type"></a>Null (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Fornisce un'istanza null di una proprietà di sola lettura di **geography** tipo.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Null  
```  
  
## <a name="arguments"></a>Argomenti  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo: **geography**  
  
 Tipo CLR: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene recuperata un'istanza `geography` Null.  
  
```  
DECLARE @g geography;   
SET @g = geography::[Null];  
SELECT @g  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geografia statici estesi](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  

