---
title: Tipo di dati ClrAssembly (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ClrAssembly Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ClrAssembly
helpviewer_keywords:
- ClrAssembly data type
ms.assetid: 3f5dc5a1-ebd6-41b8-ac04-91d4de137eb4
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e17992a5d15113ec0de5dd75978f932cb83d11c8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066179"
---
# <a name="clrassembly-data-type-assl"></a>Tipo di dati ClrAssembly (ASSL)
  Definisce un tipo di dati derivato che rappresenta un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly associato a un [Database](../objects/database-element-assl.md) oppure [Server](../objects/server-element-assl.md) elemento  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ClrAssembly>  
      <!-- The following elements extend Assembly -->  
   <Files>...</Files>  
      <PermissionSet>...</PermissionSet>  
</ClrAssembly>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[Assembly](../objects/assembly-element-assl.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno (tipo astratto)|  
|Elementi figlio|[I file](../collections/files-element-assl.md), [PermissionSet](../properties/permissionset-element-assl.md)|  
|Elementi derivati|Vedere [Assembly](../objects/assembly-element-assl.md) ([assembly](../collections/assemblies-element-assl.md) insieme [Database](../objects/database-element-assl.md) oppure [Server](../objects/server-element-assl.md))|  
  
## <a name="remarks"></a>Remarks  
 Il `ClrAssembly` elemento contiene i file necessari per ricreare un [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly, associato a un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] o a un database specifico in un'istanza di [!INCLUDE[ssAS](../../../includes/ssas-md.md)], nonché il autorizzazioni necessarie per eseguire l'assembly.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ClrAssembly>.  
  
## <a name="see-also"></a>Vedere anche  
 [File di elemento &#40;ASSL&#41;](../objects/file-element-assl.md)   
 [Tipo di dati ClrAssemblyFile &#40;ASSL&#41;](clrassemblyfile-data-type-assl.md)   
 [Elemento di dati &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [Tipo di dati DataBlock &#40;ASSL&#41;](datablock-data-type-assl.md)   
 [Blocca l'elemento &#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [Bloccare l'elemento &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Tipo di dati ComAssembly &#40;ASSL&#41;](assembly-data-type-assl.md)   
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  