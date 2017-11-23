---
title: Tipo di dati PushedDataSource (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: PushedDataSource Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: PushedDataSource
helpviewer_keywords: PushedDataSource data type
ms.assetid: b319ee87-7c0a-41ec-a8af-cc7089aeb6ad
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 96920e685a4ff05855069cf7256eab2848565e17
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="pusheddatasource-data-type-assl"></a>Tipo di dati PushedDataSource (ASSL)
  Definisce un tipo di dati primitivo che rappresenta un'origine dati (ad esempio un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] pacchetto) utilizzato per "push" di dati in un [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<PushedDataSource>  
   <Root>...</Root>  
   <EndOfData>...</EndOfData>  
</PushedDataSource>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|Nessuno|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[EndOfData](../../../analysis-services/scripting/properties/endofdata-element-assl.md), [radice](../../../analysis-services/scripting/properties/root-element-assl.md)|  
|Elementi derivati|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 **PushedDataSource** è utilizzato solo all'interno di un comando dell'elaborazione come un'origine dati out-of-line. Le origini dati persistenti non sono mai di questo tipo.  
  
## <a name="see-also"></a>Vedere anche  
 [Analysis Services Scripting Language tipi di dati XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
