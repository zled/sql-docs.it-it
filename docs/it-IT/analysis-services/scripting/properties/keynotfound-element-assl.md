---
title: Elemento KeyNotFound (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
manager: kfile
ms.openlocfilehash: 2da3d588459c11a3f2ea9a3bcdbf59d5ba3f9060
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="keynotfound-element-assl"></a>Elemento KeyNotFound (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
