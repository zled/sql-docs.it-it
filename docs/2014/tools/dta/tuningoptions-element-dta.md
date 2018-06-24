---
title: Elemento TuningOptions (DTA) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b816f81d12c7a05fb2be4c38dcd4b5bf1a867c10
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062524"
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
|**Tipo di dati e lunghezza**|Nessuna.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Facoltativo. Se usato, sono utilizzabili solo una volta per ogni `DTAInput` elemento.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento DTAInput &#40;DTA&#41;](dtainput-element-dta.md)|  
|**Elementi figlio**|`ReportSet` Elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `TuningLogTable` Elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `NumberOfEvents` Elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [Elemento TuningTimeInMin &#40;DTA&#41;](tuningtimeinmin-element-dta.md)<br /><br /> [Elemento StorageBoundInMB &#40;DTA&#41;](storageboundinmb-element-dta.md)<br /><br /> `MaxKeyColumnsInIndex` Elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `MaxColumnsInIndex` Elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `MinPercentageImprovement` Elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100)<br /><br /> [Elemento TestServer &#40;DTA&#41;](server-element-dta.md)<br /><br /> [Elemento FeatureSet &#40;DTA&#41;](featureset-element-dta.md)<br /><br /> [Elemento Partitioning &#40;DTA&#41;](partitioning-element-dta.md)<br /><br /> [Elemento DropOnlyMode &#40;DTA&#41;](droponlymode-element-dta.md)<br /><br /> [Elemento KeepExisting &#40;DTA&#41;](keepexisting-element-dta.md)<br /><br /> [Elemento OnlineIndexOperation &#40;DTA&#41;](onlineindexoperation-element-dta.md)<br /><br /> [Elemento DatabaseToConnect &#40;DTA&#41;](databasetoconnect-element-dta.md)<br /><br /> `IgnoreConstantsInWorkload` Elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `RetainShellDB` Elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="example"></a>Esempio  
 Per esempi del `TuningOptions` elemento, vedere la [esempi di File di Input XML &#40;DTA&#41;](xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  