---
title: Elemento InstanceSelection (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- InstanceSelection Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- InstanceSelection element
ms.assetid: 908a2da9-274c-40d2-87dc-4641cb8d77e6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 41587ee5acd29ca8038e188a3a3a5681bb7b91d0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48131461"
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Nessuno*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe seguenti.  
  
|valore|Description|  
|-----------|-----------------|  
|*Nessuno*|Non visualizzare un elenco di selezione. Consentire agli utenti di inserire direttamente valori.|  
|*Elenco a discesa*|Il numero di elementi è sufficientemente piccolo per la visualizzazione in un elenco a discesa.|  
|*Elenco*|Il numero di elementi è troppo grande per la visualizzazione in un elenco a discesa, ma non richiede l'applicazione di filtri.|  
|*FilteredList*|Il numero di elementi è grande a sufficienza per richiedere l'utilizzo di filtri per la visualizzazione.|  
|*MandatoryFilter*|Il numero di elementi è così grande che per la visualizzazione è sempre necessario l'utilizzo di filtri.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `InstanceSelection` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.InstanceSelection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
