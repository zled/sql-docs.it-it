---
title: "Elemento Name per Schema (DTA) | Microsoft Docs"
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
  - "Name - elemento"
ms.assetid: 014e4854-fed2-454b-8557-5f7c5bb6b17a
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Elemento Name per Schema (DTA)
  Contiene il nome dello schema.  
  
## Sintassi  
  
```  
  
<Database>  
...code removed here  
    <Schema>  
        <Name>...</Name>  
```  
  
## Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|**string**, tra 1 e 255 caratteri|  
|**Valore predefinito**|Nessuno|  
|**Occorrenza**|Obbligatorio una sola volta per elemento **Schema** .|  
  
## Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Schema per Database &#40;DTA&#41;](../../tools/dta/schema-element-for-database-dta.md)|  
|**Elementi figlio**|nessuna.|  
  
## Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Elemento Server &#40;DTA&#41;](../../tools/dta/server-element-dta.md).  
  
## Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  