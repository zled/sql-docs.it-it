---
title: Rimozione dei componenti di SQL Server Data Tools | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: f8ddb919-661f-4868-8c71-87c96f1f4487
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b114b99b816e10bc004cea8d60c56d296053c7c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685469"
---
# <a name="removing-sql-server-data-tools-components"></a>Rimozione dei componenti di SQL Server Data Tools
Alcuni componenti di SQL Server Data Tools (SSDT) non vengono rimossi quando si disinstalla SSDT o Visual Studio.  
  
Quando si disinstalla SSDT o Visual Studio non vengono rimossi i pacchetti di Windows Installer (.msi) seguenti. In seguito alla rimozione di questi componenti è possibile che altre versioni di Visual Studio si trovino in uno stato non supportato. Se si sceglie di rimuovere questi componenti, utilizzare Installazione applicazioni di Windows:  
  
-   Microsoft SQL Server Data Tools (SSDT.msi)  
  
-   Microsoft SQL Server Data Tools Build Utilities (SSDTBuildUtilities.msi)  
  
-   Prerequisiti per SSDT (SSDTDBSvcExternals.msi)  
  
I componenti condivisi seguenti possono essere utilizzati da altri prodotti, pertanto non vengono disinstallati con SSDT.  
  
-   SQL Server Data-Tier App Framework (DACFramework.msi)  
  
-   SQL Server Management Objects (SharedManagementObjects.msi)  
  
-   Servizio linguaggio Transact\-SQL SQL Server (TSqlLanguageService.msi)  
  
-   Microsoft SQL Server System CLR Types per SQL Server (SQLSysClrTypes.msi)  
  
-   SQL Server Transact\-SQL ScriptDom (SQLDom.msi)  
  
-   SQL Server Transact\-SQL Compiler Service (SQLLs.msi)  
  
