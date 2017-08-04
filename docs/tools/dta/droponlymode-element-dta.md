---
title: Elemento DropOnlyMode (DTA) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fac9ba968a7288b7bb7b9a31f93aeb1b597b7ba7
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="droponlymode-element-dta"></a>Elemento DropOnlyMode (DTA)
  Specifica che Ottimizzazione guidata motore di database deve considerare la rimozione degli indici, delle viste indicizzate o delle partizioni esistenti solo durante la sessione di ottimizzazione. Se è specificata questa opzione di ottimizzazione non viene considerata alcuna nuova struttura di progettazione fisica.  
  
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
  
-   [Partizionamento elemento &#40; DTA &#41;](../../tools/dta/partitioning-element-dta.md)  
  
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
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
