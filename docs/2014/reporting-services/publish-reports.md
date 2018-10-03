---
title: Pubblicare i report | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], publishing
- publishing reports [Reporting Services]
ms.assetid: ef5a514e-e818-4041-a8b0-15835f9a046b
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 39d5c0e2a09926c87669f537710cc44df76b30c0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200748"
---
# <a name="publish-reports"></a>Pubblicazione di report
  Da[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], è possibile pubblicare tutti i i report e origini dati condivise in un progetto Server di Report in un server di report distribuendo il progetto o è possibile pubblicare un singolo report. Prima di pubblicare un report è necessario specificare l'URL del server di report di destinazione. Per altre informazioni, vedere [Impostare le proprietà di distribuzione &#40;Reporting Services&#41;](tools/set-deployment-properties-reporting-services.md).  
  
 È possibile usare la [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] versione di [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] per aprire, modificare, visualizzare in anteprima, salvare e pubblicare entrambi [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] e [!INCLUDE[ssRSversion10](../includes/ssrsversion10-md.md)] report. Per altre informazioni, vedere [Distribuzione e supporto della versione in SQL Server Data Tools &#40;SSRS&#41;](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).  
  
### <a name="to-publish-all-reports-in-a-project"></a>Per pubblicare tutti i report di un progetto  
  
-   Nel menu **Compilazione** fare clic su **Distribuisci \<nome progetto report>**. In alternativa, in Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto report e scegliere **Distribuisci**. È possibile visualizzare lo stato del processo di pubblicazione nella finestra Output.  
  
    > [!NOTE]  
    >  Quando si distribuisce un progetto server di report, vengono distribuite anche le origini dati condivise nel progetto report.  
  
### <a name="to-publish-a-single-report"></a>Per pubblicare un solo report  
  
-   In Esplora soluzioni fare clic con il pulsante destro del mouse sul report e scegliere **Distribuisci**. È possibile visualizzare lo stato del processo di pubblicazione nella finestra Output.  
  
    > [!NOTE]  
    >  Quando si pubblica un report, è necessario distribuire anche le origini dati condivise utilizzate dal report.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di origini dati e report](reports/publishing-data-sources-and-reports.md)   
 [Anteprima dei report](reports/previewing-reports.md)   
 [Pubblicazione dei report in un server di report](reports/publishing-reports-to-a-report-server.md)   
 [Ricerca, visualizzazione e gestione dei report &#40;Generatore report e SSRS&#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Esportazione di report &#40;Report e SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
