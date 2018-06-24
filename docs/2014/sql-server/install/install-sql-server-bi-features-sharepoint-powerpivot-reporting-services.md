---
title: Installare funzionalità di Business Intelligence di SQL Server con SharePoint (PowerPivot e Reporting Services) | Documenti Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3166107c-30c2-468e-bb1b-bb42b79b37c3
caps.latest.revision: 20
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 25c8c6d8c5d83ba3661d30ed85f560d0aa18a54d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064183"
---
# <a name="install-sql-server-bi-features-with-sharepoint-powerpivot-and-reporting-services"></a>Installare le funzionalità di Business Intelligence di SQL Server con SharePoint (PowerPivot e Reporting Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] può essere integrato con una farm di Microsoft SharePoint per abilitare le funzionalità di Business Intelligence (BI) in SharePoint. Le funzionalità includono [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] viene utilizzato per [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] l'accesso ai dati in una farm di SharePoint. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] è il motore dati per le cartelle di lavoro create in [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per Excel a cui si accede da una raccolta di SharePoint. Una volta salvata una [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] cartella di lavoro in SharePoint, è possibile utilizzarlo come un'origine dati per [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] report.  
  
 Alcuni dei passaggi di installazione e configurazione necessari per SharePoint 2010 sono diversi dai passaggi necessari per SharePoint 2013. Alcuni argomenti di questa sezione si applicano a entrambe le versioni di SharePoint.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
 ![Nota](../../../2014/reporting-services/media/rs-fyinote.png "nota") le note sulla versione corrente, vedere [note sulla versione di SQL server 2014](http://go.microsoft.com/fwlink/?LinkID=296445).  
  
##  <a name="bkmk_top"></a> Contenuto dell'argomento  
  
-   [Scenari di Business Intelligence di SQL Server e SharePoint 2013](#bkmk_bi_scenarios)  
  
-   [Panoramica dell'installazione](#bkmk_install_sharepoint2013_overview)  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 Oltre alle informazioni di questo argomento, in questa sezione del contenuto sono presenti i seguenti argomenti correlati.  
  
 [Topologie di distribuzione per SQL Server BI Features in SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)  
  
 [Guida per l'utilizzo di funzionalità di Business Intelligence di SQL Server in una Farm di SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
 [Elenchi di controllo per l'installazione di funzionalità di Business Intelligence con SharePoint](../../../2014/sql-server/install/checklists-for-installing-bi-features-with-sharepoint.md)  
  
 [Installazione in modalità SharePoint di Reporting Services &#40;SharePoint 2010 e SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)  
  
 [Installazione PowerPivot per SharePoint 2013](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
 [Installazione PowerPivot per SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
##  <a name="bkmk_bi_scenarios"></a> Scenari di Business Intelligence di SQL Server e SharePoint 2013  
 In questa sezione vengono riepilogati i diversi livelli di funzionalità di Business Intelligence che è possibile scegliere di installare e configurare.  
  
 In Excel Services in SharePoint 2013 è inclusa la funzionalità del modello di dati per abilitare l'interazione con una cartella di lavoro di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nel browser. Per la funzionalità del modello di dati di base non è necessario distribuire il [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] aggiuntivo 2013 nella farm. È sufficiente installare un server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modalità SharePoint e registrarlo nelle impostazioni **Modello di dati** di Excel Services.  
  
 Distribuzione di [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] aggiuntivo 2013 vengono abilitate funzionalità aggiuntive nella farm di SharePoint. Le funzionalità aggiuntive comprendono [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] della raccolta, pianificazione dell'aggiornamento dati e Dashboard di gestione PowerPivot. Per ulteriori informazioni, vedere la tabella.  
  
||Level|Funzionalità|Installazione o configurazione|  
|-|-----------|--------------|--------------------------|  
|1|Solo SharePoint|Funzionalità native di Excel Services|Excel Services e altri servizi inclusi in SharePoint Server 2013.|  
|**2**|SharePoint con Analysis Services in modalità SharePoint|Cartelle di lavoro interattive di PowerPivot nel browser|Installare [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modalità SharePoint.<br /><br /> Registrare il server Analysis Services in Excel Services.|  
|**3**|SharePoint con Reporting Services in modalità SharePoint|Power View|Installare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modalità SharePoint.<br /><br /> Installare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] componente aggiuntivo **(rssharepoint. msi)** per SharePoint. Per altre informazioni, vedere [installare o disinstallare il componente aggiuntivo di Reporting Services per SharePoint &#40;SharePoint 2010 e SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)|  
|**4**|Tutte le funzionalità di PowerPivot|Accedere alle cartelle di lavoro come origine dati dall'esterno della farm.<br /><br /> Pianificare l'aggiornamento dati.<br /><br /> Raccolta PowerPivot.<br /><br /> Dashboard di gestione.<br /><br /> Tipo di contenuto del file di collegamento BISM.|Distribuire il componente aggiuntivo PowerPivot per SharePoint 2013 **(spPowerPivot.msi)**. Per ulteriori informazioni, vedere quanto segue:<br /><br /> [Installare o disinstallare PowerPivot per SharePoint componente aggiuntivo &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)<br /><br /> Per informazioni su come scaricare **spPowerPivot.msi**, vedere [Scaricare SQL Server 2014 PowerPivot per SharePoint](http://go.microsoft.com/fwlink/?LinkID=296473).|  
  
 Per ulteriori informazioni sull'abilitazione [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] funzionalità, vedere [di SQL Server BI chiaro-Up storia per SharePoint 2013](http://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx) (http://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx).  
  
##  <a name="bkmk_install_sharepoint2013_overview"></a> Panoramica dell'installazione  
 Se si desidera utilizzare sia [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], eseguire due volte l'installazione guidata di SQL Server. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sono opzioni separate nella **impostazione ruolo** pagina dell'installazione guidata di SQL Server.  
  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] supporta sia SharePoint 2010 e SharePoint 2013; tuttavia viene utilizzato un processo di installazione e architettura diverso a seconda della versione di SharePoint.  
  
 Di seguito viene riportato un riepilogo dei passaggi di installazione per distribuire le funzionalità di Business Intelligence per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in un unico server:  
  
 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013**  
  
 Per **SharePoint 2013**, il [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] installazione può essere eseguita su un server in cui è installato un prodotto SharePoint. Il [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] architettura utilizzata per SharePoint 2013, viene eseguito **di fuori** della farm di SharePoint e può essere installata in un server contenente anche un'installazione di SharePoint o può essere installato un server che non contiene un Installazione di SharePoint.  
  
1.  Installare SharePoint Server 2013 e abilitare Excel Services.  
  
2.  Installare [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modalità SharePoint e concedere agli account dei servizi e della farm di SharePoint i diritti di amministratore di server in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     Per entrambe le versioni di SharePoint, il [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] processo di installazione viene avviato selezionando il ruolo di installazione di **SQL Server PowerPivot per SharePoint** nella procedura guidata di installazione di SQL Server o utilizzare un prompt dei comandi di SQL Server installazione.  
  
     ![Impostazione ruolo](../../../2014/sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "impostazione ruolo")  
  
3.  Per SharePoint 2013, è possibile estendere il [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] funzionalità e l'esperienza. Scaricare ed eseguire **sppowerpivot. msi** per aggiungere dati lato server di gestione, collaborazione ed elaborazione supporto dell'aggiornamento per [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] cartella di lavoro. Per ulteriori informazioni, vedere [Microsoft SQL Server 2014 PowerPivot per Microsoft SharePoint](http://go.microsoft.com/fwlink/?LinkID=324854).  
  
     Eseguire la [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] pacchetto di installazione 2013 **sppowerpivot. msi** in ogni server della farm di SharePoint per verificare la versione corretta dei dati provider installati.  
  
4.  Per configurare [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint 2013, utilizzare **PowerPivot per SharePoint 2013** dello strumento.  
  
     L'installazione guidata di SQL Server vengono installati due [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] strumenti di configurazione. Uno degli strumenti di configurazione supporta SharePoint 2013 e l'altro supporta SharePoint 2010.  
  
     ![Due strumenti di configurazione PowerPivot](../../../2014/analysis-services/media/as-powerpivot-configtools-bothicons.gif "Due strumenti di configurazione PowerPivot")  
  
5.  Configurare Excel Services in SharePoint Server 2013 l'utilizzo dell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Per altre informazioni, vedere la sezione "Configurare base integrazione Analysis Services SharePoint" nella [PowerPivot per SharePoint 2013 Installation](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)e [(SharePoint Server impostazioni del modello di dati di gestire Excel Services 2013)](http://technet.microsoft.com/library/jj219780.aspx) (http://technet.microsoft.com/library/jj219780.aspx).  
  
6.  Per altre informazioni, vedere [PowerPivot per SharePoint 2013 Installation](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md).  
  
 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010**  
  
 Per SharePoint 2010, è necessario che l'installazione di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint venga eseguita in un server in cui è già installato o verrà installato SharePoint 2010. Il [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] architettura per SharePoint 2010 viene eseguito **all'interno** farm e richiede SharePoint nel server che [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint è installato.  
  
1.  Installare [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modalità SharePoint e concedere agli account dei servizi e della farm di SharePoint i diritti di amministratore di server in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     Una distribuzione di SharePoint 2010 non supporta spPowerPivot.msi e il file con estensione msi **non** è richiesto con SharePoint 2010.  
  
     Per entrambe le versioni di SharePoint, il [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] processo di installazione viene avviato selezionando il ruolo di installazione di **SQL Server PowerPivot per SharePoint** nella procedura guidata di installazione di SQL Server o utilizzare un prompt dei comandi di SQL Server installazione.  
  
2.  L'installazione guidata di SQL Server vengono installati due [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] strumenti di configurazione. Uno degli strumenti di configurazione supporta SharePoint 2013 e l'altro supporta SharePoint 2010.  
  
     Per configurare [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint 2010, usare il **strumento di configurazione PowerPivot** .  
  
3.  Per ulteriori informazioni, vedere [PowerPivot for SharePoint 2010 Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md).  
  
 **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]**  per SharePoint 2010 e 2013  
  
1.  L'installazione per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modalità SharePoint rimane invariata dalla versione precedente.  
  
     Il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] passaggi di installazione per SharePoint 2010 e SharePoint 2013 sono molto simili. Le note importanti relativamente alle versioni di SharePoint sono:  
  
    -   Vedere le combinazioni supportate dei prodotti seguenti:  
  
        -   Versione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
        -   Componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per prodotti SharePoint.  
  
        -   Versione del prodotto SharePoint.  
  
         [Combinazioni supportate di SharePoint e Server Reporting Services e componente aggiuntivo &#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
    -   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] su SharePoint 2010 richiede SharePoint 2010 Service Pack 2 (SP2).  
  
    1.  Installare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modalità SharePoint. [Installazione in modalità SharePoint di Reporting Services &#40;SharePoint 2010 e SharePoint 2013&#41; ](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md) e [installare Reporting Services in modalità SharePoint per SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
    2.  Installare il componente aggiuntivo di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per i prodotti SharePoint (rsSharePoint.msi). Vedere [installare o disinstallare il componente aggiuntivo di servizi Reporting per SharePoint &#40;SharePoint 2010 e SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md). Per la versione corrente di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] componente aggiuntivo per SharePoint, vedere [dove trovare il componente aggiuntivo di Reporting Services per prodotti SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
    3.  Configurare il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servizio di SharePoint e almeno un [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applicazione del servizio. Per altre informazioni, vedere la sezione "Creare un servizio applicazione di Reporting Services" nella [installare Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).  
  
##  <a name="bkm_database_attach"></a> Panoramica del collegamento di un Database di aggiornamento e SharePoint 2013  
 SharePoint 2013 non supporta l'aggiornamento sul posto. Tuttavia, l' **aggiornamento del collegamento di un database è supportato**.  
  
 Se si dispone di un'installazione di PowerPivot esistente integrata con SharePoint 2010, non è possibile eseguire l'aggiornamento sul posto del server SharePoint.  Tuttavia, è possibile completare i passaggi seguenti come parte dell'aggiornamento del collegamento di un database di SharePoint:  
  
1.  Installare una nuova farm di SharePoint Server 2013.  
  
2.  Eseguire un aggiornamento del collegamento di un database di SharePoint e la migrazione dei database del contenuto correlati a PowerPivot nella farm di SharePoint 2013.  
  
3.  Installare un'istanza di SQL Server Analysis Services in modalità SharePoint e concedere agli account dei servizi e della farm SharePoint diritti di amministratore di server in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
4.  Installare il pacchetto di installazione di PowerPivot per SharePoint 2013 **spPowerPivot.msi** in ogni server nella farm di SharePoint.  
  
5.  In Amministrazione centrale SharePoint 2013 configurare Excel Services per l'utilizzo del server Analysis Services in esecuzione in modalità SharePoint creato nel passaggio 3.  
  
     Per eseguire la migrazione delle pianificazioni di aggiornamento, configurare l'applicazione di servizio PowerPivot.  
  
> [!NOTE]  
>  Per ulteriori informazioni sull'aggiornamento del collegamento di un database di PowerPivot e SharePoint, vedere gli argomenti seguenti:  
  
-   [Eseguire la migrazione di PowerPivot per SharePoint 2013](../../analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013.md)  
  
-   [Panoramica del processo di aggiornamento a SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256688).  
  
-   [Pulire le preparazioni prima di un aggiornamento a SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256689).  
  
-   [Aggiornare i database da SharePoint 2010 a SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256690).  
  
## <a name="see-also"></a>Vedere anche  
 [Posizione in cui trovare il componente aggiuntivo Reporting Services per prodotti SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [Combinazioni supportate di SharePoint e Server Reporting Services e componente aggiuntivo &#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)   
 [Installare o disinstallare il componente aggiuntivo di servizi Reporting per SharePoint &#40;SharePoint 2010 e SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  