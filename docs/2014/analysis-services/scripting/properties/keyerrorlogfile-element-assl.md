---
title: Elemento KeyErrorLogFile (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- KeyErrorLogFile Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyErrorLogFile
helpviewer_keywords:
- KeyErrorLogFile element
ms.assetid: 1455bb54-03f7-4f25-9d4d-ab75231dd958
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 77a636531be4d6c4e84403f12e0df3bbb8ead9fe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190431"
---
# <a name="keyerrorlogfile-element-assl"></a>Elemento KeyErrorLogFile (ASSL)
  Contiene il nome del file per la registrazione di errori dell'elaborazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyErrorLogFile>...</KeyErrorLogFile>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Note  
 L'elemento che corrisponde al padre di `KeyErrorLogFile` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ErrorConfiguration>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
