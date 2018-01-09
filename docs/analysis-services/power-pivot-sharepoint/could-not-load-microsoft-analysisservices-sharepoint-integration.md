---
title: "Non è stato possibile caricare 'Microsoft.AnalysisServices.SharePoint.Integration' | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0854f5c3cdf740c68b8f83dcb3d847cefc256edd
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="could-not-load-microsoftanalysisservicessharepointintegration"></a>Non è stato possibile caricare Microsoft.AnalysisServices.SharePoint.Integration
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]In ambienti SharePoint 2010 con [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint, questo errore si verifica se la soluzione a livello di applicazione per [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] distribuzione non è riuscita correttamente.  
  
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
  
5.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuire soluzioni PowerPivot in SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
