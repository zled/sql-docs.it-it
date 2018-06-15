---
title: Tipo di elemento (Dimension) (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3af3168c39f685702154bb7c76435bd1d241a642
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34039365"
---
# <a name="type-element-dimension-assl"></a>Elemento Type (Dimension) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Regular*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Dimensione](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Per alcuni valori **tipo**, ad esempio *account*, determinare un comportamento specifico.  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Regular*|La dimensione è una dimensione regolare.|  
|*Time*|La dimensione è una dimensione temporale.<br /><br /> Nota: Questo valore indica che la dimensione supporta le funzionalità specifiche di dimensioni temporali.|  
|*Geography*|La dimensione contiene attributi geografici.|  
|*Organizzazione*|La dimensione contiene attributi organizzativi.|  
|*BillOfMaterials*|La dimensione contiene attributi della distinta base.|  
|*Accounts*|La dimensione contiene attributi relativi ai conti.<br /><br /> Nota: Questo valore indica che la dimensione supporta le funzionalità specifiche per le dimensioni dell'account.|  
|*Customers*|La dimensione contiene attributi relativi ai clienti.|  
|*Prodotti*|La dimensione contiene attributi relativi ai prodotti.|  
|*Scenario*|La dimensione contiene attributi relativi agli scenari.|  
|*Quantitative*|La dimensione contiene attributi quantitativi.|  
|*Utilità*|La dimensione contiene attributi di utilità.|  
|*Currency*|La dimensione contiene attributi di valuta.|  
|*Velocità*|La dimensione contiene attributi relativi al tasso di cambio.|  
|*Channel*|La dimensione contiene attributi relativi ai canali.|  
|*Promotion*|La dimensione contiene attributi relativi alle promozioni.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **tipo** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DimensionType>.  
  
 L'elemento che corrisponde all'elemento padre **tipo** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
