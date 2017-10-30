---
title: Aggiornare pacchetti di Integration Services | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Integration Services, migrating
- migrating packages [Integration Services]
ms.assetid: 68dbdf81-032c-4a73-99f6-41420e053980
caps.latest.revision: 54
author: MikeRayMSFT
ms.author: mikeray
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: a2e3655bedbb24f2174a62c8792cd168e7642592
ms.openlocfilehash: b04ba24fd90ec81e735933a45fed18294d77ceab
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="upgrade-integration-services-packages"></a>Aggiornare pacchetti di Integration Services
  Quando si esegue l'aggiornamento di un'istanza di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] alla versione corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], i pacchetti di [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] esistenti non vengono automaticamente aggiornati al formato dei pacchetti usato dalla versione corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . A tale scopo, sarà necessario selezionare un metodo di aggiornamento e aggiornare manualmente i pacchetti.  
  
 Per informazioni sull'aggiornamento dei pacchetti quando si converte un progetto modello di distribuzione del progetto, vedere [distribuire Integration Services (SSIS) progetti e pacchetti](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md)
  
## <a name="selecting-an-upgrade-method"></a>Selezione di un metodo di aggiornamento  
 Sono disponibili diversi metodi di aggiornamento dei pacchetti di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] . Per alcuni di questi metodi l'aggiornamento è solo temporaneo, mentre per altri è permanente. Nella tabella seguente viene descritto ciascun metodo e viene indicato se l'aggiornamento è temporaneo o permanente.  
  
> [!NOTE]  
>  Quando si esegue un pacchetto di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] con l'utilità **dtexec** (dtexec.exe) installata con la versione corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'aggiornamento temporaneo del pacchetto aumenta il tempo di esecuzione. La frequenza di aumento del tempo di esecuzione varia a seconda della dimensione del pacchetto. Per evitare un aumento del tempo di esecuzione, si consiglia di aggiornare il pacchetto prima di eseguirlo.  
  
|Metodo di aggiornamento|Tipo di aggiornamento|  
|--------------------|---------------------|  
|Eseguire l'utilità **dtexec** (dtexec.exe) installata con la versione corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire un pacchetto di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] .<br /><br /> Per altre informazioni, vedere [dtexec Utility](../../integration-services/packages/dtexec-utility.md).|L'aggiornamento del pacchetto è temporaneo.<br /><br /> Le modifiche non possono essere salvate.|  
|Aprire un file di pacchetto di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].|L'aggiornamento del pacchetto è permanente se si salva il pacchetto; in caso contrario, è temporaneo.|  
|Aggiungere un pacchetto di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a un progetto esistente in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].|L'aggiornamento del pacchetto è permanente.|  
|Aprire un file di progetto [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] o successivo in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], quindi usare l'Aggiornamento guidato pacchetti [!INCLUDE[ssIS](../../includes/ssis-md.md)] per aggiornare più pacchetti nel progetto.<br /><br /> Per altre informazioni, vedere [Aggiornare i pacchetti di Integration Services mediante l'Aggiornamento guidato pacchetti SSIS](../../integration-services/install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md) e [Guida sensibile al contesto dell'Aggiornamento guidato pacchetti SSIS](../../integration-services/ssis-package-upgrade-wizard-f1-help.md).|L'aggiornamento del pacchetto è permanente.|  
|Eseguire l'utilità <xref:Microsoft.SqlServer.Dts.Runtime.Application.Upgrade%2A> per aggiornare uno o più pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|L'aggiornamento del pacchetto è permanente.|  
  
## <a name="custom-applications-and-custom-components"></a>Applicazioni e componenti personalizzati  
 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] non funzionano con la versione corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 È possibile usare la versione corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per eseguire e gestire pacchetti che includono componenti personalizzati [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)][!INCLUDE[ssIS](../../includes/ssis-md.md)] . Sono state aggiunte quattro regole di reindirizzamento di associazione nei file seguenti per consentire il reindirizzamento degli assembly di runtime dalla versione 10.0.0.0 ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]), 11.0.0.0 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) o 12.0.0.0 ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) alla versione 13.0.0.0 ([!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).  
  
-   DTExec.exe.config  
  
-   dtshost.exe.config  
  
-   DTSWizard.exe.config  
  
-   DTUtil.exe.config  
  
-   DTExecUI.exe.config  
  
 Per utilizzare [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] per progettare pacchetti che includono [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] componenti personalizzati, è necessario modificare il file devenv.exe config si trova in  *\<unità >*: \Programmi\Microsoft Visual Studio 10.0\Common7\IDE.  
  
 Per utilizzare questi pacchetti con le applicazioni dei clienti che vengono compilate con il runtime per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], includere le regole di reindirizzamento nella sezione di configurazione del file *.exe.config per il file eseguibile. Le regole reindirizzano gli assembly di runtime alla versione 13.0.0.0 ([!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]). Per ulteriori informazioni sul reindirizzamento della versione dell'assembly, vedere [ \<assemblyBinding > elemento per \<runtime >](http://msdn.microsoft.com/library/twy1dw1e.aspx).  
  
### <a name="locating-the-assemblies"></a>Individuazione degli assembly  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] gli assembly [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sono stati aggiornati a .NET 4.0. È una global assembly cache separata per .NET 4 in  *\<unità >*: \Windows\Microsoft.net\assembly.. Tutti gli assembly di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] possono essere individuati in questo percorso, generalmente nella cartella GAC_MSIL.  
  
 Come nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], i componenti di base [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] file DLL di estendibilità sono anche disponibili in  *\<unità >*: \Programmi\Microsoft SQL Server\130\SDK\Assemblies.  
  
## <a name="understanding-sql-server-package-upgrade-results"></a>Informazioni sui risultati dell'aggiornamento dei pacchetti di SQL Server  
 Durante il processo di aggiornamento dei pacchetti, la maggior parte dei componenti e delle funzionalità dei pacchetti di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] viene convertita facilmente nella controparte della versione corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Diversi componenti e funzionalità, tuttavia, non verranno aggiornati o avranno risultati di cui è consigliabile tenere conto. Nella tabella seguente vengono identificati tali componenti e funzionalità.  
  
> [!NOTE]  
>  Per identificare i pacchetti interessati dai problemi inclusi nella tabella, eseguire Preparazione aggiornamento.  
  
|Componente o funzionalità|Risultati dell'aggiornamento|  
|--------------------------|---------------------|  
|Stringhe di connessione|Per i pacchetti di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] , i nomi di alcuni provider sono stati modificati e nelle stringhe di connessione vengono richiesti valori diversi. Per aggiornare le stringhe di connessione, utilizzare una delle procedure seguenti:<br /><br /> Utilizzare l'Aggiornamento guidato pacchetti [!INCLUDE[ssIS](../../includes/ssis-md.md)] per aggiornare il pacchetto e selezionare l'opzione **Aggiorna stringhe di connessione per l'uso di nuovi nomi di provider** .<br /><br /> Nella pagina Generale della finestra di dialogo Opzioni di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]selezionare l'opzione **Aggiorna stringhe di connessione per l'uso di nuovi provider** . Per ulteriori informazioni su questa opzione, vedere la pagina generale.<br /><br /> In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il pacchetto e modificare manualmente il testo della proprietà ConnectionString.<br /><br /> Non è possibile usare le procedure precedenti per aggiornare una stringa di connessione quando è archiviata in un file di configurazione o in un file di origine dati oppure quando un'espressione imposta la proprietà **ConnectionString** . In questi casi, per aggiornare la stringa di connessione è necessario aggiornare manualmente il file o l'espressione.<br /><br /> Per altre informazioni sulle origini dati, vedere [Origini dati](../../integration-services/connection-manager/data-sources.md).|  
  
### <a name="scripts-that-depend-on-adodbdll"></a>Script che dipendono da ADODB.dll  
 Script dell'attività Script e del componente script che fanno riferimento in modo esplicito ad ADODB.dll non possono essere aggiornati o eseguiti in computer senza [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] installato. Per aggiornare questi script Attività script o Componente script, si consiglia di rimuovere la dipendenza da ADODB.dll.  Ado.Net è l'alternativa consigliata per il codice gestito, ad esempio gli script VB e C#.  
  
  

