---
title: Installare R Server autonomo o Machine Learning Server autonomo | Documenti Microsoft
ms.custom: 
ms.date: 02/14/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 408e2503-5c7d-4ec4-9d3d-bba5a8c7661d
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 2ecb60bd02b3fc1ee7ac7101749fa7affc2523bd
ms.sourcegitcommit: 4edac878b4751efa57601fe263c6b787b391bc7c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="install-machine-learning-server-standalone-or-r-server-standalone"></a>Installare R Server (Standalone) o Machine Learning Server (Standalone)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Installazione di SQL Server include l'opzione per installare un server che esegue SQL Server di fuori di apprendimento. Questa opzione potrebbe essere utile se è necessario sviluppare soluzioni di apprendimento computer ad alte prestazioni che possono usare i contesti di calcolo remoto, o che possono essere distribuiti in più piattaforme, tra cui:
  
  + Un'istanza di SQL Server 2016 o 2017 di SQL Server in cui è abilitato l'apprendimento
  + Un'istanza di R Server o Server di Machine Learning in un cluster Hadoop o Spark
  + R Server o Server di Machine Learning in Linux

In questo articolo viene illustrato come utilizzare il programma di installazione di SQL Server per installare la versione autonoma di Machine Learning Server o Microsoft R Server. Se si dispone di un Enterprise Edition o Software Assurance, l'installazione del server di apprendimento autonomo è gratuita.

+ [Installare R Server](#bkmk_installRServer) -utilizza il programma di installazione di SQL Server 2016
+ [Installare Server di Machine Learning](#bkmk_installMLServer) -utilizza il programma di installazione di SQL Server 2017
+ [Aggiornare un'istanza esistente di Microsoft R Server](#bkmk_upgrade)
+ [Come decidere quali componenti installare](#bkmk_tips)

##  <a name="bkmk_installMLServer"></a> Installazione di Machine Learning Server (Standalone)

Questa funzionalità richiede una licenza Enterprise o equivalente per **SQL Server 2017**.

Se è installata una versione precedente di Microsoft R Server, si consiglia di disinstallarlo prima di tutto.

Se il computer non ha accesso a Internet, è necessario scaricare i programmi di installazione del componente in anticipo. Per ulteriori informazioni, vedere [l'installazione dei componenti di machine learning senza accesso a internet](./installing-ml-components-without-internet-access.md).

1. Eseguire l'installazione di SQL Server 2017.

2. Fare clic su di **installazione** scheda e selezionare **Machine Learning installazione nuovo Server (Standalone)**.
    
     ![Installazione autonoma di Server di Machine Learning](media/2017setup-installation-page-mlsvr.png "avviare l'installazione di Machine Learning Server autonomo")

3. Una volta completata la verifica delle regole, accettare i termini della licenza di SQL Server e selezionare una nuova installazione.

4. Nel **Selezione funzionalità** pagina, le seguenti opzioni dovrebbero essere già selezionate:

    - Microsoft Machine Learning Server (Standalone)

    - R e Python sono entrambe selezionate per impostazione predefinita. È possibile deselezionare entrambi i linguaggi, ma è consigliabile installare almeno uno dei linguaggi supportati.

     ![Installazione autonoma di Server di Machine Learning](media/2017setup-features-page-mlsvr-rpy.png "avviare l'installazione di Machine Learning Server autonomo")
    
    Tutte le altre opzioni devono essere ignorate. 
    
    > [!NOTE]
    > Evitare l'installazione di **Caratteristiche condivise di** se nel computer è già installato per analitica nel database di SQL Server servizi di Machine Learning. Crea raccolte duplicate.
    > 
    > Inoltre, mentre gli script R o Python in esecuzione in SQL Server vengono gestiti da SQL Server a come non in conflitto con la memoria utilizzata da altri servizi motore di database, server autonomo machine learning non ha tali vincoli e possono interferire con altre operazioni di database . Infine, accesso remoto tramite una sessione RDP, che viene spesso usata per rendere operativo, in genere è bloccato da amministratori di database.
    > 
    > Per questi motivi, in genere consigliabile installare Machine Learning Server (Standalone) in un computer diverso da servizi di SQL Server Machine Learning.

5.  Accettare le condizioni di licenza per il download e installazione di machine learning componenti. Se si installa entrambi i linguaggi, è necessario per Microsoft R e Python un contratto di licenza separato.
    
     ![Contratto di licenza di Python](media/2017setup-python-license.png "contratto di licenza di Python")
    
    Installazione di questi componenti e gli eventuali prerequisiti che necessari, potrebbe richiedere qualche istante. Quando il pulsante **Accetto** non è più disponibile, è possibile fare clic su **Avanti**.

6.  Nella pagina **Inizio installazione** verificare le opzioni selezionate e fare clic su **Installa**.

Per ulteriori informazioni sull'installazione automatica o non in linea, vedere [installare Microsoft R Server dalla riga di comando](../../advanced-analytics/r/install-microsoft-r-server-from-the-command-line.md).

##  <a name="bkmk_installRServer"></a> Installare Microsoft R Server (Standalone)

Questa funzionalità richiede una licenza Enterprise o equivalente per **SQL Server 2016**.

Se è stata installata qualsiasi versione precedente degli strumenti di Revolution Analitica o pacchetti, è necessario disinstallarle prima. Vedere [l'aggiornamento da una versione precedente di Microsoft R Server](#bkmk_Uninstall).

1. Eseguire l'installazione di SQL Server 2016. Si consiglia di installare Service Pack 1 o versione successivo.

2. Nel **installazione** scheda, fare clic su **R installazione nuovo Server (Standalone)**.
    
     ![Avviare l'installazione di R Server autonomo](media/2016-setup-installation-rsvr.png "avviare l'installazione di R Server autonomo")
    
3.  Nella pagina **Selezione funzionalità** dovrebbe essere già selezionata l'opzione seguente:
    
    **R Server (Standalone)**  
    
    ![Funzionalità selezioni per R Server autonomo](media/2016setup-rserver-features.png "funzionalità selezioni per R Server autonomo")
    
    Tutte le altre opzioni possono essere ignorate. 
    
    > [!NOTE]
    > Evitare l'installazione di **Caratteristiche condivise di** se si esegue il programma di installazione in un computer in cui R Services è già stato installato per analitica nel database di SQL Server. Crea raccolte duplicate.
    > 
    > Mentre gli script R in esecuzione in SQL Server vengono gestiti da SQL Server a come non in conflitto con la memoria utilizzata da altri servizi motore di database, Server R autonomo non presenta tali limiti e può interferire con altre operazioni di database.
    > 
    > In genere è consigliabile installare Machine Learning Server (Standalone) in un computer diverso da servizi di SQL Server Machine Learning.

4.  Accettare le condizioni di licenza per il download e l'installazione di Microsoft R Open. Quando il pulsante **Accetto** non è più disponibile, è possibile fare clic su **Avanti**.
    
    Installazione di questi componenti e gli eventuali prerequisiti che necessari, potrebbe richiedere qualche istante.
    
5.  Nella pagina **Inizio installazione** verificare le opzioni selezionate e fare clic su **Installa**.

## <a name="bkmk_upgrade"></a> Aggiornare un'istanza esistente di R Server

Se è installata una versione precedente di Microsoft R Server (Standalone), è possibile aggiornare l'istanza per utilizzare le versioni più recenti dei componenti R. L'aggiornamento modifica anche i criteri di supporto per usare i criteri del ciclo di vita Software moderni supporta. In questo modo l'istanza da aggiornare più frequentemente, in base a una pianificazione diversa rispetto a versioni di SQL Server.

1. Scaricare il programma di installazione basati su Windows separato dai percorsi elencati di seguito: 

    + [Installazione di Machine Learning Server per Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
    + [Installare R Server 9.1 per Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)

2. Eseguire il programma di installazione e seguire le istruzioni. Nella pagina in cui si seleziona le funzionalità da installare, selezionare ogni istanza del Server di R che si desidera aggiornare.

## <a name ="bkmk_tips"></a> Follow-up e suggerimenti per l'installazione

In questa sezione fornisce informazioni aggiuntive correlate al programma di installazione.

### <a name="which-version-should-i-install"></a>La versione è necessario installare?

+ **Microsoft R Server** prima di tutto è stato offerto come parte di SQL Server 2016 e supporta il linguaggio R. L'ultima versione di Microsoft R Server è stato 9.0.1.

+ **Server di Microsoft Machine Learning** è la versione più recente, che è stata rilasciata con SQL Server 2017 e molti aggiornamenti delle funzionalità, incluso il supporto per Python. Aggiornamento cumulativo 1 per SQL Server 2017 è stata rilasciata, che include la versione 9.2.1.24 di Machine Learning Server. Questo aggiornamento è consigliabile se si desidera che le API più recente di Python.

+ **L'aggiornamento sul posto**: il programma di installazione richiede una licenza di SQL Server e gli aggiornamenti sono in genere allineati con i rilasci di SQL Server. Questo garantisce la sincronizzazione degli strumenti di sviluppo con la versione in esecuzione nel contesto di calcolo di SQL Server. Tuttavia, è possibile utilizzare il programma di installazione separato basati su Windows per ottenere gli aggiornamenti più frequenti, in base ai criteri di supporto di ciclo di vita di Software più recenti. È anche possibile utilizzare il programma di installazione per aggiornare un'istanza di SQL Server 2016 o SQL Server 2017.

### <a name="default-installation-folders"></a>Cartelle di installazione predefinito

Quando si installa R Server o Machine Learning Server tramite l'installazione di SQL Server, le librerie di R vengono installate in una cartella associata alla versione di SQL Server utilizzato per l'installazione. In questa cartella, si trovano anche dati di esempio, alla documentazione per i pacchetti di base di R e documentazione di strumenti di R e runtime.

Tuttavia, se si installa tramite il programma di installazione di Windows separato o se esegue l'aggiornamento utilizzando il programma di installazione di Windows separato, le librerie di R vengono installate in una cartella diversa.

Solo per riferimento, se è stata installata un'istanza di SQL Server con R Services (In-Database) o i servizi di Machine Learning (In-Database), e tale istanza nello stesso computer, le librerie R e gli strumenti vengono installati per impostazione predefinita in una cartella diversa.

Nella tabella seguente sono elencati i percorsi per ogni installazione.

|Version| Metodo di installazione | Cartella predefinita|
|----|----|----|
|R Server (Standalone) |Installazione guidata di SQL Server 2016|`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|R Server (Standalone) |Programma di installazione di Windows autonomo|`C:\Program Files\Microsoft\R Server\R_SERVER`|
|Machine Learning Server (Standalone) |  Installazione guidata di SQL Server 2017, con l'opzione di linguaggio R |`C:\Program Files\Microsoft SQL Server\140\R_SERVER`|
|Machine Learning Server (Standalone) |  Installazione guidata di SQL Server 2017, con l'opzione di linguaggio Python |`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Machine Learning Server (Standalone) |  Programma di installazione di Windows autonomo |`C:\Program Files\Microsoft\R Server\R_SERVER`|
|R Services (In-Database) |Installazione guidata di SQL Server 2016|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|
|Machine Learning Services (In-Database) |Installazione guidata di SQL Server 2017, con l'opzione di linguaggio R|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  |
|Machine Learning Services (In-Database) |Installazione guidata di SQL Server 2017, con l'opzione di linguaggio Python| `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |
### <a name="development-tools"></a>Strumenti di sviluppo

Sviluppo IDE non è installato come parte del programma di installazione. Strumenti aggiuntivi non sono necessari, come tutti gli strumenti standard sono inclusi che sarebbero forniti con una distribuzione di R o Python.

È consigliabile provare la nuova versione di [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)]. Visual Studio supporta sia R e Python, nonché strumenti di sviluppo di database, la connettività con SQL Server e strumenti di Business Intelligence. Tuttavia, è possibile utilizzare qualsiasi ambiente di sviluppo preferito tra RStudio.

## <a name="troubleshooting"></a>Risoluzione dei problemi

In questa sezione sono elencati alcuni problemi comuni per tenere conto durante l'installazione di Server di Machine Learning o R Server.

### <a name="incompatible-version-of-r-client-and-r-server"></a>Le versioni di R Client e R Server non sono compatibili

Se si installa Microsoft R Client e utilizzarlo per l'esecuzione di R in un contesto di calcolo di SQL Server remoto, è possibile che venga visualizzato un errore simile al seguente:

*Si esegue la versione 9.0.0 del client di Microsoft R nel computer, non è compatibile con la versione 8.0.3 Microsoft R Server. Download and install a compatible version.* (Sul computer è in esecuzione la versione 9.0.0 di Microsoft R, che non è compatibile con Microsoft R Server versione 8.0.3. Scaricare e installare una versione compatibile.)

In SQL Server 2016, è necessario che la versione di R che era in esecuzione in SQL Server R Services corrispondere esattamente come le librerie client di Microsoft R. Tale requisito è stato rimosso nelle versioni successive. Tuttavia, si consiglia di sempre le versioni più recenti di machine learning i componenti di ottenere e installare tutti i service pack. 

Se si dispone di una versione precedente di Microsoft R Server ed è necessario garantire la compatibilità con Client di Microsoft R 9.0.0, installare gli aggiornamenti descritti in questo [articolo del supporto tecnico](https://support.microsoft.com/kb/3210262).

### <a name="installing-microsoft-r-server-on-an-instance-of-sql-server-installed-on-windows-core"></a>Installazione di Microsoft R Server in un'istanza di SQL Server installata in Windows Core

Nella versione RTM di SQL Server 2016, si è verificato un problema noto durante l'aggiunta di Microsoft R Server per un'istanza in versione di Windows Server Core. Questo problema è stato risolto.

Se si verifica questo problema, è possibile applicare la correzione descritta nel [KB3164398](https://support.microsoft.com/kb/3164398) per aggiungere la funzionalità di R per l'istanza esistente in Windows Server Core.   Per altre informazioni, vedere [Impossibile installare Microsoft R Server (autonomo) in un sistema operativo Windows Server Core](https://support.microsoft.com/kb/3168691).

###  <a name="bkmk_Uninstall"></a> L'aggiornamento da una versione precedente di Microsoft R Server

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

[Machine Learning Server (Standalone)](../../advanced-analytics/r/r-server-standalone.md)
