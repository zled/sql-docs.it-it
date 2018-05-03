---
title: Tipo di dati assembly (ASSL) | Documenti Microsoft
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
- Assembly Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Assembly data type
ms.assetid: 0a381322-9509-4579-a754-c6cdd0a70cc9
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9753f827296e90381faf890741139ec4fca8eda1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="assembly-data-type-assl"></a>Tipo di dati Assembly (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce un tipo di dati primitivo astratto che rappresenta un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly o libreria a collegamento dinamico (DLL) un COM associata a un [Server](../../../analysis-services/scripting/objects/server-element-assl.md) o [Database](../../../analysis-services/scripting/objects/database-element-assl.md) elemento.  
  
> [!IMPORTANT]  
>  Gli assembly COM potrebbero comportare un rischio per la sicurezza. A causa di tale rischio e di altre considerazioni, gli assembly COM sono stati deprecati in [!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)] e potrebbero non essere supportati nelle versioni future.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Assembly>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Description>...</Description>  
   <CreatedTimestamp>...</CreatedTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <ImpersonationInfo>...</ImpersonationInfo>  
   <Annotations>...</Annotations>  
</Assembly>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|Nessuno|  
|Tipi di dati derivati|[ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md), [ComAssembly](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[Annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [descrizione](../../../analysis-services/scripting/properties/description-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [ImpersonationInfo](../../../analysis-services/scripting/properties/impersonationinfo-element-assl.md), [ LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [nome](../../../analysis-services/scripting/properties/name-element-assl.md)|  
|Elementi derivati|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **Assembly** tipo di dati viene utilizzato come tipo di dati di base per il **ComAssembly** elemento che rappresenta le librerie COM associate all'istanza o database, e **ClrAssembly** elemento che rappresenta [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly associati all'istanza o database. Per ulteriori informazioni sugli assembly, vedere [gestione di assembly del modello multidimensionale](../../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Assembly>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento server & #40; ASSL & #41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Elemento database &#40;ASSL&#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
