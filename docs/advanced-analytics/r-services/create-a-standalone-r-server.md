---
title: "Creare un server R autonomo | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 408e2503-5c7d-4ec4-9d3d-bba5a8c7661d
caps.latest.revision: 35
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 27
---
# Creare un server R autonomo
  Il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] include la possibilità di installare **Microsoft R Server (Standalone)**. Questa opzione consente di sviluppare soluzioni R ad alte prestazioni in Windows mentre si è connessi all'origine dati o al database di propria scelta. Microsoft R Server è disponibile solo nella Enterprise Edition.  
  
 Quando si installa Microsoft R Server, si ottengono gli stessi strumenti di connettività e pacchetti R avanzati che sono disponibili in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], ma non è necessaria un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e gli script R vengono eseguiti sul computer autonomo, non nel database.  
  
> [!NOTE]  
>  Microsoft R Server è ora disponibile anche tramite un'installazione semplificata che registra l'istanza in base ai [criteri relativi al ciclo di vita moderni](https://support.microsoft.com/help/447912). Con questa offerta di supporto si ha la sicurezza di usare sempre la versione più recente di R. Per altre informazioni sull'uso dell'installazione semplificata, vedere [Run Microsoft R Server for Windows](https://msdnstage.redmond.corp.microsoft.com/microsoft-r/rserver-install-windows?branch=r-server-nov16-dev) (Eseguire Microsoft R Server per Windows).
>  
> Se si installa Microsoft R Server tramite l'installazione semplificata, è anche possibile convertire qualsiasi istanza specificata di R Services in modo da usare i nuovi criteri di supporto e ottenere aggiornamenti più frequenti dei componenti R. Per altre informazioni, vedere [Use sqlBindR.exe to upgrade an instance of R Services](http://www.bing.com) (Usare sqlBindR.exe per aggiornare un'istanza di R Services).   
  
##  <a name="a-namebkmkinstallrservicesindatabasea-install-microsoft-r-server-standalone"></a><a name="bkmk_installRServicesInDatabase"></a> Installare Microsoft R Server (Standalone)  
  
1.  Se si è installata una versione precedente di Microsoft R Server, è necessario prima disinstallarla.  Vedere [Aggiornamento da una versione precedente di Microsoft R Server](#bkmk_Uninstall). 

2. Eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  Nella scheda **Installazione** fare clic su **Nuova installazione di R Server (Standalone)** .  
  
     ![Setup option for R Server Standalone](../../advanced-analytics/r-services/media/rsql-rstandalonesetup.png "Setup option for R Server Standalone")  
  
3.  Nella pagina **Selezione funzionalità** dovrebbe essere già selezionata l'opzione seguente:  
  
    -   **R Server (Standalone)**  
  
         Questa opzione installa le funzionalità condivise, tra cui i pacchetti di base e gli strumenti R open source e gli strumenti di connettività e i pacchetti R avanzati forniti da Microsoft R.  
  
     Tutte le altre opzioni possono essere ignorate.  
  
4.  Accettare le condizioni di licenza per il download e l'installazione di Microsoft R Open. Quando il pulsante **Accetto** non è più disponibile, è possibile fare clic su **Avanti**. L'installazione di questi componenti (e degli eventuali prerequisiti) potrebbe richiedere alcuni minuti.   
  
5.  Nella pagina **Inizio installazione** verificare le opzioni selezionate e fare clic su **Installa**.  
  
> [!TIP]
> Per altre informazioni sull'installazione automatica o offline, vedere [Installare Microsoft R Server dalla riga di comando](../../advanced-analytics/r-services/install-microsoft-r-server-from-the-command-line.md).

  
## <a name="what-is-installed-and-where-to-find-r-packages"></a>Che cosa viene installato e dove trovare i pacchetti R  
 Microsoft R Server include i pacchetti R di base e un set di pacchetti R avanzati che supportano l'elaborazione parallela, prestazioni migliorate e la connettività a origini dati, come [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e Hadoop.  
  
-   **Pacchetti R**  
  
     Le librerie R vengono installate insieme agli altri strumenti e utilità installati con Microsoft SQL Server 2016. Esempio:  
  
     `C:\Program Files\Microsoft SQL Server\130\R_SERVER`  
  
     Inoltre, in questa cartella è possibile trovare la documentazione per i pacchetti R di base, dati di esempio e la documentazione relativa al runtime e agli strumenti R.  
  
    > [!NOTE]  
    >  Se si è installata un'istanza di SQL Server con R Services (In-Database) nello stesso computer, gli strumenti e le librerie di R vengono installati in una cartella diversa: `C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES`  
    >   
    >  Non usare le utilità o i pacchetti R associati all'istanza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Usare sempre gli strumenti e i pacchetti R nella cartella R_SERVER.  
  
-   **Strumenti R**  
  
     L'IDE di sviluppo R non viene installato durante la procedura di installazione. È possibile installare RStudio, [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] o qualsiasi altro ambiente di sviluppo preferito.  
  
     Tuttavia, non sono necessari altri strumenti. Tutti gli strumenti R di base standard sono inclusi in `C:\Program Files\Microsoft SQL Server\130\R_SERVER\bin`.  
  
     Per altre informazioni, vedere [Installare o configurare gli strumenti R](../../advanced-analytics/r-services/setup-or-configure-r-tools.md).  


 
## <a name="troubleshooting"></a>Risoluzione dei problemi  

### <a name="incompatible-version-of-r-client-and-r-server"></a>Le versioni di R Client e R Server non sono compatibili

Se si installa la versione più recente di Microsoft R Client e si usa tale versione per eseguire R su SQL Server tramite un contesto di calcolo remoto, è possibile che venga visualizzato l'errore seguente:

*You are running version 9.0.0 of Microsoft R client on your computer, which is incompatible with the Microsoft R server version 8.0.3. Download and install a compatible version.* (Sul computer è in esecuzione la versione 9.0.0 di Microsoft R, che non è compatibile con Microsoft R Server versione 8.0.3. Scaricare e installare una versione compatibile.)

In genere, la versione di R installata con SQL Server R Services viene aggiornata al momento della pubblicazione di nuove versioni del servizio. Per assicurarsi di avere sempre le versioni più aggiornate dei componenti R, installare tutti i Service Pack. Per la compatibilità con Microsoft R Client 9.0.0, è necessario installare gli aggiornamenti descritti in questo [articolo del supporto tecnico](https://support.microsoft.com/kb/3210262). 


### <a name="installing-microsoft-r-server-on-an-instance-of-sql-server-installed-on-windows-core"></a>Installazione di Microsoft R Server in un'istanza di SQL Server installata in Windows Core
Nella versione finale di SQL Server 2016 è stato riscontrato un problema durante l'aggiunta di Microsoft R Server a un'istanza nell'edizione di Windows Server Core. Questo problema è stato risolto. 

Se si riscontra questo problema, è possibile applicare la correzione descritta nell'articolo [KB3164398](https://support.microsoft.com/kb/3164398) per aggiungere la funzionalità R all'istanza esistente in Windows Server Core.   Per altre informazioni, vedere [Impossibile installare Microsoft R Server (autonomo) in un sistema operativo Windows Server Core](https://support.microsoft.com/kb/3168691).


###  <a name="a-namebkmkuninstalla-upgrading-from-an-older-version-of-microsoft-r-server"></a><a name="bkmk_Uninstall"></a> Aggiornamento da una versione precedente di Microsoft R Server  
 Se è installata una versione non definitiva di Microsoft R Server, è necessario disinstallarla prima dell'aggiornamento a una versione più recente.  
  
**Per disinstallare R Server (Standalone)**  
  
1.  Nel **Pannello di controllo** fare clic su **Installazione applicazioni** e selezionare `Microsoft SQL Server 2016 <version number>`.  
  
2.  Nella finestra di dialogo con le opzioni per **aggiungere**, **ripristinare** o **rimuovere** i componenti selezionare **Rimuovi**.  
  
3.  Nella pagina **Seleziona funzionalità**, in **Funzionalità condivise**, selezionare **R Server (Standalone)**. Fare clic su **Avanti** e quindi su **Fine** per disinstallare solo i componenti selezionati.  
   
### <a name="installation-fails-with-error-only-one-revolution-enterprise-product-can-be-installed-at-a-time"></a>L'installazione non riesce con l'errore "Only one Revolution Enterprise product can be installed at a time." (È possibile installare un solo prodotto Revolution Enterprise alla volta.)  
Questo errore può verificarsi se si dispone di un'installazione precedente dei prodotti Revolution Analytics o di una versione non definitiva di SQL Server R Services. Prima di poter installare una versione più recente di Microsoft R Server, è necessario disinstallare le versioni precedenti. L'installazione side-by-side con altre versioni degli strumenti Revolution Enterprise non è supportata.  

Tuttavia, le installazioni side-by-side sono supportate quando si usa R Server (Standalone) con [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] e 
  
### <a name="unable-to-uninstall-older-components"></a>Non è possibile disinstallare i componenti precedenti   
  
Se si riscontrano problemi durante la rimozione di una versione precedente, può essere necessario modificare il Registro di sistema per rimuovere le chiavi correlate.  

> [!IMPORTANT]
> Questo problema riguarda solo i casi in cui è installata una versione non definitiva di Microsoft R Server o una versione CTP di SQL Server 2016 R Services.
  
1. Aprire il Registro di sistema di Windows e individuare questa chiave: `HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall`.  
2. Eliminare una qualsiasi delle voci seguenti, se presente e se la chiave contiene solo il valore `sEstimatedSize2`:  
  
    -   E0B2C29E-B8FC-490B-A043-2CAE75634972        (per 8.0.2)  
  
    -   46695879-954E-4072-9D32-1CC84D4158F4        (per 8.0.1)  
  
    -   2DF16DF8-A2DB-4EC6-808B-CB5A302DA91B        (per 8.0.0)  
  
    -   5A2A1571-B8CD-4AAF-9303-8DF463DABE5A        (per 7.5.0)  
  
## <a name="see-also"></a>Vedere anche  
 [Microsoft R Server](../../advanced-analytics/r-services/r-server-standalone.md)  
  
  