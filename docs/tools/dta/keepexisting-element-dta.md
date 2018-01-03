---
title: Elemento KeepExisting (DTA) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: KeepExisting element
ms.assetid: e67aae61-d06d-4a03-85ba-6516c3502dce
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5eca95f9df364166a798fee014cfad4521c87ae4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="keepexisting-element-dta"></a>Elemento KeepExisting (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Specifica le strutture di progettazione fisica (indici, viste indicizzate o partizionamento) che Ottimizzazione guidata motore di Database deve conservare durante la generazione dell'indicazione corrispondente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <KeepExisting>...</KeepExisting>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|**string**, limite della lunghezza imposto dal server.|  
|**Valori consentiti**|**NONE**<br /> Nessuna struttura esistente.<br /><br /> **ALL**<br /> Tutte le strutture esistenti.<br /><br /> **ALIGNED**<br /> Tutte le strutture con partizionamento allineato.<br /><br /> **CL_IDX**<br /> Tutti gli indici cluster nelle tabelle.<br /><br /> **IDX**<br /> Tutti gli indici cluster e non cluster nelle tabelle.<br /><br /> Utilizzare solo uno dei valori seguenti con questo elemento.|  
|**Valore predefinito**|nessuna.|  
|**Occorrenza**|Facoltativo. È possibile usarla una volta per ogni elemento **TuningOptions** .|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento TuningOptions &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Elementi figlio**|nessuna.|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML semplice &#40;DTA&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML&#40; (Ottimizzazione guidata motore di database)&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
