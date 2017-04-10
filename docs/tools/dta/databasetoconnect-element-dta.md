---
title: "Elemento DatabaseToConnect (DTA) | Microsoft Docs"
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
  - "DatabaseToConnect - elemento"
ms.assetid: 65153a66-3aee-4429-99b7-0816ac23c285
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# Elemento DatabaseToConnect (DTA)
  Specifica il primo database al quale Ottimizzazione guidata motore di database si connette durante l'ottimizzazione di un carico di lavoro.  
  
## Sintassi  
  
```  
  
    <TuningOptions>  
...code removed here...  
      <DatabaseToConnect>...</DatabaseToConnect>  
```  
  
## Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|**string**, lunghezza illimitata.|  
|**Valore predefinito**|Nessuno|  
|**Occorrenza**|Facoltativa. È possibile utilizzarlo una volta per ogni elemento **TuningOptions** .|  
  
## Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento TuningOptions &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Elementi figlio**|Nessuno|  
  
## Osservazioni  
 Utilizzare **DatabaseToConnect** per specificare il nome del primo database al quale si desidera che Ottimizzazione guidata motore di database si connetta quando viene avviata la sessione di ottimizzazione. È possibile specificare un solo database con questo elemento. Se vengono specificati più nomi di database, Ottimizzazione guidata motore di database restituisce un errore.  
  
## Esempio  
 Per un esempio di uso, vedere [Esempio di file di input XML con carico di lavoro inline &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md).  
  
## Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  