---
title: CollectionAggregate (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- CollectionAggregate method (geography)
ms.assetid: e49a644a-dbf2-46c3-98f5-4b3ec197e2ad
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ae882f4c0f4f1a1f489b22cac14b84933f96ecf2
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="collectionaggregate-geography-data-type"></a>CollectionAggregate (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Crea un **GeometryCollection** istanza da un set di **geography** oggetti.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ConvexHullAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>Argomenti  
 *geography_operand*  
 È un **geography** colonna di tabella di tipo che rappresenta un set di **geography** oggetti da includere nel **GeometryCollection** istanza.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
## <a name="exception"></a>Exception  
 Genera un'eccezione `FormatException` in presenza di valori di input non validi. Vedere [STIsValid &#40; tipo di dati geography &#41;](../../t-sql/spatial-geography/stisvalid-geography-data-type.md)  
  
## <a name="remarks"></a>Osservazioni  
 Metodo **null** quando l'input è vuoto o l'input dispone di SRID diversi. Vedere [identificatori SRID &#40; Identificatori SRID &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
 Metodo ignora **null** input.  
  
> [!NOTE]  
>  Metodo **null** se tutti i valori immessi sono **null**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito un `GeometryCollection` istanza che contiene un set di **geography** oggetti.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT geography::CollectionAggregate(SpatialLocation).ToString() AS SpatialLocation  
 FROM Person.Address  
 WHERE City LIKE ('Bothell')
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geografia statici estesi](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  

