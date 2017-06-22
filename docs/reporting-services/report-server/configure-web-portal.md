---
title: Configurare il portale web | Documenti Microsoft
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- the web portal [Reporting Services], configuring
ms.assetid: e918986c-af15-48f6-8178-256aed829c6a
caps.latest.revision: 28
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: c0c6cc27711140e96bbf4420e8de596af53ddfcd
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="configure-the-web-portal"></a>Configurare il portale web

il portale web è un'applicazione front-end Web utilizzata per visualizzare i report, gestire il contenuto di server di report e concedere l'accesso utente a un server di report in modalità nativa. il portale web viene installato con il servizio Web ReportServer all'interno della stessa istanza server di report e facoltativamente configurato se si seleziona il **installare nella configurazione predefinita in modalità nativa** opzione durante l'installazione. È anche possibile configurare il portale web come attività di post-installazione. In questo argomento vengono fornite informazioni sui seguenti scenari di configurazione del portale web:

## <a name="prerequisites"></a>Prerequisiti

Per utilizzare il portale web, è necessario soddisfare i prerequisiti seguenti:

- È necessario disporre di una configurazione minima del server di report. Per ulteriori informazioni sulla configurazione minima di un server di report, vedere [configurare un Server di Report](../../reporting-services/report-server/configure-a-report-server-reporting-services-native-mode.md).

- Il server di report deve essere eseguito in modalità nativa. È possibile utilizzare il portale web con un server di report configurato per la modalità integrata SharePoint. In SQL Server 2013 non è possibile passare un server di report da una modalità all'altra. Se si desidera modificare il tipo di server di report utilizzato dall'ambiente, è necessario installare la modalità desiderata del server di report desiderato e copiare o spostare gli elementi del report dal server di report precedente in quello nuovo. Questo processo viene in genere chiamato "migrazione". I passaggi necessari per eseguire la migrazione dipendono dalla modalità con cui si esegue questa operazione e dalla versione dalla quale si esegue la migrazione. Per ulteriori informazioni, vedere [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).

- È inoltre necessario Internet Explorer 11 o versione successiva con gli script abilitato. Per altre informazioni, vedere [Supporto browser per Reporting Services e Power View](../../reporting-services/browser-support-for-reporting-services-and-power-view.md).

## <a name="configure-the-web-portal-to-use-the-default-url"></a>Configurare il portale web per utilizzare l'URL predefinito

Il portale web è un'applicazione Web che gli utenti di accedere in un Web browser. È necessario almeno definire l'URL utilizzato per aprire l'applicazione in una finestra del browser. L'URL è costituito da un nome host, una porta e una directory virtuale. I valori predefiniti per questo URL includono i valori del nome host e della porta definiti per l'URL del servizio Web ReportServer, oltre al nome della directory virtuale **reports** . Se si dispone di un'istanza denominata, la directory virtuale è **istanza_report**, dove **istanza** è il nome dell'istanza di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .

Per impostazione predefinita, il portale web di URL è costituito da un nome di directory virtuali univoci, più il nome host e porta definita per il servizio Web ReportServer eseguito nella stessa istanza. Nella maggior parte dei casi, il nome host corrisponde al nome di rete del computer del server di report, ma può anche essere un indirizzo IP o l'intestazione host che si risolve nel computer. Per configurare il portale web per utilizzare l'URL predefinito, utilizzare il **URL del portale Web** nella pagina di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] lo strumento di configurazione.

> [!TIP]
> Se si tenta di accedere al portale web in un computer remoto e si ricevono messaggi di errore di connessione nel browser, una causa comune è le impostazioni del Firewall. Per altre informazioni, vedere [Configurare un firewall per l'accesso al server di report](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md).

#### <a name="to-configure-the-default-the-web-portal-url-and-virtual-directory"></a>Per configurare l'impostazione predefinita, il portale web URL e la directory virtuale

1. Avviare lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e connettersi all'istanza del server di report.

2. Nel [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] strumento di configurazione, seleziona **URL del portale Web** per aprire la pagina di configurazione dell'URL.

3. Immettere un nome di directory virtuale univoco per il portale web.

4. Fare clic su **Applica**.

5. Se si utilizza [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] o Windows Server 2008, potrebbero essere necessari passaggi aggiuntivi prima di poter usare il portale web. Per altre informazioni, vedere [Configurare un server di report in modalità nativa per gli amministratori locali &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).

## <a name="configure-the-web-portal-to-use-a-specific-report-server-url"></a>Configurare il portale web per utilizzare un URL del server di report specifico

Per impostazione predefinita, il portale web connette al servizio Web ReportServer eseguito nello stesso servizio Server di Report. Il portale web Usa l'URL del servizio Web ReportServer per stabilire la connessione. Se si definiscono più URL per il servizio Web ReportServer, il portale web Usa l'ultimo definito. Tuttavia, per alcune distribuzioni, è consigliabile il portale web per sempre la connessione al servizio Web tramite un URL statico. ad esempio nei casi in cui il filtro dei pacchetti è stato configurato su una porta o un indirizzo IP specifico e si desidera che tutte le connessioni al server di report vengano sottoposte alle regole di filtro definite.

Quando si configurano gli URL di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] strumento di configurazione, il portale web rileva e utilizza automaticamente tutti gli URL nuovi e aggiornati per il server di report che viene eseguito nella stessa istanza del server. Se la distribuzione richiede l'utilizzo di un unico URL statico per tutte le richieste del server di report, è possibile specificare tale URL nel file RSReportServer.config.

#### <a name="to-configure-a-static-report-server-url"></a>Per configurare un URL di un server di report statico

1. Aprire il file **RSReportServer.config** in un editor di testo. Per impostazione predefinita, si trova in \Programmi\Microsoft SQL Server\MSRS12. \< *instancename*> Services\ReportServer..  

2. Individuare **ReportServerURL**.

3. Sostituirlo con l'URL dell'istanza del server di report.

4. Salvare le modifiche, quindi chiudere il file.

Per altre informazioni sul file di configurazione, vedere [Modificare un file di configurazione di Reporting Services &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) e [File di configurazione RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).

## <a name="customize-styles-or-application-title"></a>Personalizzare gli stili o il titolo dell'applicazione

È possibile creare un pacchetto del marchio personalizzato per modificare i colori utilizzati per il portale web. Per ulteriori informazioni, vedere [personalizzazione del portale web](../branding-the-web-portal.md)

#### <a name="to-modify-application-title"></a>Per modificare il titolo dell'applicazione

1. Accedere usando un account con autorizzazioni di **Amministratore sistema** sul server di report.

2. Aprire Internet Explorer.

3. Accedere al portale web URL. Per impostazione predefinita, è http://\<**your-server-name**> / reports, ma se Reporting Services è installato come istanza denominata, l'URL predefinito sarà http://\<**your-server-name**> / reports\<**NomeIstanza**>.

4. Selezionare **Impostazioni sito**.

5. Nella scheda **Generale** sostituire **SQL Server Reporting Services**con un nome diverso in **Nome** .

6. Selezionare **Applica**.

## <a name="next-steps"></a>Passaggi successivi

[Portale Web](../../reporting-services/web-portal-ssrs-native-mode.md)  
[Supporto browser per Reporting Services](../../reporting-services/browser-support-for-reporting-services-and-power-view.md)
[configurare un URL](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
[Verificare un'installazione di Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)   
[Attivare la funzionalità di Reporting Services o disattivare](../../reporting-services/report-server/turn-reporting-services-features-on-or-off.md)   
[Gestione di un server di report in modalità nativa](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)   
[File di configurazione RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
[Configurare un Server di Report in modalità nativa per l'amministrazione locale](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)

 Ulteriori domande? [Provare a porre il forum di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
