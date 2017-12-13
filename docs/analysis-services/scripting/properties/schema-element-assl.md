---
title: Elemento dello schema (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
apiname: Schema Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Schema
helpviewer_keywords: Schema element
ms.assetid: 4b6375fb-7ad8-4d5f-88b1-abd3da2654db
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c96773b2d1f1f42b195d41b98ac1646c997257c1
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="schema-element-assl"></a>Elemento Schema (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Contiene lo schema della vista origine dati.  
  
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
|Tipo di dati e lunghezza|schema|  
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
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
