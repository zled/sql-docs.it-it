---
title: IsNull (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IsNull (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull method
ms.assetid: c031074f-bfda-4584-a3bf-4e7c324f237f
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9b9f65a3860b1b0d54231d3243fdfdf1902ae8ca
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="isnull-geography-data-type"></a>IsNull (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Una proprietà che specifica se il **geography** istanza è null. Restituisce 'TRUE' se l'istanza è Null. In caso contrario, restituisce 0.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.IsNull  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo: **bit**  
  
 Tipo CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Osservazioni  
 `IsNull`può essere utilizzato per verificare se un **geography** istanza è null. Questa verifica potrebbe produrre risultati piuttosto confusi, poiché restituisce 0 se l'istanza è diversa da Null, ma restituisce Null se l'istanza è Null.  
  
 Questo metodo viene utilizzato principalmente per la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] infrastruttura; si consiglia di utilizzare il predicato T-SQL IS NULL per verificare se un **geography** istanza è null. Per ulteriori informazioni su T-SQL predicato IS NULL, vedere [IS NULL &#40; Transact-SQL &#41; ](../../t-sql/queries/is-null-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
