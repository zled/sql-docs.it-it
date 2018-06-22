---
title: Installare funzionalità di Business Intelligence di SQL Server 2014 | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67399b24-e48a-49f3-9dd4-32d78c6a2ece
caps.latest.revision: 21
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 3a8a984e617caf7678f04fa4e64b0d500ae9e90d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069128"
---
# <a name="install-sql-server-2014-bi-features"></a>Installare le funzionalità di business intelligence di SQL Server 2014
  Le funzionalità di SQL Server che fanno parte della piattaforma di Microsoft Business Intelligence includono [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]e diverse applicazioni client utilizzate per la creazione o l'utilizzo di dati analitici. In questa sezione della documentazione relativa al programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene descritto come installare queste funzionalità.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] possono essere installati come server autonomi, in configurazioni con scalabilità orizzontale o come applicazioni di servizio condivise in una farm SharePoint. L'installazione dei servizi in una farm consente di abilitare le funzionalità di Business Intelligence disponibili solo in SharePoint, incluso [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint e [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], la nuova la finestra di progettazione di report ad hoc interattiva di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in esecuzione in [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] o database modello tabulare di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Se si conoscono già i passaggi di installazione per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o PowerPivot per SharePoint, è possibile ignorare gli elenchi di controllo per l'abilitazione di scenari specifici. Per altre informazioni, vedere [elenchi di controllo per l'installazione delle funzionalità di Business Intelligence con SharePoint](checklists-for-installing-bi-features-with-sharepoint.md).  
  
## <a name="contents"></a>Sommario  
 Contenuto della sezione:  
  
|Collegamento|Attività|  
|----------|----------|  
|[Elenchi di controllo per l'installazione di funzionalità di Business Intelligence con SharePoint](checklists-for-installing-bi-features-with-sharepoint.md)|Se si conoscono già i componenti da installare e si dispone di familiarità con i passaggi di installazione per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint, è possibile utilizzare gli elenchi di controllo presenti in questa sezione per indicazioni sull'ordine di installazione, su account e requisiti di autorizzazione e sui passaggi per la distribuzione di topologie avanzate, incluse distribuzioni multiserver e con più funzionalità.|  
|[Installare funzionalità di Business Intelligence di SQL Server con SharePoint &#40;PowerPivot e Reporting Services&#41;](install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)|In questa sezione viene illustrato come installare funzionalità di SQL Server in un ambiente SharePoint. e vengono identificate le funzionalità di SQL Server disponibili in una versione ed edizione specifiche di SharePoint Nella sezione sono inoltre incluse procedure di installazione per PowerPivot per SharePoint e per Reporting Services in modalità SharePoint.|  
|[Installare Analysis Services in multidimensionale e modello di Data Mining](install-analysis-services-in-multidimensional-and-data-mining-mode.md)<br /><br /> [Installare Analysis Services in modalità tabulare](../../analysis-services/instances/install-windows/install-analysis-services.md)<br /><br /> [Installare Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)<br /><br /> [Installazione di Integration Services](../../integration-services/install-windows/install-integration-services.md)<br /><br /> [Installazione di Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)<br /><br /> [Installare un server di report in modalità nativa di Reporting Services](../../reporting-services/install-windows/install-reporting-services-native-mode-report-server.md)|In questa sezione vengono fornite le istruzioni per l'installazione di Analysis Services, Integration Services, Master Data Services e Reporting Services, con Analysis Services e Reporting Services installate senza SharePoint. Ciò è talvolta detta *modalità nativa*, ed è lo scenario più comune di installazione per Reporting Services e Analysis Services. In questa sezione vengono descritte opzioni di installazione che determinano direttamente il contesto operativo del server. Per Reporting Services, quest'ultimo potrebbe essere un server preconfigurato o uno che richiede più passaggi di configurazione prima che sia possibile utilizzarlo, Mentre per Analysis Services le opzioni di installazione che si selezionano determineranno il tipo di progetto che è possibile distribuire nel server.|  
|[Verifica o risoluzione dei problemi di installazione delle funzionalità di Business Intelligence di SQL Server](../../../2014/sql-server/install/verify-or-troubleshoot-sql-server-bi-feature-installation-problems.md)|In questa sezione vengono descritti i passaggi per la verifica di un'installazione e sono contenuti i collegamenti alle informazioni sulla risoluzione di problemi sul Web.|  
  
## <a name="related-content"></a>Contenuto correlato  
  
|Collegamento|Attività|  
|----------|----------|  
|[Aggiornamento a SQL Server 2014](../../database-engine/install-windows/upgrade-sql-server.md)<br /><br /> [Aggiornare Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)<br /><br /> [Aggiornare PowerPivot per SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)<br /><br /> [Eseguire l'aggiornamento e la migrazione di Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)|Utilizzare le istruzioni in questa sezione per aggiornare server e contenuto da una versione precedente a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|[Disinstallare SQL Server 2014](uninstall-sql-server.md)<br /><br /> [Disinstallare PowerPivot per SharePoint](../../../2014/sql-server/install/uninstall-power-pivot-for-sharepoint.md)<br /><br /> [Disinstallare Reporting Services](../../../2014/sql-server/install/uninstall-reporting-services.md)|Utilizzare le istruzioni in questa sezione per disinstallare le funzionalità BI.|  
  
## <a name="see-also"></a>Vedere anche  
 [Novità di &#40;Reporting Services&#41;](../../../2014/reporting-services/what-s-new-reporting-services.md)   
 [Novità di Analysis Services e Business Intelligence](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Installare SQL Server 2014](../../database-engine/install-windows/install-sql-server.md)   
 [Aggiornamento a SQL Server 2014](../../database-engine/install-windows/upgrade-sql-server.md)  
  
  