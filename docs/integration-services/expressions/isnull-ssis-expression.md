---
title: ISNULL (espressione SSIS) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: dd74ffbf491733826eef4cf61530e838033d7e3d
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="isnull-ssis-expression"></a>ISNULL (espressione SSIS)
  Restituisce un risultato booleano che varia a seconda che un'espressione abbia o meno un valore Null.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ISNULL(expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 Espressione valida con qualsiasi tipo di dati.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_BOOL  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene restituito TRUE se nella colonna **DiscontinuedDate** è contenuto un valore Null.  
  
```  
ISNULL(DiscontinuedDate)  
```  
  
 In questo esempio viene restituito il testo "Unknown last name" se il valore nella colonna **LastName** è Null, in caso contrario viene restituito il valore in **LastName**.  
  
```  
ISNULL(LastName)? "Unknown last name":LastName  
```  
  
 In questo esempio se la colonna **DaysToManufacture** ha valore Null, verrà sempre restituito TRUE indipendentemente dal valore della variabile **AddDays**.  
  
```  
ISNULL(DaysToManufacture + @AddDays)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni &#40; Espressione SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)   
 [COALESCE &#40; Transact-SQL &#41;](../../t-sql/language-elements/coalesce-transact-sql.md)  
  
  

