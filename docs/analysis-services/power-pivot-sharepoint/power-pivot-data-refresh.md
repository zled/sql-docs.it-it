---
title: Aggiornamento dati PowerPivot di Power | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: ac8358a3-ee71-44c7-8ee6-ac7afe3ebaa4
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 22a4a92f63616664ff5018d8a440e437879c7225
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="power-pivot-data-refresh"></a>Aggiornamento dati Power Pivot
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Dopo avere creato una cartella di lavoro che contiene dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , è possibile aggiornare periodicamente i dati rieseguendo una query o un comando per ottenere informazioni aggiornate dalle origini usate in origine per creare la cartella di lavoro. Questo processo, denominato **aggiornamento dati**, consente di aggiornare i dati su richiesta in [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]o come operazione pianificata eseguita come processo di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in un server applicazioni in una farm di SharePoint. Per altre informazioni, vedere:  
  
-   [Aggiornamento dati PowerPivot con SharePoint 2010](http://msdn.microsoft.com/en-us/01b54e6f-66e5-485c-acaa-3f9aa53119c9)  
  
-   [Configurare l'account di aggiornamento dati automatico PowerPivot (PowerPivot per SharePoint)](http://msdn.microsoft.com/en-us/81401eac-c619-4fad-ad3e-599e7a6f8493)  
  
-   [Configurare le credenziali archiviate per l'aggiornamento dati Power Pivot (Power Pivot per SharePoint)](http://msdn.microsoft.com/en-us/987eff0f-bcfe-4bbd-81e0-9aca993a2a75)  
  
-   [Pianificare un aggiornamento dati (Power Pivot per SharePoint)](http://msdn.microsoft.com/en-us/8571208f-6aae-4058-83c6-9f916f5e2f9b)  
  
-   [Visualizzare la cronologia dell'aggiornamento dati &#40;Power Pivot per SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e SharePoint Server 2013 Excel Services viene usata un'architettura diversa per i modelli di dati di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. L'architettura supportata da SharePoint 2013 usa Excel Services come componente principale per caricare modelli di dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . L'architettura di aggiornamento dati usata in precedenza era basata su un server che eseguiva il servizio di sistema di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] e [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modalità SharePoint per caricare i modelli di dati. Per ulteriori informazioni, vedere quanto segue:  
>   
>  -   [Aggiornamento dati PowerPivot con SharePoint 2013](../../analysis-services/power-pivot-sharepoint/power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [Aggiornare le cartelle di lavoro e l'aggiornamento dati pianificato &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
