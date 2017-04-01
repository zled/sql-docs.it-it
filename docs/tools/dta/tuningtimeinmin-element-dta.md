---
title: "Elemento TuningTimeInMin (DTA) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "XML"
helpviewer_keywords: 
  - "TuningTimeInMin - elemento"
ms.assetid: 4973d9ac-20fd-4ac3-bc9f-5d60e39fdb7d
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Elemento TuningTimeInMin (DTA)
  Specifica la lunghezza massima di una sessione di ottimizzazione espressa in minuti.  
  
## Sintassi  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <TuningTimeInMin>...</TuningTimeInMin>  
```  
  
## Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|**unsignedInt**, lunghezza illimitata.|  
|**Valore predefinito**|480 minuti (8 ore).|  
|**Occorrenza**|Obbligatorio a meno che non sia stato specificato un valore per l'elemento **NumberOfEvents** .|  
  
## Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento TuningOptions &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Elementi figlio**|Nessuno|  
  
## Esempio  
  
## Descrizione  
 Nell'esempio di codice seguente viene illustrato come impostare 12 ore come tempo di ottimizzazione massimo:  
  
## codice  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <TuningTimeInMin>720</TuningTimeInMin>  
...code removed here...  
</DTAInput>  
```  
  
## Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  