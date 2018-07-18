---
title: Elemento RootMemberIf (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0a738d6d859a74430d50439ebcee3d4aab8d031c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34038978"
---
# <a name="rootmemberif-element-assl"></a>Elemento RootMemberIf (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
