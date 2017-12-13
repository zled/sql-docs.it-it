---
title: Tipo di elemento (Dimension) (ASSL) | Documenti Microsoft
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
apiname: Type Element (Dimension)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: TYPE
helpviewer_keywords: Type element
ms.assetid: 6a2798b1-26c7-49d8-b556-e681c69d9574
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f11755a12e1876c1883b08f2460a7d8cc264dc25
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="type-element-dimension-assl"></a>Elemento Type (Dimension) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Fornisce informazioni sul contenuto della dimensione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Dimension>  
      ...  
   <Type>...</Type>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Regolare*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Per alcuni valori **tipo**, ad esempio *account*, determinare un comportamento specifico.  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Regolare*|La dimensione è una dimensione regolare.|  
|*Time*|La dimensione è una dimensione temporale.<br /><br /> Nota: Questo valore indica che la dimensione supporta le funzionalità specifiche di dimensioni temporali.|  
|*Area geografica*|La dimensione contiene attributi geografici.|  
|*Organizzazione*|La dimensione contiene attributi organizzativi.|  
|*BillOfMaterials*|La dimensione contiene attributi della distinta base.|  
|*Accounts*|La dimensione contiene attributi relativi ai conti.<br /><br /> Nota: Questo valore indica che la dimensione supporta le funzionalità specifiche per le dimensioni dell'account.|  
|*Clienti*|La dimensione contiene attributi relativi ai clienti.|  
|*Prodotti*|La dimensione contiene attributi relativi ai prodotti.|  
|*Scenario*|La dimensione contiene attributi relativi agli scenari.|  
|*Quantitativo*|La dimensione contiene attributi quantitativi.|  
|*Utilità*|La dimensione contiene attributi di utilità.|  
|*Valuta*|La dimensione contiene attributi di valuta.|  
|*Velocità*|La dimensione contiene attributi relativi al tasso di cambio.|  
|*Channel*|La dimensione contiene attributi relativi ai canali.|  
|*Innalzamento di livello*|La dimensione contiene attributi relativi alle promozioni.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **tipo** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DimensionType>.  
  
 L'elemento che corrisponde all'elemento padre **tipo** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
