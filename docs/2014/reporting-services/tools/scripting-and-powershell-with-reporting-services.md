---
title: Script e PowerShell con Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services]
- Reporting Services, scripting
- scripting [Reporting Services]
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 949ceb6b2aff0dd393cfa0c58e91355f20f4c741
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48166521"
---
# <a name="scripting-and-powershell-with-reporting-services"></a>Script e PowerShell con Reporting Services
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] supporta un'ampia gamma di scenari di sviluppo e gestione tramite script, tra cui l'utilità della riga di comando rs.exe, cmdlet di PowerShell per server di report in modalità SharePoint, sfruttando il [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] modello a oggetti da PowerShell per nativi e Modalità SharePoint.  
  
-   Gli amministratori possono scrivere script in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] per automatizzare le procedure di distribuzione e gestione dell'installazione di un server di report. Gli amministratori possono anche generare ed eseguire script [!INCLUDE[tsql](../../includes/tsql-md.md)] che consentono di creare, configurare e aggiornare un database del server di report. Gli amministratori possono inoltre utilizzare le caratteristiche script di registrazione e riproduzione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per automatizzare le attività di manutenzione di routine.  
  
-   Gli sviluppatori possono creare applicazioni personalizzate che includono script. È possibile eseguire uno script che effettua chiamate al servizio Web ReportServer. Nello script è possibile scrivere quasi tutte le operazioni che si possono scrivere in codice gestito.  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] supporta [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] script .NET come linguaggio di scripting che può essere elaborato dall'utilità RS.exe, un host di script che viene eseguito nel server di report.  
  
## <a name="reporting-services-sharepoint-mode-powershell-cmdlets-and-samples"></a>Cmdlet ed esempi di PowerShell in modalità SharePoint di Reporting Services  
 ![Contenuto correlato di PowerShell](../media/rs-powershellicon.jpg "Contenuto correlato di PowerShell")  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] La modalità SharePoint include [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] cmdlet per l'amministrazione del server di report.  
  
-   [PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) Sono inclusi gli esempi seguenti:  
  
    -   Creare un proxy e un'applicazione di servizio  
  
    -   Rivedere e aggiornare un'estensione per il recapito  
  
    -   Ottenere e impostare le proprietà del database dell'applicazione Reporting Service, ad esempio timeout database  
  
    -   Elencare le estensioni per i dati  
  
## <a name="reporting-services-object-model-and-powershell-samples"></a>Modello a oggetti di Reporting Services ed esempi di Powershell  
 ![Contenuto correlato di PowerShell](../media/rs-powershellicon.jpg "Contenuto correlato di PowerShell")  
  
 Le chiamate del modello a oggetti principale di PowerShell valide in generale per la modalità SharePoint e nativa, ad esempio l'attività di migrazione, l'attività di sottoscrizione ed esempi più correlati per le sottoscrizioni, funzionano in SQL15.  
  
-   [Usare PowerShell per modificare ed elencare i proprietari di sottoscrizioni di Reporting Services ed eseguire una sottoscrizione](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).  
  
-   [Usare PowerShell per creare una VM di Azure con un server di report in modalità nativa](http://msdn.microsoft.com/library/azure/dn449661.aspx).  
  
-   Vedere la sezione "Accedere alle classi WMI utilizzando PowerShell" in [Access the Reporting Services WMI Provider](access-the-reporting-services-wmi-provider.md).  
  
-   [Come amministrare SSRS con gli script di PowerShell](http://curah.microsoft.com/13107/how-to-administer-ssrs-using-powershell)  
  
## <a name="rsexe-scripting-samples"></a>Esempi di script RS.exe  
  
-   [Esempio di Reporting Services rs.exe Script per la migrazione del contenuto tra server di Report](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
-   Per altri esempi di script, applicazioni ed estensioni, vedere gli [esempi di prodotti di Reporting Services di SQL Server](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità RS.exe &#40;SSRS&#41;](rs-exe-utility-ssrs.md)   
 [Utilizzare script per l'esecuzione di attività di distribuzione e di amministrazione](script-deployment-and-administrative-tasks.md)   
 [Eseguire lo script con l'utilità rs.exe e il servizio Web](script-with-the-rs-exe-utility-and-the-web-service.md)  
  
  
