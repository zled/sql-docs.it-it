---
title: Elemento RootMemberIf (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- RootMemberIf Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RootMemberIf
helpviewer_keywords:
- RootMemberIf element
ms.assetid: b695e271-c748-4abc-a09f-acb1014f768f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fb10d62b14c5f13fbc26de23d832d77b724bebc6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48118701"
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*ParentIsBlankSelfOrMissing*|  
|Cardinalità|0-1: elemento facoltativo che può presentarsi una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore del `RootMemberIf` elemento viene utilizzato solo dagli attributi padre (in altre parole, il valore della [utilizzo](usage-element-dimensionattribute-assl.md) elemento del `DimensionAttribute` elemento padre è impostato su *padre*) per determinare la radice ( in primo piano) membri di una gerarchia padre-figlio.  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*ParentIsBlankSelfOrMissing*|Solo i membri che soddisfano una o più delle condizioni descritte per *ParentIsBlank*, *ParentIsSelf*, o *ParentIsMissing* vengono trattati come membri radice.|  
|*ParentIsBlank*|Solo i membri con un valore null, pari a zero o una stringa vuota nelle colonne chiave rappresentate dal [KeyColumns](../collections/columns-element-assl.md) insieme di `DimensionAttribute` vengono trattati come membri radice.|  
|*ParentIsSelf*|Solo i membri che hanno se stessi come padre vengono trattati come membri radice.|  
|*ParentIsMissing*|Solo i membri per i quali non è possibile trovare l'elemento padre vengono trattati come membri radice.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `RootMemberIf` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.RootIfValue>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
