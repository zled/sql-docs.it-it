---
title: Elemento ServerProperty (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ServerProperty Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: SERVERPROPERTY
helpviewer_keywords: ServerProperty element
ms.assetid: f152a1b5-0972-40d8-907f-f131c2a108bb
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: edf7c78a2486d7e09dfb8eeb437b1215bff50bc1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="serverproperty-element-assl"></a>Elemento ServerProperty (ASSL)
  Definisce una proprietà del server associata a un [Server](../../../analysis-services/scripting/objects/server-element-assl.md) elemento.  
  
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[ServerProperties](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)|  
|Elementi figlio|[DefaultValue](../../../analysis-services/scripting/properties/defaultvalue-element-assl.md), [DisplayFlag](../../../analysis-services/scripting/properties/displayflag-element-assl.md), [nome](../../../analysis-services/scripting/properties/name-element-assl.md), [PendingValue](../../../analysis-services/scripting/properties/pendingvalue-element-assl.md), [RequiresRestart](../../../analysis-services/scripting/properties/requiresrestart-element-assl.md), [valore](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il **ServerProperty** elemento descrive i dati e metadati per una proprietà del server associata a un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. A differenza degli elementi contenuti dalle altre raccolte in di Analysis Services Scripting Language (ASSL), il **ServerProperty** elemento utilizza coppie nome/valore anziché elementi denominati in modo esplicito per descrivere le proprietà del server. Le coppie nome/valore forniscono flessibilità ed estensibilità.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento server &#40; ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Oggetti &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
