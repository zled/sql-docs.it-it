---
title: "Propriet&#224; DatabaseQueryTimeout (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "DatabaseQueryTimeout Property"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "DatabaseQueryTimeout - proprietà"
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
caps.latest.revision: 35
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Propriet&#224; DatabaseQueryTimeout (MSReportServer_ConfigurationSetting WMI)
  Specifica il numero di secondi di attesa prima che il server di report presuma che il comando non sia riuscito e che sia necessaria una quantità di tempo troppo elevata per l'esecuzione. Il server di report calcola il tempo di esecuzione della query rispetto al catalogo SQL e non rispetto a un'origine dati per il report. Proprietà di lettura/scrittura.  
  
## Sintassi  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## Valori della proprietà  
 Oggetto **integer** non firmato a 32 bit che rappresenta il numero di secondi concessi per l'esecuzione della query.  
  
## Codice di esempio  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  