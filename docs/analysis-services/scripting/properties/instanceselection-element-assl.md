---
title: Elemento InstanceSelection (ASSL) | Documenti Microsoft
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
apiname: InstanceSelection Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: InstanceSelection element
ms.assetid: 908a2da9-274c-40d2-87dc-4641cb8d77e6
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 539c7259235437b39690f7c5241b63bd0b18a2f7
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="instanceselection-element-assl"></a>Elemento InstanceSelection (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Fornisce un hint alle applicazioni client per suggerire come un elenco di elementi deve essere visualizzato, in base al numero previsto di elementi nell'elenco.  
  
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
  
|Valore|Description|  
|-----------|-----------------|  
|*Nessuno*|Non visualizzare un elenco di selezione. Consentire agli utenti di inserire direttamente valori.|  
|*Elenco a discesa*|Il numero di elementi è sufficientemente piccolo per la visualizzazione in un elenco a discesa.|  
|*Elenco*|Il numero di elementi è troppo grande per la visualizzazione in un elenco a discesa, ma non richiede l'applicazione di filtri.|  
|*FilteredList*|Il numero di elementi è grande a sufficienza per richiedere l'utilizzo di filtri per la visualizzazione.|  
|*MandatoryFilter*|Il numero di elementi è così grande che per la visualizzazione è sempre necessario l'utilizzo di filtri.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **InstanceSelection** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.InstanceSelection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
