---
title: Configurare SCOM per il monitoraggio di sistema della piattaforma Analitica
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4dba9b50-1447-45fc-b219-b9fc99d47d8d
caps.latest.revision: "10"
ms.openlocfilehash: f9c8a778afad89abea9ad4fd092fefb15844a5ae
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="configure-scom-to-monitor-analytics-platform-system"></a>Configurare SCOM per il monitoraggio di sistema della piattaforma Analitica
Seguire questi passaggi per configurare i Management Pack di System Center Operations Manager (SCOM) per il sistema di piattaforma Analitica. I Management Pack sono necessari per il monitoraggio di sistema della piattaforma Analitica da SCOM.  
  
## <a name="BeforeBegin"></a>Prima di iniziare  
**Prerequisiti**  
  
System Center Operations Manager 2007 R2 deve essere installato e in esecuzione.  
  
I management pack deve essere installato e configurato. Vedere [installa i Management Pack SCOM &#40; Sistema della piattaforma Analitica &#41; ](install-the-scom-management-packs.md) e [importare il Management Pack SCOM per PDW &#40; Sistema della piattaforma Analitica &#41; ](import-the-scom-management-pack-for-pdw.md).  
  
## <a name="ConfigureRunAsProfile"></a>Configurare i profili runas in System Center  
Per configurare System Center, è necessario eseguire la procedura seguente:  
  
-   Creare account RunAs per il **APS Watcher** utente di dominio e mapparlo al **Account Watcher punti di accesso di Microsoft.**  
  
-   Creare account RunAs per il **monitoring_user** utente APS ed eseguire il mapping per il **Account azione dei punti di accesso di Microsoft**.  
  
Di seguito sono fornite istruzioni dettagliate su come è possibile farlo:  
  
1.  Creare il **APS Watcher** account RunAs con **Windows** account di tipo per il **APS Watcher** utente di dominio.  
  
    1.  Passare il **amministrazione** destro del mouse sul riquadro **configurazione runas** -> **account** e selezionare **crea Account runas...**  
  
        ![ConfigureScomCreateRunAsAccount](./media/configure-scom-to-monitor-analytics-platform-system/ConfigureScomCreateRunAsAccount.png "ConfigureScomCreateRunAsAccount")  
  
    2.  Il **Creazione guidata Account runas** finestra di dialogo verrà aperto. Nel **Introduzione** pagina fare clic su **Avanti**.  
  
    3.  Nel **proprietà generali** pagina selezionare **Windows** da **tipo Account runas** e specificare "Controllo APS" come il **nome visualizzato**.  
  
        ![CreateRunAsAccountWizardGeneralProperties](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties.png "CreateRunAsAccountWizardGeneralProperties")  
  
    4.  Nel **credenziali** pagina specificare le credenziali utente di dominio di "Controllo APS".  
  
        ![CreateRunAsAccountWizardCredentials](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials.png "CreateRunAsAccountWizardCredentials")  
  
    5.  Nel **sicurezza distribuzione** pagina selezionare **meno sicura** e fare clic su di **crea** pulsante per terminare.  
  
        ![CreateRunAsAccountWizardDistributionSecurity](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardDistributionSecurity.png "CreateRunAsAccountWizardDistributionSecurity")  
  
        1.  Se si decide di utilizzare il **più sicuro** opzione, è necessario specificare manualmente i computer per le credenziali verrà distribuite. A tale scopo, dopo aver creato l'account RunAs, fare clic su di esso e selezionare **proprietà**.  
  
        2.  Passare il **distribuzione** scheda e **Aggiungi** computer desiderato.  
  
            ![RunAsAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/RunAsAccountProperties.png "RunAsAccountProperties")  
  
2.  Impostare il **Microsoft APS controllo Account** profilo da utilizzare **APS Watcher** account RunAs.  
  
    1.  Passare a **amministrazione** -> **configurazione runas** -> **profili**.  
  
        ![AdministrationRunAsConfigurationProfiles](./media/configure-scom-to-monitor-analytics-platform-system/AdministrationRunAsConfigurationProfiles.png "AdministrationRunAsConfigurationProfiles")  
  
    2.  Fare clic con il pulsante destro su **Microsoft APS Watcher Account** dall'elenco e selezionare **proprietà**.  
  
        ![MicrosoftApsWatcherAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/MicrosoftApsWatcherAccountProperties.png "MicrosoftApsWatcherAccountProperties")  
  
    3.  Il **eseguire Creazione guidata profilo runas** finestra di dialogo verrà aperto. Ignora il **Introduzione** pagina facendo clic su **Avanti**.  
  
    4.  Nel **proprietà generali** pagina fare clic su **Avanti**.  
  
    5.  Nel **account RunAs** pagina fare clic su di **Aggiungi...** e selezionare creato in precedenza **APS Watcher** account RunAs.  
  
        ![RunAsProfileWizardAdd](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd.png "RunAsProfileWizardAdd")  
  
    6.  Fare clic su **salvare** per completare l'assegnazione di profilo.  
  
3.  Attendere il completamento dell'individuazione di dispositivi di punti di accesso.  
  
    1.  Passare al **monitoraggio** riquadro e aprire il **dispositivo di SQL Server** -> **Microsoft Analitica Platform System**  ->   **Accessori** visualizzazione stato.  
  
        ![SqlServerApplianceMicrosoftApsAppliances](./media/configure-scom-to-monitor-analytics-platform-system/SqlServerApplianceMicrosoftApsAppliances.png "SqlServerApplianceMicrosoftApsAppliances")  
  
    2.  Attendere che il dispositivo viene visualizzato nell'elenco. Il nome del dispositivo deve essere uguale a quello specificato nel Registro di sistema.  
  
    Al termine dell'individuazione dovrebbe essere elencato, ma non monitorati tutti i dispositivi. Affinché il monitoraggio di lavoro, seguire i passaggi successivi.  
  
    > [!NOTE]  
    > Mentre si attende per completare l'individuazione iniziale dello strumento, è possono eseguire i passaggi successivi in parallelo.  
  
4.  Creare un altro nuovo account RunAs per eseguire query dei punti di accesso per il recupero dei dati di integrità.  
  
    1.  Iniziare a creare un nuovo account RunAs, come descritto nel passaggio 1.  
  
    2.  Nel **proprietà generali** pagina selezionare **l'autenticazione di base** tipo di account.  
  
        ![CreateRunAsAccountWizardGeneralProperties2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties2.png "CreateRunAsAccountWizardGeneralProperties2")  
  
    3.  Nel **credenziali** pagina specificare credenziali valide per accedere allo stato di integrità APS DMV.  
  
        ![CreateRunAsAccountWizardCredentials2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials2.png "CreateRunAsAccountWizardCredentials2")  
  
5.  Configurare il **Account azione dei punti di accesso di Microsoft** profilo da utilizzare l'account RunAs appena creato per l'istanza di punti di accesso.  
  
    1.  Passare il **Account azione dei punti di accesso di Microsoft** proprietà come descritto nel passaggio 2.  
  
    2.  Nel **account RunAs** pagina fare clic su **Aggiungi...** Selezionare l'account RunAs appena creato.  
  
        ![RunAsProfileWizardAdd2](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd2.png "RunAsProfileWizardAdd2")  
  
## <a name="next-step"></a>Passaggio successivo  
Ora che è stato configurato il Management Pack, si è pronti per avviare il monitoraggio del dispositivo. Per ulteriori informazioni, vedere [monitorare l'accessorio tramite System Center Operations Manager &#40; Sistema della piattaforma Analitica &#41; ](monitor-the-appliance-by-using-system-center-operations-manager.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
