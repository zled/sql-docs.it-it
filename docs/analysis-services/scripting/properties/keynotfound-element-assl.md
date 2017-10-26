---
title: Elemento KeyNotFound (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- KeyNotFound Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- KeyNotFound
helpviewer_keywords:
- KeyNotFound element
ms.assetid: 2a93bbfa-2409-4e94-8b68-926532895a4c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b193d4a9a7c87138287b28286a65e867430a0d36
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*ReportAndContinue*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Si verificano errori di integrità referenziale quando per un valore di chiave esterna in una tabella dipendente non è presente una voce corrispondente nella tabella padre. Questo errore si verifica quando [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] elabora una dimensione in cui la tabella dei fatti fa riferimento a un valore di chiave esterna che non è presente nella tabella delle dimensioni per la dimensione oppure quando [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] elabora una partizione quando la tabella principale delle dimensioni per una dimensione inclusa nella partizione fa riferimento a un valore di chiave che non è presente in un'altra tabella delle dimensioni associata. Nel caso di gerarchie padre-figlio e di attributi padre, questo errore può inoltre verificarsi quando la tabella principale delle dimensioni per una dimensione inclusa nella partizione fa riferimento a un valore di chiave che non è presente nella stessa tabella delle dimensioni.  
  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*IgnoreError*|Consente di ignorare l'errore e continuare l'elaborazione.|  
|*ReportAndContinue*|Consente di segnalare l'errore e continuare l'elaborazione.|  
|*ReportAndStop*|Consente di segnalare l'errore e arrestare l'elaborazione.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **KeyNotFound** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

