---
title: risultati Element (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- results Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.results
- urn:schemas-microsoft-com:xml-analysis#results
- http://schemas.microsoft.com/analysisservices/2003/engine#results
helpviewer_keywords:
- results element
ms.assetid: 3249a17a-7bfa-4753-b605-8f611ba7ae2b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e99728941db468f361535fa675281f880ad3133a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48091361"
---
# <a name="results-element-xmla"></a>Elemento results (XMLA)
  Contiene una raccolta di [radice](root-element-xmla.md) gli elementi restituiti dai [Execute](../xml-elements-methods-execute.md) metodo utilizzando il [Batch](../xml-elements-commands/batch-element-xmla.md) comando.  
  
 **Namespace** http://schemas.microsoft.com/analysisservices/2003/xmla-multipleresults  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<return>  
   <results>  
      <root>...</root>  
   </results>  
</return>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[restituire](return-element-xmla.md)|  
|Elementi figlio|[root](root-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Se un comando `Batch` viene eseguito dal metodo `Execute`, l'elemento `return` contiene un singolo elemento `results` anziché un singolo elemento `root`. Il contenuto dell'elemento `results` dipende dalle impostazioni utilizzate per eseguire il comando `Batch`.  
  
 Per i comandi `Batch` non transazionali, l'elemento `results` contiene un elemento `root` per ogni comando eseguito dal comando `Batch`, sia che l'esecuzione del comando abbia esito positivo o negativo. Per i comandi `Batch` transazionali, l'elemento `results` contiene solo un elemento `root` che contiene le informazioni sull'errore per il comando non riuscito all'interno del comando `Batch`.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
