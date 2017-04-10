---
title: "Elemento Banner (ssbdiagnose) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "elemento Banner"
  - "formato file di output XML [ssbdiagnose], elemento banner"
  - "ssbdiagnose"
ms.assetid: cc6cd49a-acf0-4cfb-8c6a-554692b89de2
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Elemento Banner (ssbdiagnose)
  Identifica l'utilità che ha generato il file di output XML di **ssbdiagnose**.  
  
## Sintassi  
  
```  
  
<Banner  
    title="..."   
    product="..."   
    version="..." />  
```  
  
## Attributi elemento  
  
|Attribute|Descrizione|  
|---------------|-----------------|  
|**title**|Identifica l'utilità che ha generato il file di output XML di **ssbdiagnose**.|  
|**product**|Identifica il prodotto che ha generato il file di output XML di **ssbdiagnose**.|  
|**version**|Identifica la versione dell'utilità che ha generato il file XML di output.|  
  
## Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuno|  
|**Valore predefinito**|Nessuno|  
|**Occorrenza**|Una volta per ogni file di output XML di **ssbdiagnose**.|  
  
## Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento DiagnosticInformation &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)|  
|**Elementi figlio**|nessuna.|  
  
## Esempio  
 Di seguito viene riportato un esempio di un elemento Banner.  
  
```  
<Banner title="Service Broker Diagnostics Utility" product="Microsoft SQL Server" version="10.0.1073.0" />  
```  
  
## Vedere anche  
 [Utilità ssbdiagnose &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  