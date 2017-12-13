---
title: Elemento UnknownMember (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: UnknownMember Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: UnknownMember
helpviewer_keywords: UnknownMember element
ms.assetid: 5558961e-e3c6-4f4e-817d-5b12b0734c03
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6f2911b41c4dda82fd5ca06d50dca798c73bcb75
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="unknownmember-element-assl"></a>Elemento UnknownMember (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Indica se il membro sconosciuto è visibile.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Dimension>  
      ...  
   <UnknownMember>...</UnknownMember>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Nessuno*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Visibile*|Il membro sconosciuto esiste ed è visualizzato.|  
|*Nascosto*|Il membro sconosciuto esiste ma non è visualizzato.|  
|*Nessuno*|Il membro sconosciuto non è utilizzato.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **UnknownMember** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.UnknownMemberBehavior>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento UnknownMemberName &#40; ASSL &#41;](../../../analysis-services/scripting/properties/unknownmembername-element-assl.md)   
 [Elemento UnknownMemberTranslation &#40; ASSL &#41;](../../../analysis-services/scripting/objects/unknownmembertranslation-element-assl.md)   
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
