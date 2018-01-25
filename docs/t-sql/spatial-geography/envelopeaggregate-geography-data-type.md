---
title: EnvelopeAggregate (tipo di dati geography) | Documenti Microsoft
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EnvelopeAggregate_TSQL
- EnvelopeAggregate
dev_langs: TSQL
helpviewer_keywords: EnvelopeAggregate method (geography)
ms.assetid: 4947797f-edb8-490f-beca-37df9ec06954
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 62e288175b4c8f6f33e3996046fa24ffccaa8b2c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="envelopeaggregate-geography-data-type"></a>EnvelopeAggregate (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Restituisce un oggetto di delimitazione per un determinato set di **geography** oggetti. Il valore risultante **geography** oggetto contiene più segmenti di arco circolare.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
EnvelopeAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>Argomenti  
 *geography_operand*  
 È un **geography** colonna della tabella che contiene il set di tipo **geography** operazione di aggregazione di oggetti su cui eseguire una busta.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geography**  
  
## <a name="remarks"></a>Osservazioni  
 Oggetto **FullGlobe** oggetto viene restituito quando l'oggetto di delimitazione risultante è maggiore di un emisfero. Il metodo non è preciso.  
  
 Metodo **null** se l'input dispone di SRID diversi. Vedere [identificatori SRID &#40; Identificatori SRID &#41; ](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
 Metodo ignora **null** input.  
  
> [!NOTE]  
>  Metodo **null** se tutti i valori immessi sono **null**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eseguito un `EnvelopeAggregate` su un set di **geography** punti percorso all'interno di una città.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT City,  
 geography::EnvelopeAggregate(SpatialLocation) AS SpatialLocation  
 FROM Person.Address  
 WHERE PostalCode LIKE('981%')  
 GROUP BY City;
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi geography statici estesi](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
