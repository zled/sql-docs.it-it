---
title: Elemento TuningOptions (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a4630640d2d61685accdb26031b87aff2883b644
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48065841"
---
# <a name="tuningoptions-element-dta"></a>Elemento TuningOptions (DTA)
  Contiene le opzioni di ottimizzazione per una specifica sessione di ottimizzazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuno|  
|**Valore predefinito**|Nessuno|  
|**Occorrenza**|Facoltativa. Se usato, utilizzabile solo una volta per ogni `DTAInput` elemento.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento DTAInput &#40;DTA&#41;](dtainput-element-dta.md)|  
|**Elementi figlio**|`ReportSet` elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `TuningLogTable` elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `NumberOfEvents` elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [Elemento TuningTimeInMin &#40;DTA&#41;](tuningtimeinmin-element-dta.md)<br /><br /> [Elemento StorageBoundInMB &#40;DTA&#41;](storageboundinmb-element-dta.md)<br /><br /> `MaxKeyColumnsInIndex` elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `MaxColumnsInIndex` elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `MinPercentageImprovement` elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100)<br /><br /> [Elemento TestServer &#40;DTA&#41;](server-element-dta.md)<br /><br /> [Elemento FeatureSet &#40;DTA&#41;](featureset-element-dta.md)<br /><br /> [Elemento Partitioning &#40;DTA&#41;](partitioning-element-dta.md)<br /><br /> [Elemento DropOnlyMode &#40;DTA&#41;](droponlymode-element-dta.md)<br /><br /> [Elemento KeepExisting &#40;DTA&#41;](keepexisting-element-dta.md)<br /><br /> [Elemento OnlineIndexOperation &#40;DTA&#41;](onlineindexoperation-element-dta.md)<br /><br /> [Elemento DatabaseToConnect &#40;DTA&#41;](databasetoconnect-element-dta.md)<br /><br /> `IgnoreConstantsInWorkload` elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `RetainShellDB` elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="example"></a>Esempio  
 Per esempi del `TuningOptions` elemento, vedere la [esempi di File di Input XML &#40;DTA&#41;](xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
