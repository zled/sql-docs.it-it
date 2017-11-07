---
title: Elemento InstanceSelection (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- InstanceSelection Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- InstanceSelection element
ms.assetid: 908a2da9-274c-40d2-87dc-4641cb8d77e6
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4587536131aa3484846bc241a08be866a30d1da6
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="instanceselection-element-assl"></a>Elemento InstanceSelection (ASSL)
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
  
  

