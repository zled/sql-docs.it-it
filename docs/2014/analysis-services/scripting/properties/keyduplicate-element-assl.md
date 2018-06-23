---
title: Elemento KeyDuplicate (ASSL) | Documenti Microsoft
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
- KeyDuplicate Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyDuplicate
helpviewer_keywords:
- KeyDuplicate element
ms.assetid: d7000b8b-e81f-4401-8738-00c2e0f73a59
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 353c8d1eac5803db6f76014519d1c812813f535d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068577"
---
# <a name="keyduplicate-element-assl"></a>Elemento KeyDuplicate (ASSL)
  Determina la modalità [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gestisce un errore di chiave duplicata che si verifica durante l'elaborazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyDuplicate>...</KeyDuplicate>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*IgnoreError*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Gli errori di chiave duplicata vengono generati solo durante l'elaborazione della dimensione, quando una chiave dell'attributo si ripete più di una volta. Poiché le chiavi dell'attributo devono essere univoche, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] elimina i record duplicati. In genere gli errori di chiave duplicata indicano un difetto nella progettazione della dimensione, specificamente nelle relazioni tra attributi.  
  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*IgnoreError*|Consente di ignorare l'errore e continuare l'elaborazione.|  
|*ReportAndContinue*|Consente di segnalare l'errore e continuare l'elaborazione.|  
|*ReportAndStop*|Consente di segnalare l'errore e arrestare l'elaborazione.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `KeyDuplicate` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  