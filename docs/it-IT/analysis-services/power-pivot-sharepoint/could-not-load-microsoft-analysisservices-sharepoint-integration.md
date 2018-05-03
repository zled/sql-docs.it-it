---
title: Non è stato possibile caricare 'Microsoft.AnalysisServices.SharePoint.Integration' | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ppvt-sharepoint
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b90fd2a99bd6321936c0cef399ec115baceced0f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="could-not-load-microsoftanalysisservicessharepointintegration"></a>Non è stato possibile caricare Microsoft.AnalysisServices.SharePoint.Integration
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Negli ambienti di SharePoint 2010 in cui è disponibile [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint, questo errore si verifica se la distribuzione della soluzione a livello di applicazione per [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] non è avvenuta correttamente.  
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Applicabile a|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint|  
|Versione prodotto|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Causa|La soluzione Powerpivotwebapp non è stata distribuita o non ha eseguito correttamente la distribuzione.|  
|Testo del messaggio|Impossibile caricare il file o l'assembly "Microsoft.AnalysisServices.SharePoint.Integration"|  
  
## <a name="explanation"></a>Spiegazione  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] PowerPivot per SharePoint usa pacchetti della soluzione per distribuire le funzionalità in un server SharePoint. Una delle soluzioni non è distribuita correttamente. Di conseguenza, questo errore viene visualizzato quando si cerca di aprire la raccolta [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] o altre pagine dell'applicazione [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in un sito di SharePoint.  
  
## <a name="user-action"></a>Azione dell'utente  
 Distribuire il pacchetto della soluzione.  
  
1.  In Impostazioni sistema di Amministrazione centrale fare clic su **Gestisci soluzioni farm**.  
  
2.  Fare clic su **Powerpivotwebapp**.  
  
3.  Fare clic su **Distribuisci soluzione**.  
  
4.  Scegliere l'applicazione Web per la quale si sta verificando questo errore. Se sono presenti più applicazioni Web, ridistribuire la soluzione per tutte.  
  
5.  Scegliere **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuire soluzioni PowerPivot in SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
