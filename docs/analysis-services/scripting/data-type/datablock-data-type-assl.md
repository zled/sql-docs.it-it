---
title: Il tipo di dati DataBlock (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7ef74279d2430df004ae00429f559ceb9a5c174e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="datablock-data-type-assl"></a>Tipo di dati DataBlock (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce un tipo di dati primitivo che rappresenta una raccolta di blocchi di dati utilizzata per archiviare il contenuto binario di un elemento [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataBlock>  
   <Blocks>...</Blocks>  
</DataBlock>  
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
|Elementi figlio|[Blocchi](../../../analysis-services/scripting/collections/blocks-element-assl.md)|  
|Elementi derivati|Elemento[Data](../../../analysis-services/scripting/objects/data-element-assl.md) di tipo [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) (raccolta[Files](../../../analysis-services/scripting/collections/files-element-assl.md) di tipo [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md) )|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento assembly & #40; ASSL & #41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Elemento file & #40; ASSL & #41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Elemento di blocco & #40; ASSL & #41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
