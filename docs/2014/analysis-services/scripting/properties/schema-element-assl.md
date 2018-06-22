---
title: Elemento dello schema (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Schema Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Schema
helpviewer_keywords:
- Schema element
ms.assetid: 4b6375fb-7ad8-4d5f-88b1-abd3da2654db
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 130d1363a007fb51db3bc7b39efcae4d9140c368
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077675"
---
# <a name="schema-element-assl"></a>Elemento Schema (ASSL)
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|schema|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DataSourceView](../objects/datasourceview-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 L'elemento `Schema` viene rappresentato utilizzando il formato XSD (XML Schema Definition) dei set di dati in [!INCLUDE[msCoName](../../../includes/msconame-md.md)].NET Framework, con alcune estensioni per i set di dati e altre specifiche per questo utilizzo all'interno di Data Definition Language (DDL). I set di dati definiscono un mapping flessibile da XSD a uno schema relazionale, ma restituiscono quindi XSD in una forma più canonica. All'interno delle origini dati è valida solo questa forma canonica.  
  
 L'elemento che corrisponde al padre di `Schema` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DataSourceView>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  