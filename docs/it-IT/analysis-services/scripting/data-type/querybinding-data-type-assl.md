---
title: Il tipo di dati QueryBinding (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- QueryBinding Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- QueryBinding
helpviewer_keywords:
- QueryBinding data type
ms.assetid: 7b58fc89-0060-4e56-ad99-6f74fe8cfc6d
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4a9f9d1ed9a81aaded7f4bb9b16880969bd3b707
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="querybinding-data-type-assl"></a>Tipo di dati QueryBinding (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce un tipo di dati derivato che rappresenta l'associazione di un [DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md) elemento con un [QueryDefinition](../../../analysis-services/scripting/properties/querydefinition-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<QueryBinding>  
   <!-- The following elements extend TabularBinding -->  
   <DataSourceID>...</DataSourceID>  
      <QueryDefinition>...</QueryDefinition>  
</QueryBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|[TabularBinding](../../../analysis-services/scripting/data-type/tabularbinding-data-type-assl.md)|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[DataSourceID](../../../analysis-services/scripting/properties/datasourceid-element-assl.md), [QueryDefinition](../../../analysis-services/scripting/properties/querydefinition-element-assl.md)|  
|Elementi derivati|Vedere [associazione](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni sul **associazione** tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) del **associazione** tipo e la gerarchia di ereditarietà dei **associazione**  sui tipi, vedere [associazione tipo di dati &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni dati in ASSL, vedere [origini dati e associazioni & #40; SSAS multidimensionale & #41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.QueryBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
