---
title: Elemento dello schema (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9822bbf6112673c5e03c382063af2ed017b8d5ca
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="schema-element-assl"></a>Elemento Schema (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene lo schema della vista origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataSourceView>  
   ...  
   <Schema>...</Schema>  
   ...  
</DataSourceView>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Schema|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **Schema** rappresentato utilizzando il formato di linguaggio XML Schema Definition (XSD) di set di dati di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework, con alcune estensioni per i set di dati e altre specifiche per questo utilizzo all'interno della definizione di dati Language (DDL). I set di dati definiscono un mapping flessibile da XSD a uno schema relazionale, ma restituiscono quindi XSD in una forma più canonica. All'interno delle origini dati è valida solo questa forma canonica.  
  
 L'elemento che corrisponde all'elemento padre **Schema** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DataSourceView>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
