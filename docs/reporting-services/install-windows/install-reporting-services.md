---
title: Installare SQL Server Reporting Services 2017 e versioni successive | Microsoft Docs
ms.date: 12/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
author: markingmyname
ms.author: maghan
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: a3a822ddfdd954e0811e83ca4c92a2c3dc7e5b90
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51812974"
---
# <a name="install-sql-server-reporting-services-2017-and-later"></a>Installare SQL Server Reporting Services 2017 e versioni successive

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

L'installazione di SQL Server Reporting Services richiede i componenti server per archiviare gli elementi dei report, il rendering dei report e l'elaborazione della sottoscrizione e altri servizi report. 

Per scaricare SQL Server 2017 Reporting Services, accedere all'[Area download Microsoft](https://www.microsoft.com/download/details.aspx?id=55252).

> [!NOTE]
> Per informazioni sul server di report di Power BI, vedere [Installare il server di report di Power BI](https://powerbi.microsoft.com/documentation/reportserver-install-report-server/).

## <a name="before-you-begin"></a>Operazioni preliminari

Prima di installare Reporting Services, rivedere l'articolo [Requisiti hardware e software per l'installazione di SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).

## <a name="install-your-report-server"></a>Installare il server di report

L'installazione di un server di report è semplice. Occorrono solo pochi passaggi per installare i file.

> [!NOTE]
> Non è necessario avere a disposizione un server del motore di database di SQL Server al momento dell'installazione. Sarà necessario per configurare Reporting Services dopo l'installazione.

1. Individuare il percorso di SQLServerReportingServices.exe e avviare il programma di installazione.

2. Selezionare **Installa Reporting Services**.

    ![Installare Reporting Services](media/install-reporting-services/report-server-install.png)

3. Selezionare un'edizione da installare e quindi selezionare **Avanti**.

    ![Scegliere l'edizione](media/install-reporting-services/report-server-install-edition.png)

    Per l'edizione gratuita, nell'elenco a discesa scegliere Evaluation o Developer.

    ![Evaluation o Developer Edition](media/install-reporting-services/report-server-install-edition-select.png)

    In alternativa, immettere un codice Product Key. [Find the product key for SQL Server 2017 Reporting Services](find-reporting-services-product-key-ssrs.md) (Trovare il codice Product Key per SQL Server Reporting Services 2017)

4. Leggere e accettare le condizioni di licenza e scegliere **Avanti**.

5. È necessario avere disponibile un motore di database per archiviare il database del server di report. Selezionare **Avanti** per installare solo il server di report.

    ![Database non necessario per l'installazione](media/install-reporting-services/report-server-install-db-engine.png)

6. Specificare il percorso di installazione del server di report. Per continuare, fare clic su **Installa**.

    ![Specificare il percorso dell'installazione](media/install-reporting-services/report-server-install-file-path.png)

    > [!NOTE]
    > Il percorso di installazione predefinito è C:\Programmi\Microsoft SQL Server Reporting Services.

7. Una volta completata l'installazione, selezionare **Configura server di report** per avviare Gestione configurazione Reporting Services.

    ![Configurare il server di report](media/install-reporting-services/report-server-install-configure.png)

## <a name="configuration-your-report-server"></a>Configurare il server di report

Dopo aver selezionato **Configura server di report** nel programma di installazione, verrà visualizzata la **Gestione configurazione del server di report**. Per altre informazioni, vedere [Gestione configurazione Reporting Services](reporting-services-configuration-manager-native-mode.md).

È necessario [creare un database del server di report](ssrs-report-server-create-a-report-server-database.md) per completare la configurazione iniziale di Reporting Services. Per completare questo passaggio è necessario un server di database di SQL Server.

### <a name="creating-a-database-on-a-different-server"></a>Creazione di un database in un server diverso

Se si sta creando il database del server di report in un server di database in un computer diverso, è necessario modificare l'account del servizio del server di report con credenziali riconosciute nel server di database.

Per impostazione predefinita, il server di report usa l'account del servizio virtuale. Se si tenta di creare un database in un server diverso, si potrebbe ricevere l'errore seguente durante il passaggio di applicazione dei diritti di connessione.

`System.Data.SqlClient.SqlException (0x80131904): Windows NT user or group '(null)' not found. Check the name again.`

Per risolvere l'errore, è possibile modificare l'account del servizio impostandolo su un servizio di rete o un account di dominio. Se si modifica l'account del servizio impostandolo su un servizio di rete, i diritti verranno applicati nel contesto dell'account computer del server di report.

Per altre informazioni, vedere [Configurare l'account del servizio del server di report](configure-the-report-server-service-account-ssrs-configuration-manager.md).

## <a name="windows-service"></a>Servizio Windows

Come parte dell'installazione viene creato un servizio di Windows che viene visualizzato come **SQL Server Reporting Services**. Il nome del servizio è **SQLServerReportingServices**.

## <a name="default-url-reservations"></a>Prenotazioni URL predefinite

Le prenotazioni URL sono composte da un prefisso, un nome host, una porta e una directory virtuale:

|Parte|Descrizione|
|----------|-----------------|
|Prefisso|Il prefisso predefinito è HTTP. Se in precedenza è stato installato un certificato SSL (Secure Sockets Layer), il programma di installazione tenta di creare prenotazioni URL che usano il prefisso HTTPS.|
|Nome host|Il nome host predefinito è un carattere jolly complesso (+). Specifica che il server di report accetta le richieste HTTP sulla porta designata per qualsiasi nome host risolto nel computer, tra cui `https://<computername>/reportserver`, `https://localhost/reportserver`, o `https://<IPAddress>/reportserver.`|
|Port|La porta predefinita è 80. Se si usa un numero di porta diverso da 80, sarà necessario aggiungerlo in modo esplicito all'URL quando si apre il portale Web in una finestra del browser.|
|Directory virtuale|Per impostazione predefinita, le directory virtuali vengono create nel formato ReportServer per il servizio Web ReportServer e Reports per il portale Web. Per il servizio Web ReportServer, la directory virtuale predefinita è **reportserver**. Per il portale Web, la directory virtuale predefinita è **reports**.|

Di seguito viene fornito un esempio di stringa dell'URL completa:

- `https://+:80/reportserver` consente l'accesso al server di report.

- `https://+:80/reports` consente l'accesso al portale Web.

## <a name="firewall"></a>Firewall

Se si accede al server di report da un computer remoto, se è presente un firewall sarà necessario aver configurato tutte le regole firewall.

È necessario aprire la porta TCP configurata per l'URL del servizio Web e per l'URL del portale Web. Per impostazione predefinita, viene configurata la porta TCP 80.

## <a name="additional-configuration"></a>Configurazione aggiuntiva

- Per configurare l'integrazione con il servizio Power BI in modo che sia possibile aggiungere elementi del report a un dashboard di Power BI, vedere [Integrazione con il servizio Power BI](power-bi-report-server-integration-configuration-manager.md).

- Per configurare la posta elettronica per l'elaborazione delle sottoscrizioni, vedere [Impostazioni posta elettronica](e-mail-settings-reporting-services-native-mode-configuration-manager.md) e [Recapito tramite posta elettronica in un server di report](../subscriptions/e-mail-delivery-in-reporting-services.md).

- Per configurare il portale Web in modo che sia possibile accedervi in un computer remoto per visualizzare e gestire report, vedere [Configurare un firewall per l'accesso al server di report](../report-server/configure-a-firewall-for-report-server-access.md) e [Configurare un server di report per l'amministrazione remota](../report-server/configure-a-report-server-for-remote-administration.md).

## <a name="related-information"></a>Informazioni correlate

Per informazioni su come installare la modalità nativa di SQL Server 2016 Reporting Services, vedere [Installare un server di report in modalità nativa di Reporting Services](install-reporting-services-native-mode-report-server.md). Per informazioni su come installare SQL Server 2016 Reporting Services in modalità integrata SharePoint, vedere [Installare il primo server di report in modalità SharePoint](install-the-first-report-server-in-sharepoint-mode.md).

## <a name="next-steps"></a>Passaggi successivi

Una volta installato il server di report, iniziare a creare report e a distribuirli nel server di report. Per informazioni su come iniziare a usare Generatore report, vedere [Installare Generatore report](../../reporting-services/install-windows/install-report-builder.md).

Per creare report con SQL Server Data Tools, [scaricare SQL Server Data Tools](https://go.microsoft.com/fwlink/?LinkID=616714).

Altre domande? [Visitare il forum su Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
