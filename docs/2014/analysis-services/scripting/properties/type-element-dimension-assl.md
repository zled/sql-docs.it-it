---
title: Tipo di elemento (Dimension) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Type Element (Dimension)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 6a2798b1-26c7-49d8-b556-e681c69d9574
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c6afa3b273200630a4d36e0c4df679c58efb6bd5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283947"
---
# <a name="type-element-dimension-assl"></a>Elemento Type (Dimension) (ASSL)
  Fornisce informazioni sul contenuto della dimensione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Dimension>  
      ...  
   <Type>...</Type>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Regolare*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Dimension](../objects/dimension-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Alcuni valori per `Type`, ad esempio *account*, determinano comportamenti specifici.  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Regolare*|La dimensione è una dimensione regolare.|  
|*Time*|La dimensione è una dimensione temporale. **Nota:** questo valore indica che la dimensione supporta le funzionalità specifiche delle dimensioni temporali.|  
|*Geography*|La dimensione contiene attributi geografici.|  
|*Organizzazione*|La dimensione contiene attributi organizzativi.|  
|*BillOfMaterials*|La dimensione contiene attributi della distinta base.|  
|*Accounts*|La dimensione contiene attributi relativi ai conti. **Nota:** questo valore indica che la dimensione supporta le funzionalità specifiche delle dimensioni di tipo conti.|  
|*Clienti*|La dimensione contiene attributi relativi ai clienti.|  
|*Prodotti*|La dimensione contiene attributi relativi ai prodotti.|  
|*Scenario*|La dimensione contiene attributi relativi agli scenari.|  
|*Quantitative*|La dimensione contiene attributi quantitativi.|  
|*Utilità*|La dimensione contiene attributi di utilità.|  
|*Valuta*|La dimensione contiene attributi di valuta.|  
|*Tariffe*|La dimensione contiene attributi relativi al tasso di cambio.|  
|*Channel*|La dimensione contiene attributi relativi ai canali.|  
|*Innalzamento di livello*|La dimensione contiene attributi relativi alle promozioni.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `Type` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.DimensionType>.  
  
 L'elemento che corrisponde al padre di `Type` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
