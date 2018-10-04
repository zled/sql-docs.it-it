---
title: Elemento ProcessingQuery (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ProcessingQuery Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProcessingQuery element
ms.assetid: d18e6f4b-c24c-4f73-8b85-4b6e8a82a695
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 055ec55609d60060385ebcce077119cf61549e1f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051131"
---
# <a name="processingquery-element-assl"></a>Elemento ProcessingQuery (ASSL)
  Contiene il testo con parametri della query da eseguire per la notifica dello stato di elaborazione incrementale.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<IncrementalProcessingNotification>  
   ...  
   <ProcessingQuery>...</ProcessingQuery>  
   ...  
</IncrementalProcessingNotification>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 La tabella nel [DataSourceView](../objects/datasourceview-element-assl.md) che fa riferimento il `ProcessingQuery` identificato dall'elemento di pari livello, [TableID](id-element-assl.md).  
  
 L'elemento che corrisponde al padre di `ProcessingQuery` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
