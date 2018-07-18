---
title: Il tipo di dati ClrAssembly (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f6fb3493fc7add4ece9ef2d5acacd772d5911ebd
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037082"
---
# <a name="clrassembly-data-type-assl"></a>Tipo di dati ClrAssembly (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce un tipo di dati derivato che rappresenta un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly associato a un [Database](../../../analysis-services/scripting/objects/database-element-assl.md) o [Server](../../../analysis-services/scripting/objects/server-element-assl.md) elemento  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ClrAssembly>  
      <!-- The following elements extend Assembly -->  
   <Files>...</Files>  
      <PermissionSet>...</PermissionSet>  
</ClrAssembly>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|[Assembly](../../../analysis-services/scripting/objects/assembly-element-assl.md)|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno (tipo astratto)|  
|Elementi figlio|[File](../../../analysis-services/scripting/collections/files-element-assl.md), [PermissionSet](../../../analysis-services/scripting/properties/permissionset-element-assl.md)|  
|Elementi derivati|Vedere [Assembly](../../../analysis-services/scripting/objects/assembly-element-assl.md) (raccolta[Assemblies](../../../analysis-services/scripting/collections/assemblies-element-assl.md) di [Database](../../../analysis-services/scripting/objects/database-element-assl.md) o [Server](../../../analysis-services/scripting/objects/server-element-assl.md))|  
  
## <a name="remarks"></a>Osservazioni  
 Il **ClrAssembly** elemento contiene i file necessari per ricreare un [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly associato a un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] o a un database specifico in un'istanza di [!INCLUDE[ssAS](../../../includes/ssas-md.md)], nonché le autorizzazioni necessarie per eseguire l'assembly.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ClrAssembly>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento file & #40; ASSL & #41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Tipo di dati ClrAssemblyFile & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)   
 [Elemento di dati & #40; ASSL & #41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [Tipo di dati DataBlock & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Elemento Blocks & #40; ASSL & #41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Elemento di blocco & #40; ASSL & #41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [Tipo di dati ComAssembly & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
