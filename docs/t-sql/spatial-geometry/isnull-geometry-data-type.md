---
title: IsNull (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IsNull (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull (geometry Data Type)
ms.assetid: f95813a5-26c0-48aa-bfb8-56d2a0980788
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: 5e213bd847f2d5836802d93ade5fa46f3dc3d1a9
ms.contentlocale: it-it
ms.lasthandoff: 09/13/2017

---
# <a name="isnull-geometry-data-type"></a>IsNull (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Il tipo di un **geometry** istanza è null. Restituisce 0 se l'istanza è diversa da Null.
  
## <a name="syntax"></a>Sintassi  
  
```  
.IsNull  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo: **bit**  
  
 Tipo CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Osservazioni  
 `IsNull`può essere utilizzato per verificare se un **geometry** istanza è null. Questa verifica potrebbe produrre risultati piuttosto confusi, poiché restituisce 0 se l'istanza è diversa da Null, ma restituisce Null se l'istanza è Null.  
  
 Questo metodo viene utilizzato principalmente dall'infrastruttura di SQL Server. Non è consigliabile utilizzare `IsNull` per verificare se un'istanza è Null.  
  

## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geometria](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  


