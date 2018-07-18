---
title: Elemento KeyErrorLogFile (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 067e509f6be5657e1e748738bc6910fed977fd41
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323051"
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
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento che corrisponde al padre di `KeyErrorLogFile` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ErrorConfiguration>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
