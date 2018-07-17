---
title: Z (tipo di dati geometry) | Microsoft Docs
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
- Z (geometry Data Type)
- Z_(geometry_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Z (geometry Data Type)
ms.assetid: a62ed736-44df-4591-9109-ce90e1df9bd3
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 01f303a935423fc652b8e1254ccbec4be9712129
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36253303"
---
# <a name="z-geometry-data-type"></a>Z (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Valore Z (elevazione) dell'istanza. La semantica del valore di elevazione è definita dall'utente.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.Z  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **float**  
  
 Tipo CLR: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 Il valore di questa proprietà sarà Null se l'istanza di geometria non è un punto e per qualsiasi istanza **Point** per cui la proprietà non è impostata.  
  
 Questa proprietà è di sola lettura.  
  
 Le coordinate Z non vengono utilizzate in alcun calcolo eseguito dalla libreria né vengono trasferite ad alcun calcolo della libreria.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `Point` con valori Z (innalzamento) e M (misura) e viene utilizzato `Z` per recuperare il valore Z dell'istanza.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(1 2 3 4)', 0);  
SELECT @g.Z;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [M &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/m-geometry-data-type.md)   
 [AsTextZM &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/astextzm-geometry-data-type.md)   
 [Metodi estesi sulle istanze di geometria](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

