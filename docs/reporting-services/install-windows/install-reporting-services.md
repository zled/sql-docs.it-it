---
title: Installazione di SQL Server Reporting Services | Documenti Microsoft
ms.date: 10/10/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 52c2f8fae79884b025e067b7d628cd3154ba93f4
ms.openlocfilehash: 5ce83ff18d6908441a3eaaf05599068ec5876308
ms.contentlocale: it-it
ms.lasthandoff: 10/10/2017

---
# <a name="install-sql-server-reporting-services"></a>Installare SQL Server Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

Installazione di SQL Server Reporting Services include i componenti server per archiviare gli elementi del report, il rendering dei report e l'elaborazione della sottoscrizione e altri servizi di report.  Informazioni su come installare Server di Report di Power BI.

Per scaricare SQL Server 2017 Reporting Services, visitare il [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=55252).

> [!NOTE]
> Ricerca di Power BI Report Server? Vedere [installare Server di Report di BI Power](https://powerbi.microsoft.com/documentation/reportserver-install-report-server/).

## <a name="before-you-begin"></a>Operazioni preliminari

Prima di installare Reporting Services, verificare il [requisiti Hardware e software per l'installazione di SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).

## <a name="install-your-report-server"></a>Installare il server di report

Installazione di un server di report è semplice. Sono disponibili solo pochi passaggi per installare i file.

> [!NOTE]
> Non è necessario un server del motore di Database di SQL Server disponibile al momento dell'installazione. È necessario uno configurare Reporting Services dopo l'installazione.

1. Individuare il percorso di SQLServerReportingServices.exe e avviare il programma di installazione.

2. Selezionare **installare Reporting Services**.

    ![Installare Reporting Services](media/install-reporting-services/report-server-install.png)

3. Selezionare un'edizione per installare e quindi selezionare **Avanti**.

    ![Scegliere l'edizione](media/install-reporting-services/report-server-install-edition.png)

    È possibile scegliere Evaluation o Developer edition nell'elenco a discesa.

    ![Evaluation o developer Edition](media/install-reporting-services/report-server-install-edition-select.png)

    In caso contrario, è possibile immettere un codice product key.

4. Leggere e accettare le condizioni di licenza e quindi selezionare **Avanti**.

5. È necessario disporre di un motore di Database per archiviare il database del server di report. Selezionare **Avanti** per installare solo il server di report.

    ![Non è necessario per l'installazione di database](media/install-reporting-services/report-server-install-db-engine.png)

6. Specificare il percorso di installazione del server di report. Selezionare **installare** per continuare.

    ![Specificare il percorso di installazione](media/install-reporting-services/report-server-install-file-path.png)

    > [!NOTE]
    > Il percorso predefinito è c:\Programmi\Microsoft SQL Server Reporting Services.

7. Dopo l'installazione con esito positivo, selezionare **configurare Server di Report** per avviare Gestione configurazione Reporting Services.

    ![Configurare il server di report](media/install-reporting-services/report-server-install-configure.png)

## <a name="configuration-your-report-server"></a>Configurazione del server di report

Dopo aver selezionato **configurare Server di Report** nel programma di installazione, verrà visualizzato con **Gestione configurazione Reporting Services**. Per ulteriori informazioni, vedere [Gestione configurazione Reporting Services](reporting-services-configuration-manager-native-mode.md).

È necessario [creare un database del server di report](ssrs-report-server-create-a-report-server-database.md) per completare la configurazione iniziale di Reporting Services. Per completare questo passaggio è necessario un server di Database di SQL Server.

### <a name="creating-a-database-on-a-different-server"></a>Creazione di un database in un server diverso

Se si sta creando il database del server di report in un server di database in un computer diverso, è necessario modificare l'account del servizio del server di report a una credenziale riconosciuto nel server di database.

Per impostazione predefinita, il server di report utilizza l'account servizio virtuale. Se si tenta di creare un database in un server diverso, si potrebbe ricevere l'errore seguente durante il passaggio di diritti di connessione di applicazione.

`System.Data.SqlClient.SqlException (0x80131904): Windows NT user or group '(null)' not found. Check the name again.`

Per risolvere l'errore, è possibile modificare l'account del servizio a servizio di rete o un account di dominio. Modifica l'account del servizio al servizio di rete applica diritti nel contesto dell'account computer del server di report.

Per ulteriori informazioni, vedere [configurare l'account del servizio ReportServer](configure-the-report-server-service-account-ssrs-configuration-manager.md).

## <a name="windows-service"></a>Servizio Windows

Come parte dell'installazione viene creato un servizio di windows. Viene visualizzato come **SQL Server Reporting Services**. Il nome del servizio **SQLServerReportingServices**.

## <a name="default-url-reservations"></a>Prenotazioni URL predefinite

Le prenotazioni URL sono composte da un prefisso, un nome host, una porta e una directory virtuale:

|Parte|Descrizione|
|----------|-----------------|
|Prefisso|Il prefisso predefinito è HTTP. Se si è installato un certificato Secure Sockets Layer (SSL), il programma di installazione tenta di creare prenotazioni URL che utilizzano il prefisso HTTPS.|
|Nome host|Il nome host predefinito è un carattere jolly complesso (+). Specifica che il server di report accetti le richieste HTTP sulla porta designata per qualsiasi nome host risolto nel computer, tra cui `http://<computername>/reportserver`, `http://localhost/reportserver`, o`http://<IPAddress>/reportserver.`|
|Porta|La porta predefinita è 80. Se si utilizza una porta diversa dalla porta 80, è necessario aggiungerlo in modo esplicito all'URL quando si apre il portale web in una finestra del browser.|
|Directory virtuale|Per impostazione predefinita, le directory virtuali vengono create nel formato di ReportServer per il servizio Web ReportServer e report per il portale web. Per il servizio Web ReportServer, la directory virtuale predefinita è **reportserver**. Per il portale web, la directory virtuale predefinita è **report**.|

Di seguito viene fornito un esempio di stringa dell'URL completa:

- `http://+:80/reportserver`, fornisce l'accesso al server di report.

- `http://+:80/reports`, fornisce l'accesso al portale web.

## <a name="firewall"></a>Firewall

Se il server di report si accede da un computer remoto, si desidera assicurarsi di che aver configurato tutte le regole firewall se è presente un firewall.

È necessario aprire la porta TCP configurata per l'URL del servizio Web e l'URL del portale Web. Per impostazione predefinita, vengono configurate sulla porta TCP 80.

## <a name="additional-configuration"></a>Configurazione aggiuntiva

- Per configurare l'integrazione con il servizio Power BI in modo che è possibile aggiungere elementi del report a un dashboard di Power BI, vedere [integrazione con il servizio Power BI](power-bi-report-server-integration-configuration-manager.md).

- Per configurare posta elettronica per l'elaborazione delle sottoscrizioni, vedere [impostazioni di posta elettronica](e-mail-settings-reporting-services-native-mode-configuration-manager.md) e [recapito in un server di report tramite posta elettronica](../subscriptions/e-mail-delivery-in-reporting-services.md).

- Per configurare il portale web, pertanto è possibile accedervi in un computer remoto per visualizzare e gestire report, vedere [configurare un firewall per l'accesso al server di report](../report-server/configure-a-firewall-for-report-server-access.md) e [configurare un server di report per l'amministrazione remota](../report-server/configure-a-report-server-for-remote-administration.md) .

## <a name="related-information"></a>Informazioni correlate

Per informazioni su come installare la modalità nativa di SQL Server 2016 Reporting Services, vedere [server di report in modalità nativa di installare Reporting Services](install-reporting-services-native-mode-report-server.md). Per informazioni su come installare SQL Server 2016 Reporting Services in modalità integrata SharePoint, vedere [installare il primo Server di Report in modalità SharePoint](install-the-first-report-server-in-sharepoint-mode.md).

## <a name="next-steps"></a>Passaggi successivi

Con il server di report installato, iniziare a creare report e distribuirle nel server di report. Per informazioni su come avviare Generatore Report, vedere [Install Report Builder](../../reporting-services/install-windows/install-report-builder.md).

Per creare report utilizzando SQL Server Data Tools, [scaricare SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=616714).

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
