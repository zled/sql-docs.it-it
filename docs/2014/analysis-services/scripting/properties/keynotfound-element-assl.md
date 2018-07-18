---
title: Elemento KeyNotFound (ASSL) | Microsoft Docs
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
- KeyNotFound Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyNotFound
helpviewer_keywords:
- KeyNotFound element
ms.assetid: 2a93bbfa-2409-4e94-8b68-926532895a4c
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 58228d8f4029fecf22062a3e3c5c0c9adf3eafe1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281807"
---
# <a name="keynotfound-element-assl"></a>Elemento KeyNotFound (ASSL)
  Specifica la modalità [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] risponde quando viene rilevato un errore di integrità referenziale.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyNotFound>...</KeyNotFound>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*ReportAndContinue*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Si verificano errori di integrità referenziale quando per un valore di chiave esterna in una tabella dipendente non è presente una voce corrispondente nella tabella padre. Questo errore si verifica quando [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] elabora una dimensione in cui la tabella dei fatti fa riferimento a un valore di chiave esterna che non è presente nella tabella delle dimensioni per la dimensione oppure quando [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] elabora una partizione quando la tabella principale delle dimensioni per una dimensione inclusa nella partizione fa riferimento a un valore di chiave che non è presente in un'altra tabella delle dimensioni associata. Nel caso di gerarchie padre-figlio e di attributi padre, questo errore può inoltre verificarsi quando la tabella principale delle dimensioni per una dimensione inclusa nella partizione fa riferimento a un valore di chiave che non è presente nella stessa tabella delle dimensioni.  
  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*IgnoreError*|Consente di ignorare l'errore e continuare l'elaborazione.|  
|*ReportAndContinue*|Consente di segnalare l'errore e continuare l'elaborazione.|  
|*ReportAndStop*|Consente di segnalare l'errore e arrestare l'elaborazione.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `KeyNotFound` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
