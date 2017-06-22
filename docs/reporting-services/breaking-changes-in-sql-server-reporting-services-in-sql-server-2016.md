---
title: Modifiche di rilievo in SQL Server Reporting Services in SQL Server 2016 | Documenti Microsoft
ms.date: 03/15/2017
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
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 36ec7d7f1aa78e08f7fa4b63e8ca6525afe1c215
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="breaking-changes-in-sql-server-reporting-services-in-sql-server-2016"></a>Modifiche di rilievo di SQL Server Reporting Services in SQL Server 2016
  In questo argomento vengono descritte le modifiche di rilievo introdotte in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Tali modifiche potrebbero interrompere il funzionamento di applicazioni, funzionalità o script basati su versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. I problemi potrebbero verificarsi durante un aggiornamento oppure in script o report personalizzati.  
  
  ## <a name="security-extensions"></a>Estensioni di sicurezza
  
  Le estensioni di sicurezza personalizzate richiedono alcune modifiche per funzionare con il nuovo [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]. Le estensioni di sicurezza devono usare l'interfaccia IAuthenticationExtension2.
  
  ## <a name="wmi-provider"></a>Provider WMI
  
  Il nome dell'applicazione [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] cambia da "ReportManager" a "ReportServerWebApp".
  
## <a name="see-also"></a>Vedere anche 

[Modifiche del comportamento di SQL Server Reporting Services in SQL Server 2016](../reporting-services/behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)

[Novità di Reporting Services (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)
 
[Funzionalità deprecate di SQL Server Reporting Services in SQL Server 2016](../reporting-services/deprecated-features-in-sql-server-reporting-services-ssrs.md)
  
[Funzionalità non più disponibili di SQL Server Reporting Services in SQL Server 2016](../reporting-services/discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)



