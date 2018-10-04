---
title: Elemento ServerProperty (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ServerProperty Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SERVERPROPERTY
helpviewer_keywords:
- ServerProperty element
ms.assetid: f152a1b5-0972-40d8-907f-f131c2a108bb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d84d9fc4bb78969265399d2a67207ea15e753f39
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185771"
---
# <a name="serverproperty-element-assl"></a>Elemento ServerProperty (ASSL)
  Definisce una proprietà server associata a un [Server](server-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ServerProperties>  
   <ServerProperty>  
      <Name>...</Name>  
      <Value>...</Value>  
            <RequiresRestart>...</RequiresRestart>  
            <PendingValue>...</PendingValue>  
      <DefaultValue>...</DefaultValue>  
      <DisplayFlag>...</DisplayFlag>  
   </ServerProperty>  
</ServerProperties>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[ServerProperties](../collections/serverproperties-element-assl.md)|  
|Elementi figlio|[DefaultValue](../properties/value-element-assl.md), [DisplayFlag](../properties/displayflag-element-assl.md), [Name](../properties/name-element-assl.md), [PendingValue](../properties/pendingvalue-element-assl.md), [RequiresRestart](../properties/requiresrestart-element-assl.md), [valore](../properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 Il `ServerProperty` elemento descrive i dati e metadati per una proprietà server associata a un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. A differenza di elementi contenuti dalle altre raccolte in Analysis Services Scripting language (ASSL), l'elemento `ServerProperty` utilizza coppie nome/valore anziché elementi denominati in modo esplicito per descrivere le proprietà server. Le coppie nome/valore forniscono flessibilità ed estensibilità.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento server &#40;ASSL&#41;](server-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
