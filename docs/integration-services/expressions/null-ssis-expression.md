---
title: NULL (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- NULL function
- null values [Integration Services]
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 96994599bc0aea30d6cbb42ce1d9156c464839b7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654391"
---
# <a name="null-ssis-expression"></a>NULL (espressione SSIS)
  Restituisce un valore Null di un tipo di dati richiesto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
NULL(typespec)  
```  
  
## <a name="arguments"></a>Argomenti  
 *typespec*  
 Tipo di dati valido. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Tipi restituiti  
 Qualsiasi tipo di dati valido con valore Null.  
  
## <a name="remarks"></a>Remarks  
 Se l'argomento è Null, NULL restituirà Null.  
  
 Per ottenere un valore Null per determinati tipi di dati, è necessario specificare i parametri appropriati. Nella tabella seguente vengono elencati tali tipi di dati e i parametri corrispondenti.  
  
|Tipo di dati|Parametro|Esempio|  
|---------------|---------------|-------------|  
|DT_STR|*charcount*<br /><br /> *codepage*|(DT_STR,30,1252): esegue il cast di 30 caratteri al tipo di dati DT_STR utilizzando la tabella codici 1252.|  
|DT_WSTR|*charcount*|(DT_WSTR,20): esegue il cast di 20 caratteri al tipo di dati DT_WSTR.|  
|DT_BYTES|*bytecount*|(DT_BYTES,50): esegue il cast di 50 byte al tipo di dati DT_BYTES.|  
|DT_DECIMAL|*scala*|(DT_DECIMAL,2): esegue il cast di un valore numerico al tipo di dati DT_DECIMAL, utilizzando una scala pari a 2.|  
|DT_NUMERIC|*precisione*<br /><br /> *scala*|(DT_NUMERIC,10,3): esegue il cast di un valore numerico al tipo di dati DT_NUMERIC, utilizzando una precisione pari a 10 e una scala pari a 3.|  
|DT_TEXT|*codepage*|(DT_TEXT,1252): esegue il cast di un valore al tipo di dati DT_TEXT utilizzando la tabella codici 1252.|  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questi esempi viene restituito il valore Null per i tipi di dati DT_STR, DT_DATE e DT_BOOL.  
  
```  
NULL(DT_STR,10,1252)  
NULL(DT_DATE)  
NULL(DT_BOOL)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ISNULL &#40;espressione SSIS&#41;](../../integration-services/expressions/isnull-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
