---
title: Elemento RootMemberIf (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
apiname:
- RootMemberIf Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- RootMemberIf
helpviewer_keywords:
- RootMemberIf element
ms.assetid: b695e271-c748-4abc-a09f-acb1014f768f
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9c312a638544071697a59bf1a7ddfb44ce9c5746
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="rootmemberif-element-assl"></a>Elemento RootMemberIf (ASSL)
  Determina il modo in cui vengono identificati il membro o i membri radice di un attributo padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <RootMemberIf>...</RootMemberIf>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*ParentIsBlankSelfOrMissing*|  
|Cardinalità|0-1: elemento facoltativo che può presentarsi una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore della **RootMemberIf** elemento viene utilizzato solo dagli attributi padre (in altre parole, il valore del [utilizzo](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) elemento del **DimensionAttribute** elemento padre è Impostare su *padre*) per determinare i membri radice (in primo piano) di una gerarchia padre-figlio.  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*ParentIsBlankSelfOrMissing*|Solo i membri che soddisfano una o più delle condizioni descritte per *ParentIsBlank*, *ParentIsSelf*, o *ParentIsMissing* vengono trattati come membri radice.|  
|*ParentIsBlank*|Solo i membri con un valore null, pari a zero o una stringa vuota nelle colonne chiave rappresentate dal [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md) insieme di **DimensionAttribute** vengono trattati come membri radice.|  
|*ParentIsSelf*|Solo i membri che hanno se stessi come padre vengono trattati come membri radice.|  
|*ParentIsMissing*|Solo i membri per i quali non è possibile trovare l'elemento padre vengono trattati come membri radice.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **RootMemberIf** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.RootIfValue>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

