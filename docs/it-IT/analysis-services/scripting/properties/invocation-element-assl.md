---
title: Elemento Invocation (ASSL) | Documenti Microsoft
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
- Invocation Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Invocation
helpviewer_keywords:
- Invocation element
ms.assetid: f6bf64ad-ae57-4d46-bf92-1d07a65378bb
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3c2426f3870eb1658097e2448c9f7f6de1e91ff5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="invocation-element-assl"></a>Elemento Invocation (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Specifica come un [azione](../../../analysis-services/scripting/objects/action-element-assl.md) deve essere richiamato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action>  
   ...  
   <Invocation>...</Invocation>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Interattivo*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Azione](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 La chiamata di un'azione dipende dall'applicazione client. Il **chiamata** elemento suggerisce a un'applicazione client come un'azione deve essere gestita e non indica all'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] come richiamare un'azione.  
  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|*Interattivo*|Richiamato in modo interattivo dall'utente.|  
|*Su apertura*|Richiamato quando un'applicazione client apre l'oggetto.|  
|*Batch*|Richiamato da un comando dell'elaborazione batch.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **chiamata** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
