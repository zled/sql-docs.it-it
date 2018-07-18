---
title: Configurare SCOM per il monitoraggio di sistema della piattaforma Analitica | Documenti Microsoft
description: Seguire questi passaggi per configurare i management pack di System Center Operations Manager (SCOM) per il sistema di piattaforma Analitica. I Management Pack sono necessari per il monitoraggio di sistema della piattaforma Analitica da SCOM.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 4c2e8a42d488c18e705c9d7d8c1d53c9ff7c9cb8
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="configure-system-center-operations-manager-scom-to-monitor-analytics-platform-system"></a>Configurare System Center Operations Manager (SCOM) per il monitoraggio di sistema della piattaforma Analitica
Seguire questi passaggi per configurare i Management Pack di System Center Operations Manager (SCOM) per il sistema di piattaforma Analitica. I Management Pack sono necessari per il monitoraggio di sistema della piattaforma Analitica da SCOM.  
  
## <a name="BeforeBegin"></a>Prima di iniziare  
**Prerequisiti**  
  
System Center Operations Manager 2007 R2 deve essere installato e in esecuzione.  
  
I management pack deve essere installato e configurato. Vedere [installare i Management Pack SCOM &#40;Analitica Platform System&#41; ](install-the-scom-management-packs.md) e [Importa Management Pack di SCOM per PDW &#40;Analitica Platform System&#41;](import-the-scom-management-pack-for-pdw.md).  
  
## <a name="ConfigureRunAsProfile"></a>Configurare i profili runas in System Center  
Per configurare System Center, è necessario eseguire la procedura seguente:  
  
-   Creare account RunAs per il **APS Watcher** utente di dominio e mapparlo al **Microsoft APS Watcher Account.**  
  
-   Creare account RunAs per il **monitoring_user** utente APS ed eseguire il mapping per il **Account azione dei punti di accesso di Microsoft**.  
  
Di seguito sono fornite istruzioni dettagliate su come eseguire le attività:  
  
1.  Creare il **APS Watcher** account RunAs con **Windows** account di tipo per il **APS Watcher** utente di dominio.  
  
    1.  Passare il **amministrazione** pulsante destro del mouse nel riquadro **Run As Configuration** -> **account** e selezionare **crea Account runas...**  
  
        ![ConfigureScomCreateRunAsAccount](./media/configure-scom-to-monitor-analytics-platform-system/ConfigureScomCreateRunAsAccount.png "ConfigureScomCreateRunAsAccount")  
  
    2.  Il **Creazione guidata Account runas** finestra di dialogo verrà aperto. Nel **Introduzione** pagina, fare clic su **Avanti**.  
  
    3.  Nel **delle proprietà generali** pagina, selezionare **Windows** dal **tipo Account runas** e specificare "APS Watcher" come il **nome visualizzato**.  
  
        ![CreateRunAsAccountWizardGeneralProperties](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties.png "CreateRunAsAccountWizardGeneralProperties")  
  
    4.  Nel **credenziali** pagina ![CreateRunAsAccountWizardCredentials](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials.png "CreateRunAsAccountWizardCredentials")  
  
    5.  Nel **protezione di distribuzione** pagina, selezionare **una soluzione meno sicura** e fare clic sul **crea** pulsante per terminare.  
  
        ![CreateRunAsAccountWizardDistributionSecurity](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardDistributionSecurity.png "CreateRunAsAccountWizardDistributionSecurity")  
  
        1.  Se si decide di utilizzare il **più sicuro** opzione, è necessario specificare manualmente i computer in cui le credenziali verranno distribuite. A tale scopo, dopo aver creato l'account RunAs, fare clic su di esso e selezionare **proprietà**.  
  
        2.  Passare il **distribuzione** scheda e **Aggiungi** computer desiderato.  
  
            ![RunAsAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/RunAsAccountProperties.png "RunAsAccountProperties")  
  
2.  Impostare il **Microsoft APS controllo Account** profilo da utilizzare **APS Watcher** account RunAs.  
  
    1.  Passare a **amministrazione** -> **configurazione runas** -> **profili**.  
  
        ![AdministrationRunAsConfigurationProfiles](./media/configure-scom-to-monitor-analytics-platform-system/AdministrationRunAsConfigurationProfiles.png "AdministrationRunAsConfigurationProfiles")  
  
    2.  Fare clic con il pulsante destro su **Microsoft APS Watcher Account** dall'elenco e selezionare **proprietà**.  
  
        ![MicrosoftApsWatcherAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/MicrosoftApsWatcherAccountProperties.png "MicrosoftApsWatcherAccountProperties")  
  
    3.  Il **eseguire Creazione guidata profilo runas** finestra di dialogo verrà aperto. Ignora il **Introduzione** pagina facendo clic su **Avanti**.  
  
    4.  Nel **proprietà generali** pagina, fare clic su **Avanti**.  
  
    5.  Nel **gli account RunAs** fare clic sul **Aggiungi...** e selezionare creato in precedenza **APS Watcher** account RunAs.  
  
        ![RunAsProfileWizardAdd](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd.png "RunAsProfileWizardAdd")  
  
    6.  Fare clic su **salvare** per completare l'assegnazione di profilo.  
  
3.  Attendere il completamento dell'individuazione di dispositivi di punti di accesso.  
  
    1.  Passare al **monitoraggio** riquadro e aprire il **dispositivo di SQL Server** -> **Microsoft Analitica Platform System**  ->   **Accessori** visualizzazione stato.  
  
        ![SqlServerApplianceMicrosoftApsAppliances](./media/configure-scom-to-monitor-analytics-platform-system/SqlServerApplianceMicrosoftApsAppliances.png "SqlServerApplianceMicrosoftApsAppliances")  
  
    2.  Attendere che il dispositivo viene visualizzato nell'elenco. Il nome del dispositivo deve essere uguale a quello specificato nel Registro di sistema. Al termine dell'individuazione dovrebbe essere elencato, ma non monitorati tutti i dispositivi. Per abilitare il monitoraggio, seguire i passaggi successivi.  
  
    > [!NOTE]  
    > Mentre si attende per completare l'individuazione iniziale dello strumento, è possono eseguire i passaggi successivi in parallelo.  
  
4.  Creare un altro nuovo account RunAs per eseguire query dei punti di accesso per il recupero dei dati di integrità.  
  
    1.  Iniziare a creare un nuovo account RunAs, come descritto nel passaggio 1.  
  
    2.  Nel **delle proprietà generali** pagina, selezionare **l'autenticazione di base** tipo di account.  
  
        ![CreateRunAsAccountWizardGeneralProperties2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties2.png "CreateRunAsAccountWizardGeneralProperties2")  
  
    3.  Nel **credenziali** pagina, immettere credenziali valide per accedere allo stato di integrità APS viste a gestione dinamica.  
  
        ![CreateRunAsAccountWizardCredentials2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials2.png "CreateRunAsAccountWizardCredentials2")  
  
5.  Configurare il **Account azione dei punti di accesso di Microsoft** profilo da utilizzare l'account RunAs appena creato per l'istanza di punti di accesso.  
  
    1.  Passare il **Account azione dei punti di accesso di Microsoft** proprietà come descritto nel passaggio 2.  
  
    2.  Nel **gli account RunAs** fare clic su **Aggiungi...** e 
    3.  Selezionare l'account RunAs appena creato.  
  
        ![RunAsProfileWizardAdd2](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd2.png "RunAsProfileWizardAdd2")  
  
## <a name="next-step"></a>Passaggio successivo  
Ora che è stato configurato il Management Pack, si è pronti per avviare il monitoraggio del dispositivo. Per altre informazioni, vedere [monitorare l'accessorio by Using System Center Operations Manager &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
