---
title: GETUTCDATE (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6fb17eed079feabfaf27e0d757e8be48338bcb08
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35408233"
---
# <a name="getutcdate-ssis-expression"></a>GETUTCDATE (espressione SSIS)
  Viene restituita la data corrente del sistema in base all'ora UTC (Universal Time Coordinated o ora di Greenwich) utilizzando un formato DT_DBTIMESTAMP. La funzione GETUTCDATE non accetta argomenti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
GETUTCDATE()  
```  
  
## <a name="arguments"></a>Argomenti  
 None  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene restituito l'anno della data corrente in base all'ora UTC (Universal Time Coordinated o ora di Greenwich).  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 In questo esempio viene restituito il numero di giorni tra una data nella colonna **ModifiedDate** e la data UTC corrente.  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 In questo esempio vengono aggiunti tre mesi alla data UTC corrente.  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## <a name="see-also"></a>Vedere anche  
 [GETDATE &#40;espressione SSIS&#41;](../../integration-services/expressions/getdate-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
