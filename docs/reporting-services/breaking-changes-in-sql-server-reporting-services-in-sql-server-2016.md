---
title: Modifiche di rilievo in SQL Server Reporting Services in SQL Server 2016 | Documenti Microsoft
ms.date: 07/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Me.Value references
- Reporting Services, backward compatibility
- breaking changes [Reporting Services]
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
caps.latest.revision: 121
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 6348d05b8dbe6c8ab1a682388b4e69ce438e6a12
ms.contentlocale: it-it
ms.lasthandoff: 07/03/2017

---

# Modifiche di rilievo di SQL Server Reporting Services in SQL Server 2016
<a id="breaking-changes-in-sql-server-reporting-services-in-sql-server-2016" class="xliff"></a>

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../includes/ssrs-previous-versions.md)]

In questo argomento vengono descritte le modifiche di rilievo introdotte in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Tali modifiche potrebbero interrompere il funzionamento di applicazioni, funzionalità o script basati su versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. I problemi potrebbero verificarsi durante un aggiornamento oppure in script o report personalizzati.

## Estensioni di sicurezza
<a id="security-extensions" class="xliff"></a>

Le estensioni di sicurezza personalizzate richiedono alcune modifiche per funzionare con il nuovo [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]. Le estensioni di sicurezza devono usare l'interfaccia IAuthenticationExtension2.

## Provider WMI
<a id="wmi-provider" class="xliff"></a>

Il nome dell'applicazione [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] cambia da "ReportManager" a "ReportServerWebApp".

## Passaggi successivi
<a id="next-steps" class="xliff"></a>

[Modifiche del comportamento di SQL Server Reporting Services in SQL Server 2016](../reporting-services/behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)  
[Novità di Reporting Services (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)   
[Funzionalità deprecate in SQL Server Reporting Services in SQL Server 2016](../reporting-services/deprecated-features-in-sql-server-reporting-services-ssrs.md)    
[Funzionalità non più disponibili di SQL Server Reporting Services in SQL Server 2016](../reporting-services/discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  

Ulteriori domande? [Provare a porre il forum di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
