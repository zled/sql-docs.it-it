---
title: Creare un server R autonomo | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 408e2503-5c7d-4ec4-9d3d-bba5a8c7661d
caps.latest.revision: 35
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4f39a03ecf7b74e0e1305d692a71c28609c80bf0
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-a-standalone-r-server"></a>Creare un server R autonomo

Installazione di SQL Server include l'opzione per installare un server che esegue SQL Server di fuori di apprendimento. 

Questa opzione potrebbe essere utile se è necessario sviluppare soluzioni R ad alte prestazioni in Windows e quindi condividere le soluzioni con altre piattaforme. Per configurare un ambiente per la creazione di soluzioni per l'esecuzione su questi supportata contesti di calcolo remoto, è possibile utilizzare anche l'opzione server:
  
  + Un'istanza di SQL Server che esegue R Services
  + Un'istanza di R Server che usa un cluster Hadoop o Spark
  + Analisi nel database di teradati
  + R Server in esecuzione in Linux 

In questo argomento vengono descritti i passaggi di installazione nel programma di installazione di SQL Server per Microsoft R Server e Server di Microsoft Machine Learning.

## <a name="which-should-i-install"></a>Che è necessario installare?

**Microsoft R Server** prima di tutto è stato offerto come parte di SQL Server 2016 e supporta il linguaggio R. L'ultima versione di Microsoft R Server è stato 9.0.1.
In SQL Server 2017, R Server è stato rinominato **Microsoft Machine Learning Server**, con aggiunto il supporto per Python. La versione più recente del Server di Microsoft Machine Learning è 9.1.0.

Microsoft R Server sia Server di Microsoft Machine Learning richiedono Enterprise Edition.

+ [Installare Microsoft R Server (Standalone) utilizzando il programma di installazione di SQL Server](#bkmk_installRServer)
+ [Installare Microsoft Machine Learning Server (Standalone) utilizzando il programma di installazione di SQL Server](#bkmk_installRServer) 

  La configurazione richiede una licenza di SQL Server e gli aggiornamenti sono in genere allineati alla frequenza di rilascio di SQL Server. Questo garantisce la sincronizzazione degli strumenti di sviluppo con la versione in esecuzione nel contesto di calcolo di SQL Server.

+ [Installare R Server per Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)

  Con questa opzione, R Server viene installato usando i criteri di supporto del ciclo di vita moderna. È anche possibile eseguire il programma di installazione al termine dell'installazione per aggiornare un'istanza di SQL Server 2016. Attualmente, si _Impossibile_ Python supporta l'utilizzo di questa opzione di installazione. Per ottenere Python, è necessario installare Machine Learning Server tramite l'installazione di SQL Server 2017.

##  <a name="bkmk_installRServer"></a>Come installare Microsoft Machine Learning Server (Standalone)
  
1. Se è installata una versione precedente di Microsoft R Server, si consiglia di disinstallarlo prima di tutto.

2. Eseguire l'installazione di SQL Server 2017.
  
3. Fare clic su di **installazione** scheda e selezionare **Machine Learning installazione nuovo Server (Standalone)**.

4. Una volta completata la verifica delle regole, accettare i termini della licenza di SQL Server e selezionare una nuova installazione.

5. Nel **Selezione funzionalità** pagina, le seguenti opzioni dovrebbero essere già selezionate:
    
    - Microsoft Machine Learning Server (Standalone)
    
    - R e Python sono entrambe selezionate per impostazione predefinita.
    
    Tutte le altre opzioni devono essere ignorate.

6.  Accettare le condizioni di licenza per il download e installazione di machine learning componenti. Un contratto di licenza separato è necessario per Microsoft R Open e Python. 
    
    Quando il pulsante **Accetto** non è più disponibile, è possibile fare clic su **Avanti**. 
    
    L'installazione di questi componenti (e degli eventuali prerequisiti) potrebbe richiedere alcuni minuti. 
    
    Se il computer non ha accesso a Internet, è necessario scaricare i programmi di installazione del componente in anticipo. Per ulteriori informazioni, vedere [componenti di installazione di ML senza accesso a Internet](./installing-ml-components-without-internet-access.md). 
    
7.  Nella pagina **Inizio installazione** verificare le opzioni selezionate e fare clic su **Installa**.


Per altre informazioni sull'installazione automatica o offline, vedere [Installare Microsoft R Server dalla riga di comando](../../advanced-analytics/r-services/install-microsoft-r-server-from-the-command-line.md).

###  <a name="bkmk_installRServer"></a> Installare Microsoft R Server (Standalone)  

1. Se è stato installato una versione precedente di Microsoft R Server o qualsiasi versione degli strumenti di Revolution Analitica, è necessario disinstallare prima.  Vedere [Aggiornamento da una versione precedente di Microsoft R Server](#bkmk_Uninstall).

2. Eseguire l'installazione di SQL Server 2016. Si consiglia di installare Service Pack 1 o versione successivo.

3. Nella scheda **Installazione** fare clic su **Nuova installazione di R Server (Standalone)** .
    
     ![Opzione di configurazione per R Server Standalone](media/rsql-rstandalonesetup.png "Opzione di configurazione per R Server Standalone")
    
4.  Nella pagina **Selezione funzionalità** dovrebbe essere già selezionata l'opzione seguente:
    
    **R Server (Standalone)**  
    
    Tutte le altre opzioni possono essere ignorate. Non installare il motore di database di SQL Server o SQL Server R Services.
    
5.  Accettare le condizioni di licenza per il download e l'installazione di Microsoft R Open. Quando il pulsante **Accetto** non è più disponibile, è possibile fare clic su **Avanti**. 
    
    L'installazione di questi componenti (e degli eventuali prerequisiti) potrebbe richiedere alcuni minuti.
    
6.  Nella pagina **Inizio installazione** verificare le opzioni selezionate e fare clic su **Installa**.  


### <a name="upgrade-an-existing-r-server-to-901"></a>L'aggiornamento di un Server esistente di R a 9.0.1

Se è stata installata una versione precedente di Microsoft R Server (Standalone) è possibile aggiornare l'istanza per utilizzare le versioni più recenti dei componenti R. L'aggiornamento viene modificato anche il server dei criteri di supporto del ciclo di vita moderna. In questo modo l'istanza da aggiornare più frequentemente, in base a una pianificazione diversa rispetto a versioni di SQL Server.

1. Installare Microsoft R Server (Standalone), se non è già installato.

2. Download l'installazione basata su Windows separato dai percorsi elencato di seguito: [eseguire Microsoft R Server per Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows#howtoinstall).

3. Eseguire il programma di installazione e seguire [queste istruzioni](https://msdn.microsoft.com/microsoft-r/rserver-install-windows#download-r-server-installer).


### <a name="change-in-default-folder-for-r-packages"></a>Cartella predefinita di modifica per i pacchetti R

Quando si installa tramite l'installazione di SQL Server, le librerie di R vengono installate in una cartella associata alla versione di SQL Server utilizzato per l'installazione. In questa cartella si troveranno anche dati di esempio, la documentazione per i pacchetti R di base, e la documentazione relativa al runtime e agli strumenti R.

**R Server (Standalone) con configurazione tramite SQL Server 2016**

`C:\Program Files\Microsoft SQL Server\130\R_SERVER`

**R Server (Standalone) con configurazione tramite SQL Server 2017**

`C:\Program Files\Microsoft SQL Server\140\R_SERVER`

**Installazione mediante il programma di installazione autonomo di Windows**

Tuttavia, se si installa tramite il programma di installazione di Windows separato o se esegue l'aggiornamento utilizzando il programma di installazione di Windows separato, librerie R vengono spostate nella cartella R Server seguenti:

`C:\Program Files\Microsoft\R Server\R_SERVER`
      
**Nel database di servizi di installazione di R Services o di Machine LEarning**

Se è stata installata un'istanza di SQL Server con R Services (In-Database) o i servizi di Machine Learning (In-Database) e tale istanza è sullo stesso computer, le librerie R e gli strumenti vengono installati per impostazione predefinita in una cartella diversa:

`C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES`

Non chiamare direttamente le utilità o i pacchetti R associati all'istanza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Se R Server R Services vengono installati sia nello stesso computer, quando è necessario eseguire RGui o altri strumenti, è possibile utilizzare gli strumenti di R e i pacchetti installati nella cartella R_SERVER.


### <a name="development-tools"></a>Strumenti di sviluppo

Sviluppo IDE non è installato come parte del programma di installazione. Strumenti aggiuntivi non sono necessari, come tutti gli strumenti standard sono inclusi che sarebbero forniti con una distribuzione di R o Python.

È consigliabile provare la nuova versione di [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)], come Visual Studio supporta gli strumenti di R e Python, nonché SQL Server e Business Intelligence. Tuttavia, è possibile utilizzare qualsiasi ambiente di sviluppo preferito tra RStudio.

## <a name="troubleshooting"></a>Risoluzione dei problemi  

### <a name="incompatible-version-of-r-client-and-r-server"></a>Le versioni di R Client e R Server non sono compatibili

Se si installa la versione più recente di Microsoft R Client e si usa tale versione per eseguire R su SQL Server tramite un contesto di calcolo remoto, è possibile che venga visualizzato l'errore seguente:

*Si esegue la versione 9.0.0 del client di Microsoft R nel computer, non è compatibile con la versione del server 8.0.3 di Microsoft R. Download and install a compatible version.* (Sul computer è in esecuzione la versione 9.0.0 di Microsoft R, che non è compatibile con Microsoft R Server versione 8.0.3. Scaricare e installare una versione compatibile.)

In genere, la versione di R installata con SQL Server R Services viene aggiornata al momento della pubblicazione di nuove versioni del servizio. Per assicurarsi di avere sempre le versioni più aggiornate dei componenti R, installare tutti i Service Pack. Per la compatibilità con Microsoft R Client 9.0.0, è necessario installare gli aggiornamenti descritti in questo [articolo del supporto tecnico](https://support.microsoft.com/kb/3210262). 


### <a name="installing-microsoft-r-server-on-an-instance-of-sql-server-installed-on-windows-core"></a>Installazione di Microsoft R Server in un'istanza di SQL Server installata in Windows Core

Nella versione RTM di SQL Server 2016, si è verificato un problema noto durante l'aggiunta di Microsoft R Server per un'istanza in versione di Windows Server Core. Questo problema è stato risolto.

Se si riscontra questo problema, è possibile applicare la correzione descritta nell'articolo [KB3164398](https://support.microsoft.com/kb/3164398) per aggiungere la funzionalità R all'istanza esistente in Windows Server Core.   Per altre informazioni, vedere [Impossibile installare Microsoft R Server (autonomo) in un sistema operativo Windows Server Core](https://support.microsoft.com/kb/3168691).


###  <a name="bkmk_Uninstall"></a> Aggiornamento da una versione precedente di Microsoft R Server

Se è installata una versione non definitiva di Microsoft R Server, è necessario disinstallarla prima dell'aggiornamento a una versione più recente.

**Per disinstallare R Server (Standalone)**

1.  Nel **Pannello di controllo**fare clic su **Installazione applicazioni**e selezionare `Microsoft SQL Server 2016 <version number>`.  
  
2.  Nella finestra di dialogo con le opzioni per **aggiungere**, **ripristinare**o **rimuovere** i componenti selezionare **Rimuovi**.  
  
3.  Nella pagina **Seleziona funzionalità** , in **Funzionalità condivise**, selezionare **R Server (Standalone)**. Fare clic su **Avanti**e quindi su **Fine** per disinstallare solo i componenti selezionati.  
   
### <a name="installation-fails-with-error-only-one-revolution-enterprise-product-can-be-installed-at-a-time"></a>L'installazione non riesce con l'errore "Only one Revolution Enterprise product can be installed at a time." (È possibile installare un solo prodotto Revolution Enterprise alla volta.)

Questo errore può verificarsi se si dispone di un'installazione precedente dei prodotti Revolution Analytics o di una versione non definitiva di SQL Server R Services. Prima di poter installare una versione più recente di Microsoft R Server, è necessario disinstallare le versioni precedenti. L'installazione side-by-side con altre versioni degli strumenti Revolution Enterprise non è supportata.

Tuttavia, le installazioni side-by-side sono supportate quando si usa R Server (Standalone) con [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] o SQL Server 2016.

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


