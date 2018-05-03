---
title: Il tipo di dati ClrAssemblyFile (ASSL) | Documenti Microsoft
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
- ClrAssemblyFile Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ClrAssemblyFile
helpviewer_keywords:
- ClrAssemblyFile data type
ms.assetid: 91074677-c149-483b-a56d-0e35d959d9eb
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: db8ea758a2666f042ae0b67772e0af62fc177377
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="clrassemblyfile-data-type-assl"></a>Tipo di dati ClrAssemblyFile (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce un tipo di dati primitivo che rappresenta uno dei file che compongono un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] **Assembly** ([ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md) elemento).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ClrAssemblyFile>  
   <Name>...</Name>  
      <Type>...</Type>  
      <Data>...</Data>  
</ClrAssemblyFile>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|Nessuno|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[I dati](../../../analysis-services/scripting/objects/data-element-assl.md), [nome](../../../analysis-services/scripting/properties/name-element-assl.md), [tipo](../../../analysis-services/scripting/properties/type-element-clrassemblyfile-assl.md)|  
|Elementi derivati|[File](../../../analysis-services/scripting/objects/file-element-assl.md) ([file](../../../analysis-services/scripting/collections/files-element-assl.md) insieme [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md))|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento server & #40; ASSL & #41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Elemento database &#40;ASSL&#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Elemento Assemblies &#40;ASSL&#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Elemento assembly & #40; ASSL & #41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Tipo di dati DataBlock & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Elemento Blocks & #40; ASSL & #41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Elemento di blocco & #40; ASSL & #41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [Tipo di dati ComAssembly & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
