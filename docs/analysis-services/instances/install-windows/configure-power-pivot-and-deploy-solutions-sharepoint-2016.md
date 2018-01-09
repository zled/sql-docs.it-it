---
title: Configurare PowerPivot e distribuire soluzioni (SharePoint 2016) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18a48995-639f-4782-8b17-6caa5769bb5f
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cfa636d3fcf08410ecaf2062aa7cd68d1e4aeaec
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="configure-power-pivot-and-deploy-solutions-sharepoint-2016"></a>Configurare PowerPivot e distribuire soluzioni (SharePoint 2016)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Questo argomento vengono descritte la distribuzione e la configurazione di miglioramenti di livello intermedio per la [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] le caratteristiche in [!INCLUDE[SPS2016](../../../includes/sps2016-md.md)] inclusi [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] raccolta pianificazione aggiornamento dati, Dashboard di gestione e i provider di dati. Eseguire lo strumento di **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] per SharePoint 2016** per eseguire le operazioni seguenti:  
  
-   Distribuire i file di soluzione SharePoint.  
  
-   Creare un'applicazione del servizio [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] .  
  
-   Per informazioni sui servizi back-end e sull'installazione di un server [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in modalità [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] , vedere [Installazione di Analisi Services in modalità Power Pivot](../../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md).  
  
 Per informazioni sull'installazione di [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] per lo strumento di configurazione di SharePoint 2016, vedere [installare o disinstallare Power Pivot per Add-in SharePoint (SharePoint 2016)](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2016.md).  
  
 In questo argomento sono incluse le sezioni seguenti:  
  
 [Eseguire la configurazione di PowerPivot per SharePoint 2016](#bkmk_run_configuration_tool)  
  
 [Verificare la configurazione di Power Pivot](#bkmk_verify_powerpivot)  
  
 [Risolvere eventuali problemi](#bkmk_troubleshoot_issues)  
  
||  
|-|  
|**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2016|  
  
##  <a name="bkmk_run_configuration_tool"></a> Eseguire la configurazione di PowerPivot per SharePoint 2016  
 **Nota:** per completare i passaggi seguenti, è necessario essere un amministratore di farm. Se viene visualizzato un messaggio di errore simile al seguente,  
  
-   "L'utente non è un amministratore di farm. Risolvere gli errori di convalida e riprovare".  
  
 Effettuare l'accesso con l'account tramite cui è stato installato SharePoint oppure configurare l'account di configurazione come amministratore principale del sito Amministrazione centrale SharePoint.  
  
1.  Nel menu **Start** selezionare **Tutti i programmi**, quindi [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], **Strumenti di configurazione**e infine selezionare **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] per SharePoint 2016**. Gli strumenti sono elencati solo quando [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] per SharePoint è installato nel server locale.  
  
2.  Selezionare **Configura o Ripristina [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] per SharePoint** e quindi selezionare **OK**.  
  
3.  Lo strumento esegue una convalida per verificare lo stato corrente di [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] e identificare i passaggi necessari per completare la configurazione. Espandere completamente la finestra. Nella parte inferiore della finestra dovrebbe essere disponibile una barra contenente i comandi **Convalida**, **Esegui**ed **Esci** .  
  
4.  Nella scheda **Parametri** :  
  
    1.  **Nome utente account predefinito**: immettere un account utente di dominio per l'account predefinito. L'account verrà usato per eseguire il provisioning dei servizi, incluso il pool di applicazioni del servizio [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] . Non specificare un account predefinito quale Servizio di rete o Sistema locale. Le configurazioni tramite cui vengono specificati account predefiniti vengono bloccate dallo strumento.  
  
    2.  **Server di database**: è possibile utilizzare il motore di database di SQL Server supportato per la farm di SharePoint.  
  
    3.  **Passphrase**: immettere una passphrase. Se si crea una nuova farm di SharePoint, la passphrase viene utilizzata ogni volta che si aggiunge un server o un'applicazione alla farm di SharePoint. Se la farm esiste già, immettere la passphrase che consente di aggiungere un'applicazione server alla farm.  
  
    4.  Fare clic su **Creare raccolta siti** nella finestra a sinistra. Annotarsi l' **URL sito** in modo che sia possibile utilizzarlo come riferimento nei passaggi successivi. Se il server SharePoint non è ancora configurato, tramite la Configurazione guidata l'applicazione Web e gli URL della raccolta siti vengono impostati in modo predefinito sulla radice di `http://[ServerName]`. Per modificare le impostazioni predefinite, rivedere le seguenti pagine della finestra a sinistra: **Creare applicazione Web predefinita** e **Distribuire la soluzione applicazione Web**  
  
5.  Facoltativamente, rivedere i valori di input rimanenti usati per completare ogni azione. Fare clic su ogni azione nella finestra a sinistra per visualizzare e verificare i dettagli dell'azione. Per altre informazioni su ogni azione, vedere la sezione "Valori di input usati per configurare il server" in [Configurare o ripristinare Power Pivot per SharePoint 2010 (strumento di configurazione Power Pivot)](http://msdn.microsoft.com/en-us/d61f49c5-efaa-4455-98f2-8c293fa50046) .  
  
6.  Facoltativamente, rimuovere eventuali azioni che non si desidera elaborare in questo momento. Ad esempio, se si vuole configurare il servizio di archiviazione sicura in un secondo momento, selezionare **Configurare il servizio di archiviazione sicura**e quindi deselezionare la casella di controllo **Includere l'azione nell'elenco attività**.  
  
7.  Selezionare **Convalida** per verificare se le informazioni disponibili per lo strumento sono sufficienti per l'elaborazione delle azioni nell'elenco. Se si verificano errori di convalida, fare clic sugli avvisi nel riquadro a sinistra per visualizzare i dettagli dell'errore di convalida. Correggere eventuali errori di convalida, quindi selezionare di nuovo **Convalida** .  
  
8.  Selezionare **Esegui** per elaborare tutte le azioni nell'elenco attività. Si noti che dopo aver convalidato le azioni, il comando **Esegui** diventa disponibile. Se **Esegui** non è abilitato, selezionare **Convalida** .  
  
 Per altre informazioni, vedere [Configurare o ripristinare Power Pivot per SharePoint 2010 (strumento di configurazione Power Pivot)](http://msdn.microsoft.com/en-us/d61f49c5-efaa-4455-98f2-8c293fa50046)  
  
##  <a name="bkmk_verify_powerpivot"></a> Verificare la configurazione di Power Pivot  
 **Servizi:**  
  
1.  In Amministrazione centrale, in Impostazioni di sistema, selezionare **Gestisci servizi nel server**.  
  
2.  Verificare che **SQL Server [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] servizio di sistema** viene avviato.  
  
 **Funzionalità della farm:**  
  
1.  In Amministrazione centrale, in Impostazioni di sistema, selezionare **Gestisci caratteristiche farm**.  
  
2.  Verificare che la **Funzionalità di integrazione[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]** sia **Attiva**.  
  
 **Funzionalità della raccolta siti:**  
  
1.  Selezionare l'URL del sito creato tramite lo strumento di configurazione.  
  
     Selezionare **impostazioni**![impostazioni SharePoint](../../../analysis-services/media/as-sharepoint2013-settings-gear.gif "le impostazioni di SharePoint"), quindi fare clic su **Impostazioni sito**.  
  
     Selezionare **Caratteristiche raccolta siti**.  
  
2.  Verificare che l' **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] per le raccolte siti** sia **attiva**.  
  
 **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] :**  
  
1.  In Amministrazione centrale, in **Gestione applicazioni**, selezionare **Gestisci applicazioni di servizio**.  
  
2.  Verificare che lo stato dell'applicazione di servizio sia **Avviato**. Il nome predefinito è **Applicazione del servizio [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] predefinita**.  
  
     Selezionare il nome dell'applicazione di servizio per aprire il dashboard di gestione [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] da cui è possibile aprire l'applicazione del servizio. Al primo utilizzo, il dashboard potrebbe impiegare diversi minuti per il caricamento.  
  
 Per altre informazioni, vedere [Verify a Power Pivot for SharePoint Installation](../../../analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation.md).  
  
##  <a name="bkmk_troubleshoot_issues"></a> Risolvere eventuali problemi  
 Per ricevere assistenza durante la risoluzione dei problemi, è consigliabile verificare che la registrazione diagnostica sia abilitata.  
  
1.  In Amministrazione centrale SharePoint fare clic su **Monitoraggio** , quindi selezionare **Configura raccolta dati di utilizzo e integrità**.  
  
2.  Verificare che l'opzione **Abilita raccolta dati di utilizzo** sia selezionata.  
  
3.  Verificare che gli eventi seguenti siano selezionati:  
  
    -   Definizione dei campi di utilizzo per la telemetria del settore formativo  
  
    -   [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Connessioni  
  
    -   [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Utilizzo dati di caricamento  
  
    -   [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Utilizzo query  
  
    -   [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Utilizzo dati di scaricamento  
  
4.  Verificare che l'opzione **Abilita raccolta dati integrità** sia selezionata.  
  
5.  Fare clic su **OK**.  
  
 Per altre informazioni sulla risoluzione dei problemi relativi all'aggiornamento dei dati, vedere [Troubleshooting Power Pivot Data Refresh](http://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) (Risoluzione dei problemi di aggiornamento dei dati di Power Pivot (http://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx).  
  
 Per altre informazioni sullo strumento di configurazione, vedere [Strumenti di configurazione di Power Pivot](../../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md).  
  
  
