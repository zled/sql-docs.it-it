---
title: Elemento DropOnlyMode (DTA) | Documenti Microsoft
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
helpviewer_keywords: DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 27b7db70bf4ee3a7e775c25dba130f1546b1bb82
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="droponlymode-element-dta"></a>Elemento DropOnlyMode (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Specifica che Ottimizzazione guidata motore di Database deve considerare la rimozione solo gli indici esistenti, le viste indicizzate o partizioni durante la sessione di ottimizzazione. Se è specificata questa opzione di ottimizzazione non viene considerata alcuna nuova struttura di progettazione fisica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <DropOnlyMode>...</DropOnlyMode>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
 **Tipo di dati e lunghezza**  
  
 **Valore predefinito**  
  
 **Occorrenza**: facoltativo. È possibile usarlo solo una volta per ogni elemento **TuningOptions** . Non è possibile usarlo se nell'elemento **TuningOptions** sono specificati gli elementi seguenti:  
  
-   [Elemento FeatureSet &#40;DTA&#41;](../../tools/dta/featureset-element-dta.md)  
  
-   [Elemento Partitioning &#40;DTA&#41;](../../tools/dta/partitioning-element-dta.md)  
  
-   [Elemento KeepExisting &#40;DTA&#41;](../../tools/dta/keepexisting-element-dta.md) impostato su **ALL**  
  
## <a name="element-relationships"></a>Relazioni elemento  
 **Elemento padre**: [elemento TuningOptions &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)  
  
 **Elementi figlio**  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra la sezione **TuningOptions** di un file di input XML di Ottimizzazione guidata motore di database in cui è specificata la modalità **DropOnlyMode** . In questo esempio, il tempo di ottimizzazione è limitato a 24 ore (1440 minuti) e tutti gli indici esistenti cluster e non cluster verranno presi in considerazione per l'eliminazione:  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML&#40; (Ottimizzazione guidata motore di database)&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
