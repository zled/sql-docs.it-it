---
title: "Modifiche di rilievo di SQL Server Reporting Services in SQL Server 2016 | Microsoft Docs"
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Me.Value references"
  - "Reporting Services, compatibilità con le versioni precedenti"
  - "modifiche di rilievo [Reporting Services]"
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
caps.latest.revision: 121
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 116
---
# Modifiche di rilievo di SQL Server Reporting Services in SQL Server 2016
  In questo argomento vengono descritte le modifiche di rilievo introdotte in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Tali modifiche potrebbero interrompere il funzionamento di applicazioni, funzionalità o script basati su versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. I problemi potrebbero verificarsi durante un aggiornamento oppure in script o report personalizzati.  
  
  ## Estensioni di sicurezza
  
  Le estensioni di sicurezza personalizzate richiedono alcune modifiche per funzionare con il nuovo [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]. Le estensioni di sicurezza devono usare l'interfaccia IAuthenticationExtension2.
  
  ## Provider WMI
  
  Il nome dell'applicazione [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] cambia da "ReportManager" a "ReportServerWebApp".
  
## Vedere anche  
 [Modifiche di funzionamento di SQL Server Reporting Services in SQL Server 2016](http://msdn.microsoft.com/it-it/2a767f0f-84f2-4099-8784-1e37790f858e)   
 [Novità di Reporting Services &#40;SSRS&#41;](../Topic/What's%20New%20in%20Reporting%20Services%20\(SSRS\).md)   
 [Funzionalità deprecate di SQL Server Reporting Services in SQL Server 2016](http://msdn.microsoft.com/it-it/3876c01e-f81d-4cce-9104-5106a8c369e6)   
 [Funzionalità non più disponibili di SQL Server Reporting Services in SQL Server 2016](http://msdn.microsoft.com/it-it/d529cc96-3483-480b-9bfc-bd28b1d0ef52)  
  
  