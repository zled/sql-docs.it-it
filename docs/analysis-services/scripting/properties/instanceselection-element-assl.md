---
title: Elemento InstanceSelection (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 1f00127f58bb1f8c5a6792bec3ddcb8420f0d24b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34035332"
---
# <a name="instanceselection-element-assl"></a>Elemento InstanceSelection (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Fornisce un hint alle applicazioni client sul modo in cui deve venire visualizzato un elenco di elementi, in base al numero previsto di elementi presenti nell'elenco.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <InstanceSelection>...</InstanceSelection>  
   ...  
</DimensionAttribute>  
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
|Elemento padre|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|*Nessuno*|Non visualizzare un elenco di selezione. Consentire agli utenti di inserire direttamente valori.|  
|*Elenco a discesa*|Il numero di elementi è sufficientemente piccolo per la visualizzazione in un elenco a discesa.|  
|*Elenco*|Il numero di elementi è troppo grande per la visualizzazione in un elenco a discesa, ma non richiede l'applicazione di filtri.|  
|*FilteredList*|Il numero di elementi è grande a sufficienza per richiedere l'utilizzo di filtri per la visualizzazione.|  
|*MandatoryFilter*|Il numero di elementi è così grande che per la visualizzazione è sempre necessario l'utilizzo di filtri.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **InstanceSelection** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.InstanceSelection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
