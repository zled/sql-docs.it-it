---
title: "Reporting Services (modalità nativa) di Configuration Manager | Documenti Microsoft"
ms.custom: 
ms.date: 09/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Reporting Services Configuration tool
- configuration options [Reporting Services]
- report servers [Reporting Services], configuring
- components [Reporting Services], Reporting Services Configuration tool
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: f684f0168e57c5cd727af6488b2460eeaead100c
ms.openlocfilehash: c9aa72267460ed2d52ae3e2d42a73071b4d7a0f3
ms.contentlocale: it-it
ms.lasthandoff: 09/21/2017

---

# <a name="reporting-services-configuration-manager-native-mode"></a>Gestione configurazione Reporting Services (modalità nativa)

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Utilizzare Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per configurare un'installazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modalità nativa. Se si è installato un server di report mediante l'opzione di installazione di tipo "solo file", è necessario utilizzare Gestione configurazione per configurare il server prima di poterlo utilizzare. Se si è installato un server di report mediante l'opzione di installazione della configurazione predefinita, è possibile utilizzare Gestione configurazione per verificare o modificare le impostazioni specificate durante l'installazione. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per configurare un'istanza remota o locale di un server di report.

> [!NOTE]
> A partire dalla versione [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non è progettato per gestire server di report in modalità SharePoint. La modalità SharePoint viene gestita e configurata tramite Amministrazione centrale SharePoint gli e script di PowerShell.  
  
##  <a name="bkmk_scenarios"></a> Scenari di utilizzo di Gestione configurazione Reporting Services  
 Tramite Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è possibile effettuare le attività seguenti:  
  
-   Configurare l'account del servizio del server di report. Questo account viene inizialmente configurato durante l'installazione, ma può essere modificato tramite Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] se la password viene aggiornata o si desidera utilizzare un account diverso.  
  
-   Creare e configurare URL. Il server di report e il [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] sono applicazioni [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] a cui è possibile accedere tramite URL. L'URL del server di report fornisce l'accesso agli endpoint di SOAP del server di report. L'URL di [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] consente di aprire [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] . È possibile configurare un singolo URL o più URL per ogni applicazione.  
  
-   Creare e configurare il database del server di report. Il server di report è un server senza stato che richiede un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per lo spazio di archiviazione interno. Per creare il database del server di report e configurare una connessione al database del server di report, è possibile utilizzare Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . È anche possibile selezionare un database del server di report esistente in cui è già incluso il contenuto che si desidera utilizzare.  
  
-   Configurare una distribuzione con scalabilità orizzontale in modalità nativa [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] supporta una topologia di distribuzione che consente a più istanze del server di report di utilizzare un singolo database del server di report condiviso. Per distribuire un server di report con scalabilità orizzontale, utilizzare Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per connettere ogni server di report al database del server di report condiviso.  
  
-   Eseguire il backup, il ripristino o la sostituzione della chiave simmetrica utilizzata per crittografare stringhe di connessione e credenziali archiviate. È necessario disporre di un backup della chiave simmetrica se si modifica l'account del servizio o si sposta un database del server di report in un altro computer.  
  
-   Configurazione dell'account di esecuzione automatica. Questo account viene utilizzato per le connessioni remote durante le operazioni pianificate o quando non sono disponibili credenziali utente.  
  
-   Consente di configurare la posta elettronica del server di report. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] include un'estensione per il recapito tramite posta elettronica del server di report che usa SMTP (Simple Mail Transfer Protocol) per recapitare report o notifiche di elaborazione di report in una cassetta postale elettronica. È possibile utilizzare Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per specificare quale server o gateway SMTP nella rete dovrà essere utilizzato per il recapito tramite posta elettronica.  
  
 Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] consente di gestire il contenuto del server di report, abilitare funzionalità aggiuntive o concedere l'accesso al server. Distribuzione completa richiede anche l'utilizzo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per abilitare funzionalità aggiuntive o modificare i valori predefiniti e il portale web per concedere l'accesso utente al server.

##  <a name="bkmk_requirements"></a> Requisiti

Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è uno strumento specifico della versione. Non è possibile utilizzare Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installato con questa versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per configurare una versione precedente di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Se si eseguono versioni precedenti e più recenti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modalità side-by-side nello stesso computer, sarà necessario utilizzare Gestione configurazione Reporting Services fornito con ogni versione per configurare ciascuna istanza.  

Per utilizzare Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , è necessario disporre di quanto segue:

- Autorizzazioni di amministratore di sistema locale nel computer in cui è ospitato il server di report da configurare. Se si sta configurando un computer remoto, è necessario disporre delle autorizzazioni di amministratore di sistema locale anche in questo computer.

- È necessario disporre dell'autorizzazione per la creazione di database nel [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in cui è ospitato il database del server di report.

- Il servizio WMI (Windows Management Instrumentation) deve essere attivato e in esecuzione nel server di report che si sta configurando. Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilizza il provider WMI del server di report per la connessione ai server di report locali e remoti. Se si sta configurando un server di report remoto, il computer deve consentire l'accesso remoto a WMI. Per altre informazioni, vedere [Configurare un server di report per l'amministrazione remota](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md).  

- Prima di poter connettersi a un'istanza remota del server di report e configurarla, è necessario abilitare il passaggio delle chiamate di Strumentazione gestione Windows (WMI) attraverso Windows Firewall. Per altre informazioni, vedere [Configurare un server di report per l'amministrazione remota](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md) nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

Gestione configurazione Reporting Services viene installata automaticamente quando si installa SQL Server Reporting Services.

##  <a name="bkmk_start_configuration_manager"></a> Per avviare Gestione configurazione Reporting Services

1.  Effettuare il passaggio riportato di seguito appropriato alla versione di Microsoft Windows in uso:

    - Dalla schermata start di Windows, digitare **Reporting** e selezionare **Gestione configurazione Reporting Services** dai risultati della ricerca.

    - Fare clic sul pulsante **Start**, scegliere **Tutti i programmi**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]e quindi **Strumenti di configurazione**.

         Se si desidera configurare un'istanza del server di report di una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], aprire la cartella del programma per la versione specifica. Selezionare, ad esempio, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] anziché [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] per aprire gli strumenti di configurazione per i componenti server di [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] .

         Selezionare **Gestione configurazione Reporting Services**.

2. Verrà visualizzata la finestra di dialogo **Connessione configurazione Reporting Services** in cui è possibile selezionare l'istanza del server di report che si desidera configurare. Selezionare **Connetti**.

3. In **Nome server**specificare il nome del computer in cui è installata l'istanza del server di report. Per impostazione predefinita, viene visualizzato il nome del computer locale, ma è possibile digitare il nome di un'istanza remota di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se si desidera connettersi a un server di report installato in un computer remoto.

4. Se si specifica un computer remoto, fare clic su **Trova** per stabilire una connessione.

5. In **Istanza server di report**selezionare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] che si desidera configurare. Nell'elenco sono visualizzate solo le istanze del server di report relative a questa versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Non è possibile configurare versioni precedenti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].

6. Selezionare **Connetti**.

## <a name="next-steps"></a>Passaggi successivi

[Portale Web](../../reporting-services/web-portal-ssrs-native-mode.md)   
[Strumenti di Reporting Services](../../reporting-services/tools/reporting-services-tools.md)   
[Configurare una connessione di Database Server di Report](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
[Gestione configurazione SQL Server](../../relational-databases/sql-server-configuration-manager.md)   
[Configurare e amministrare un Server di Report](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

