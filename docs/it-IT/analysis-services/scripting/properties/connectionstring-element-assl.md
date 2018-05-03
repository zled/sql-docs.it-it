---
title: Elemento ConnectionString (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ConnectionString Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ConnectionString
helpviewer_keywords:
- ConnectionString element
ms.assetid: f74181c4-7df7-4fbd-94dd-e4ad03dffe14
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 328c0cf793d7440d34784fa33487839a011ce0b1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connectionstring-element-assl"></a>Elemento ConnectionString (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene la stringa di connessione crittografata per un [DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataSource>  
   ...  
   <ConnectionString>...</ConnectionString>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Origine dati](../../../analysis-services/scripting/objects/datasource-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento che corrisponde all'elemento padre **ConnectionString** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DataSource>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
