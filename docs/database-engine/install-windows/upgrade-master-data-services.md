---
title: "Aggiornare Master Data Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c3543f3-3eb9-455d-a9bf-f17e9506ad21
caps.latest.revision: 31
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 30
---
# Aggiornare Master Data Services
  Di seguito sono descritti gli scenari di aggiornamento a Microsoft [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
-   [Aggiornare senza aggiornamento del motore di database](../../database-engine/install-windows/upgrade-master-data-services.md#noengine)  
  
-   [Aggiornare con l'aggiornamento del motore di database](../../database-engine/install-windows/upgrade-master-data-services.md#engine)  
  
-   [Aggiornare in uno scenario con due computer](../../database-engine/install-windows/upgrade-master-data-services.md#twocomputer)  
  
-   [Aggiornare con il ripristino di un database da un backup](../../database-engine/install-windows/upgrade-master-data-services.md#restore)  
  
> [!IMPORTANT]  
>  -   L'aggiornamento dalla versione [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP1 alla versione CTP2 non è supportato.  
> -   Eseguire il backup del database prima di effettuare qualsiasi aggiornamento.  
> -   Con il processo di aggiornamento vengono ricreate le stored procedure e le tabelle aggiornate utilizzate da [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Le personalizzazioni apportate a questi componenti potrebbero andare perse.  
> -   I pacchetti di distribuzione di modelli possono essere utilizzati solo nell'edizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzata per crearli. Non è possibile distribuire i pacchetti di distribuzione del modello creati in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
> -   Dopo l'aggiornamento di Data Quality Services e Master Data Services a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], tutte le versioni precedenti del componente aggiuntivo Master Data Services per Excel non funzioneranno più. È possibile scaricare il componente aggiuntivo Master Data Services di [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] per Excel dall'[Area download Microsoft](http://www.microsoft.com/en-us/download/details.aspx?id=47343).  
  
##  <a name="fileLocation"></a> Percorso del file  
  
-   Per impostazione predefinita, in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] i file sono installati in *unità*:\Programmi\Microsoft SQL Server\130\Master Data Services.  
  
-   Per impostazione predefinita, in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] i file sono installati in *unità*:\Programmi\Microsoft SQL Server\120\Master Data Services.  
  
-   Per impostazione predefinita, in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] i file sono installati in *unità*:\Programmi\Microsoft SQL Server\110\Master Data Services.  
  
-   Per impostazione predefinita, in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] i file sono installati in *unità*:\Programmi\Microsoft SQL Server\Master Data Services.  
  
##  <a name="noengine"></a> Aggiornare senza aggiornamento del motore di database  
 In questo scenario si continua a usare [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] per ospitare il database MDS. Tuttavia, è necessario aggiornare lo schema del database MDS e, successivamente, creare un'applicazione Web [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per accedere al database MDS. L'accesso al database MDS non può essere più eseguito dall'applicazione Web [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
 È possibile installare [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] e una versione precedente di SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) nello stesso computer. I file vengono installati in posizioni diverse, come illustrato in [Percorso file](#fileLocation).  
  
 **Per eseguire l'aggiornamento senza aggiornare il motore di database**  
  
1.  Installare [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] e qualsiasi altra funzionalità desiderata.  
  
    1.  Aprire l'Installazione guidata di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    2.  Fare clic su **Installazione** nel riquadro sinistro.  
  
    3.  Nel riquadro destro, fare clic su **Nuova installazione autonoma di SQL Server o aggiunta di funzionalità a un'installazione esistente**.  
  
    4.  Nella pagina **Selezione funzionalità**, selezionare **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** e qualsiasi altra funzionalità si voglia installare.  
  
    5.  Completare la procedura guidata.  
  
2.  Aggiornare lo schema del database MDS.  
  
    1.  Aprire la versione [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] di [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
        > [!IMPORTANT]  
        >  Per aggiornare lo schema del database MDS, è necessario avere effettuato l'accesso con l'account Administrator specificato quando è stato creato il database MDS. Nel database MDS, in mdm.tblUser, a questo utente è assegnato il valore **ID** **1**.  
  
    2.  Nel riquadro sinistro fare clic su **Configurazione database**.  
  
    3.  Nel riquadro destro fare clic su **Seleziona database** e specificare le informazioni per l'istanza del database di [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
    4.  Fare clic su **Aggiorna database** per avviare l'**Aggiornamento guidato database**. Per altre informazioni, vedere [Aggiornamento guidato database &#40;Gestione configurazione Master Data Services&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).  
  
3.  Creare un'applicazione Web.  
  
    1.  Aprire la versione [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] di [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
    2.  Nel riquadro sinistro fare clic su **Configurazione Web**.  
  
    3.  Nel riquadro destro, selezionare nell'elenco **Sito Web** una delle seguenti opzioni:  
  
        -   **Sito Web predefinito**, quindi scegliere **Crea applicazione**.  
  
        -   **Crea nuovo sito**. Quando si crea il sito Web, viene creata automaticamente una nuova applicazione Web.  
  
        > [!IMPORTANT]  
        >  L'applicazione Web MDS esistente di una versione precedente di SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) è disponibile per la selezione nella versione [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] di Gestione configurazione Master Data Services. Non è necessario selezionare l'applicazione Web esistente, è invece necessario creare un'applicazione Web [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] per MDS. In caso contrario, verrà visualizzato un errore quando si tenta di associare l'applicazione Web al database MDS aggiornato, indicante che non è possibile accedere alla pagina richiesta perché i dati di configurazione correlati per la pagina non sono validi.  
        >   
        >  Per usare lo stesso nome (alias) dell'applicazione Web ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) esistente per l'applicazione Web MDS, è necessario prima di tutto eliminare l'applicazione Web e il pool di applicazioni associato da IIS, quindi creare un'applicazione Web con lo stesso nome usando la versione [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] di Gestione configurazione Master Data Services. Per informazioni sulla rimozione di un'applicazione Web e di pool di applicazioni da IIS, vedere [Rimuovere un'applicazione (IIS)](http://go.microsoft.com/fwlink/?LinkId=323537) e [Rimuovere un pool di applicazioni (IIS)](http://go.microsoft.com/fwlink/?LinkId=323538).  
  
4.  Associare la nuova applicazione Web al database MDS aggiornato.  
  
    1.  Nella sezione **Associare un'applicazione a un database** fare clic su **Seleziona**.  
  
    2.  Selezionare il database MDS.  
  
    3.  Fare clic su **Applica**.  
  
##  <a name="engine"></a> Aggiornare con l'aggiornamento del motore di database  
 In questo scenario il motore di database e l'applicazione [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] vengono aggiornati da [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
 **Per eseguire l'aggiornamento aggiornando il motore di database**  
  
1.  **Solo per [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]**: aprire **Pannello di controllo** >  > Programmi e funzionalità** e disinstallare **Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
2.  Aggiornare il motore di database a [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Per altre informazioni, vedere [Scegliere un metodo di aggiornamento del motore di database](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md).  
  
3.  Completare tutti i passaggi in [Aggiornare senza aggiornamento del motore di database](#noengine).  
  
##  <a name="twocomputer"></a> Aggiornare in uno scenario con due computer  
 Questo scenario comporta l'aggiornamento di un sistema nel quale SQL Server viene installato in due computer: uno con [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] e l'altro con [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
 Se è installato [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], si continua a usare rispettivamente [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] per ospitare il database MDS in un computer. Tuttavia, è necessario aggiornare lo schema del database MDS e quindi utilizzare l'applicazione Web [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] per accedere al database MDS. L'accesso al database MDS non può essere più eseguito dall'applicazione Web [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
 **Per eseguire l'aggiornamento in uno scenario con computer**  
  
-   Completare tutti i passaggi in [Aggiornare senza aggiornamento del motore di database](#noengine).  
  
##  <a name="restore"></a> Aggiornare con il ripristino di un database da un backup  
 In questo scenario, [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] è installato insieme a [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] nello stesso computer o in due computer differenti. È stato eseguito il backup prima dell'aggiornamento di un database in una versione precedente a [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] e il database deve essere ripristinato.  
  
 **Per eseguire l'aggiornamento con il ripristino di un database da un backup**  
  
1.  Installare [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] e qualsiasi altra funzionalità desiderata.  
  
    1.  Aprire l'Installazione guidata di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    2.  Fare clic su **Installazione** nel riquadro sinistro.  
  
    3.  Nel riquadro destro, fare clic su **Nuova installazione autonoma di SQL Server o aggiunta di funzionalità a un'installazione esistente**.  
  
    4.  Nella pagina **Selezione funzionalità**, selezionare **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** e qualsiasi altra funzionalità si voglia installare.  
  
    5.  Completare la procedura guidata.  
  
2.  Ripristinare il database di cui è stato eseguito il backup.  
  
3.  Aggiornare lo schema del database MDS, creare un'applicazione Web e associare la nuova applicazione Web al database MDS aggiornato. Per le istruzioni, vedere i passaggi da 2 a 4 in [Aggiornare senza aggiornamento del motore di database](#noengine)  
  
## Risoluzione dei problemi  
 **Problema:** quando si apre l'applicazione Web [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)][!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], viene visualizzato un messaggio di errore indicante che la versione del client non è compatibile con quella del database.  
  
 **Soluzione:** questo problema si verifica quando un'applicazione Web Gestione dati master di [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] prova ad accedere a un database che è stato aggiornato a [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] Master Data Services. È necessario quindi utilizzare un'applicazione Web [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
 Questo problema si può verificare anche qualora non si arresti e riavvii il **pool di applicazioni MDS** in IIS in caso di aggiornamento dello schema del database MDS. Riavviare il **pool di applicazioni MDS** per correggere il problema.  
  
## Vedere anche  
 [Installazione di Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  