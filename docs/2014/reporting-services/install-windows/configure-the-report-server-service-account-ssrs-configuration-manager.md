---
title: Configurare l'account del servizio del server di report (Gestione configurazione SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: f880c623-67c8-4167-b98b-ace17e800faa
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 546cf8172cbfc2e13b0953207078f3b2cc9dc146
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48082521"
---
# <a name="configure-the-report-server-service-account-ssrs-configuration-manager"></a>Configurare l'account del servizio del server di report (Gestione configurazione SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] viene implementato come singolo servizio contenente un servizio Web ReportServer, Gestione report e un'applicazione di elaborazione in background utilizzata per l'elaborazione pianificata di report e il recapito di sottoscrizioni. In questo argomento vengono illustrate la configurazione iniziale dell'account del servizio e la modifica dell'account o della password tramite lo strumento di configurazione di Reporting Services.  
  
## <a name="initial-configuration"></a>Configurazione iniziale  
 L'account del servizio del server di report viene definito durante l'installazione. È possibile eseguire il servizio con un account utente di dominio o un oggetto incorporato, ad esempio `NetworkService` account. Nessun account predefinito; qualunque sia l'account specificato nella [configurazione Server - account di servizio](../../sql-server/install/server-configuration-service-accounts.md) pagina dell'installazione guidata diventerà l'account iniziale del servizio Server di Report.  
  
> [!IMPORTANT]  
>  Anche se il servizio Web ReportServer e gestione Report siano [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] le applicazioni, non vengono eseguite con la [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] account. L'architettura del servizio esegue entrambe le applicazioni ASP.NET all'interno della stessa identità di processo del server di report. Si tratta di un'importante differenza rispetto alle versioni precedenti, in cui sia il servizio Web ReportServer sia Gestione report vengono eseguite utilizzando la stessa identità del processo di lavoro [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] specificata in IIS.  
  
## <a name="changing-the-service-account"></a>Modifica dell'account del servizio  
 Per visualizzare e riconfigurare le informazioni sull'account del servizio, utilizzare sempre lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Le informazioni sull'identità del servizio sono archiviate internamente in più percorsi. L'utilizzo dello strumento garantisce che tutti i riferimenti vengano aggiornati di conseguenza ogni volta che si modifica l'account o la password. Lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] effettua le operazioni supplementari seguenti per garantire la disponibilità del server di report:  
  
-   Aggiunta automatica del nuovo account al gruppo di server di report creato nel computer locale. Questo gruppo è specificato negli elenchi di controllo di accesso (ACL) utilizzati per la protezione dei file di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   Aggiornamento automatico delle autorizzazioni di accesso nell'istanza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance used to host the report server database. Il nuovo account verrà aggiunto a **RSExecRole**.  
  
     L'account di accesso al database per l'account precedente non verrà rimosso automaticamente. Assicurarsi di rimuovere gli account non più in uso. Per altre informazioni, vedere [Amministrare un database del server di report &#40;modalità nativa SSRS&#41;](../report-server/report-server-database-ssrs-native-mode.md) nella documentazione online di SQL Server.  
  
     Al nuovo account del servizio vengono concesse autorizzazioni per il database solo se la connessione al database del server di report è stata configurata fin dall'inizio per l'utilizzo dell'account del servizio. Se la connessione al database del server di report è stata configurata per l'utilizzo di un account utente di dominio o di un account di accesso al database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , l'aggiornamento dell'account del servizio non influisce sulle informazioni di connessione.  
  
-   Aggiornamento automatico della chiave di crittografia per includere le informazioni sul profilo del nuovo account.  
  
    > [!NOTE]  
    >  Se il server di report fa parte di una distribuzione con scalabilità orizzontale, la modifica interesserà solo il server di report che si sta aggiornando. Le chiavi di crittografia per gli altri server di report della distribuzione non sono interessate dalla modifica dell'account del servizio.  
  
 Per istruzioni su come impostare l'account, vedere [configurare un Account del servizio &#40;Gestione configurazione SSRS&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md).  
  
## <a name="choosing-an-account"></a>Scelta di un account  
 È possibile configurare il servizio del server di report per l'esecuzione con uno dei tipi di account seguenti:  
  
-   Account utente di Windows con privilegi minimi  
  
-   NetworkService  
  
-   LocalSystem  
  
-   LocalService  
  
 Non esiste un approccio ottimale per la scelta del tipo di account. Ogni account presenta vantaggi e svantaggi di cui è necessario tenere conto. Se si sta distribuendo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in un server di produzione, le procedure consigliate indicano di configurare il servizio venga eseguito con un account utente di dominio in modo che è possibile evitare danni estesi se un account condiviso risulta compromesso da un utente malintenzionato. In questo modo, viene inoltre semplificato il controllo dell'attività di accesso per l'account. Un compromesso relativo all'utilizzo di un account utente di Windows è che, se si sta distribuendo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in una rete che utilizza l'autenticazione Kerberos, è necessario registrare il servizio con l'account utente. Per altre informazioni, vedere [Registrare un nome dell'entità servizio &#40;SPN&#41; per un server di report](../report-server/register-a-service-principal-name-spn-for-a-report-server.md).  
  
 Per la scelta dell'approccio ottimale per la propria distribuzione, è possibile utilizzare le linee guida e i collegamenti seguenti.  
  
-   [Account del servizio &#40;modalità nativa SSRS&#41;](../../sql-server/install/service-account-ssrs-native-mode.md).  
  
-   [Configurare account di servizio e autorizzazioni di Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) nella documentazione online di SQL Server.  
  
-   [Guida alla pianificazione della sicurezza dei servizi e degli account dei servizi](http://go.microsoft.com/fwlink/?LinkId=69155) nel sito Web MSDN.  
  
## <a name="updating-an-expired-password"></a>Aggiornamento di una password scaduta  
 Se il servizio del server di report viene eseguito con un account di dominio e la password scade prima che sia possibile aggiornarla nello strumento di configurazione di Reporting Services, il servizio non verrà avviato se prima non si specifica una nuova password. Se il servizio non può essere avviato, non è possibile utilizzare lo strumento di configurazione di Reporting Services per connettersi al server e aggiornare l'account. In questo caso, è necessario utilizzare una combinazione di strumenti per riportare il server online.  
  
 Per reimpostare la password, effettuare le operazioni seguenti:  
  
1.  Nel **avviare** dal menu **Pannello di controllo**, scegliere **strumenti di amministrazione**, fare clic su **servizi**.  
  
2.  Fare doppio clic su **SQL Server Reporting Services**, selezionare **proprietà**.  
  
3.  Fare clic su **Accedi**e digitare la nuova password.  
  
4.  Dopo avere aggiornato la password, avviare lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e aggiornare la password nella pagina Account servizio. Tale passaggio aggiuntivo è necessario per aggiornare le informazioni sull'account archiviate internamente dal server di report.  
  
 Se la password dell'account del servizio per il [!INCLUDE[ssDE](../../includes/ssde-md.md)] scade, quando si tenterà di connettersi al server di report verrà restituito l'errore `rsReportServerDatabaseUnavailable`. Per risolvere l'errore è necessario reimpostare la password.  
  
## <a name="configuring-the-report-server-service-for-a-sharepoint-integrated-report-server"></a>Configurazione del servizio del server di report per un server di report integrato con SharePoint  
 Se si esegue un server di report in modalità integrata SharePoint, è necessario aggiornare le informazioni sull'account del servizio archiviate nel database di configurazione di SharePoint nei casi seguenti.  
  
-   Modifica il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service account (ad esempio, il passaggio da NetworkService a un account utente di dominio).  
  
-   Estensione di una farm di SharePoint per includere un'applicazione Web di SharePoint aggiuntiva. Se la server farm è configurata per l'integrazione del server di report e la nuova applicazione aggiunta è configurata per l'esecuzione di un account utente diverso rispetto alle altre applicazioni nella farm, è necessario aggiornare le informazioni di accesso al database.  
  
 Dopo avere reimpostato le informazioni di accesso al database, è consigliabile riavviare il servizio [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] per garantire che la connessione precedente non venga più utilizzata.  
  
1.  Nelle **strumenti di amministrazione**, fare clic su **Amministrazione centrale SharePoint 2010**.  
  
2.  Fare clic su **Gestione applicazioni**.  
  
3.  Nella sezione Reporting Services, fare clic su **Concedi accesso al Database**.  
  
4.  Fare clic su **OK**. Verrà visualizzata la finestra di dialogo Immissione credenziali.  
  
5.  Immettere le credenziali di un utente membro del gruppo locale Administrators sul computer che ospita il server di report. Tali credenziali verranno utilizzate per una connessione occasionale al computer server di report per recuperare le informazioni sull'account del servizio. L'account di accesso al database creato per ogni account del servizio verrà aggiornato nei database di SharePoint.  
  
6.  Per riavviare il servizio, fare clic su **operazioni**.  
  
7.  In topologia e servizi, fare clic su **servizi nel Server**.  
  
8.  Per l'applicazione Web di Windows SharePoint Services, fare clic su **arrestare**.  
  
9. Attendere l'arresto del servizio.  
  
10. Fare clic su **avviare**.  
  
> [!NOTE]  
>  I prodotti e le tecnologie SharePoint richiedono l'utilizzo di account di dominio per la configurazione di servizi, ad esempio Reporting Services con modalità SharePoint.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare un Account del servizio &#40;Gestione configurazione SSRS&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)   
 [Account del servizio &#40;modalità nativa SSRS&#41;](../../sql-server/install/service-account-ssrs-native-mode.md)   
 [Configurare gli URL di Server di Report &#40;Gestione configurazione SSRS&#41;](configure-report-server-urls-ssrs-configuration-manager.md)   
 [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
