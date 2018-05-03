---
title: Il tipo di dati ReportAction (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- ReportAction Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ReportAction
helpviewer_keywords:
- ReportAction data type
ms.assetid: b22f0d52-ed3a-4239-840e-0eaf172d7276
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2b9fb3a6727f74c28474f965af15476d7a81c8f4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="reportaction-data-type-assl"></a>Tipo di dati ReportAction (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce un tipo di dati derivato che rappresenta un'azione che genera un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ReportAction>  
   <!-- The following elements extend Action -->  
   <ReportServer>...</ReportServer>  
   <Path>...</Path>  
   <ReportParameters>...</ReportParameters>  
   <ReportFormatParameters>...</ReportFormatParameters>  
</ReportAction>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|[Azione](../../../analysis-services/scripting/data-type/action-data-type-assl.md)|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[Percorso](../../../analysis-services/scripting/properties/path-element-assl.md), [Reportformatparameter](../../../analysis-services/scripting/collections/reportformatparameters-element-assl.md), [ReportParameters](../../../analysis-services/scripting/collections/reportparameters-element-assl.md), [ReportServer](../../../analysis-services/scripting/properties/reportserver-element-assl.md)|  
|Elementi derivati|[Azione](../../../analysis-services/scripting/objects/action-element-assl.md) ([azioni](../../../analysis-services/scripting/collections/actions-element-assl.md) insieme [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md) oppure [prospettiva](../../../analysis-services/scripting/objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Osservazioni  
 Il server di report risponde alle richieste basate su URL relative ai report. L'azione del report viene definito con un tipo *Report*. Le risorse e i parametri vengono inviati al server quando viene creata l'azione. Il server espone l'azione come un'azione di tipo set di righe.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ReportAction>.  
  
## <a name="see-also"></a>Vedere anche  
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
