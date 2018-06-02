---
title: Installazione di SQL Server 2017 Machine Learning Server (Standalone) | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: cb906a8a05221204ec10310d652f6891861d35e2
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34708269"
---
# <a name="install-sql-server-2017-machine-learning-server-standalone-on-windows"></a>Installare SQL Server 2017 apprendimento Server (Standalone) in Windows
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Installazione di SQL Server include l'opzione per installare un server che esegue SQL Server di fuori di apprendimento. Questa opzione potrebbe essere utile se è necessario sviluppare ad alte prestazioni machine learning soluzioni utilizzano remoto da contesti di calcolo, passare in modo intercambiabile tra il server locale e un Server di apprendimento remoto computer in un cluster Spark o in un altro Server SQL istanza.
  
In questo articolo viene descritto come utilizzare il programma di installazione di SQL Server per installare la versione autonoma di **Server di SQL Server 2017 Machine Learning**. 

## <a name="bkmk_prereqs"> </a> Elenco di controllo pre-installazione

SQL Server 2017 è obbligatorio. Se si dispone di SQL Server 2016, installare [SQL Server 2016 R Server (Standalone)](sql-r-standalone-windows-install.md) invece.

Se è stata installata una versione precedente, ad esempio SQL Server 2016 R Server (Standalone) o Microsoft R Server, disinstallare la versione esistente prima di continuare.

## <a name="get-the-installation-media"></a>Ottenere il supporto di installazione

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

## <a name="run-setup"></a>Esecuzione del programma di installazione

Per le installazioni locali è necessario eseguire il programma di installazione come amministratore. Se si installa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio con autorizzazioni di lettura ed esecuzione relative a tale condivisione.

1. Avviare Installazione guidata di SQL Server 2017.

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

### <a name="default-installation-folders"></a>Cartelle di installazione predefinito

Quando si installa R Server o Machine Learning Server tramite l'installazione di SQL Server, le librerie di R vengono installate in una cartella associata alla versione di SQL Server utilizzato per l'installazione. In questa cartella, si trovano anche dati di esempio, alla documentazione per i pacchetti di base di R e documentazione di strumenti di R e runtime.

Tuttavia, se si installa tramite il programma di installazione di Windows separato o se esegue l'aggiornamento utilizzando il programma di installazione di Windows separato, le librerie di R vengono installate in una cartella diversa.

Solo per riferimento, se è stata installata un'istanza di SQL Server con R Services (In-Database) o i servizi di Machine Learning (In-Database), e tale istanza nello stesso computer, le librerie R e gli strumenti vengono installati per impostazione predefinita in una cartella diversa.

Nella tabella seguente sono elencati i percorsi per ogni installazione.

|Versione| Metodo di installazione | Cartella predefinita|
|----|----|----|
|SQL Server 2017 Machine Learning Server (Standalone) |  Installazione guidata di SQL Server 2017 |`C:\Program Files\Microsoft SQL Server\140\R_SERVER` <br/>`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Microsoft Machine Learning Server (Standalone) |  Programma di installazione di Windows autonomo |`C:\Program Files\Microsoft\ML Server\R_SERVER`<br/>`C:\Program Files\Microsoft\ML Server\PYTHON_SERVER`|
|SQL Server 2017 Machine Learning Services (In-Database) |Installazione guidata di SQL Server 2017, con l'opzione di linguaggio R|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  <br/>`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |
|R Server (Standalone) di SQL Server 2016 |  Installazione guidata di SQL Server 2016 |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2016 R Services (In-Database) |Installazione guidata di SQL Server 2016|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|

## <a name="development-tools"></a>Strumenti di sviluppo

Sviluppo IDE non è installato come parte del programma di installazione. Strumenti aggiuntivi non sono necessari, come tutti gli strumenti standard sono inclusi che sarebbero forniti con una distribuzione di R o Python.

È consigliabile provare la nuova versione di [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] oppure [Python per Visual Studio](https://docs.microsoft.com/visualstudio/python/installing-python-support-in-visual-studio). Visual Studio supporta sia R e Python, nonché strumenti di sviluppo di database, la connettività con SQL Server e strumenti di Business Intelligence. Tuttavia, è possibile utilizzare qualsiasi ambiente di sviluppo preferito tra RStudio.

## <a name="get-help"></a>Supporto

Assistenza sull'installazione o aggiornamento? Per le risposte alle domande più comuni e i problemi noti, vedere l'articolo seguente:

* [Aggiornamento e l'installazione domande frequenti - servizi di Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Per controllare lo stato di installazione dell'istanza e risolvere i problemi comuni, provare a questi report personalizzati.

* [Report personalizzati per SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Passaggi successivi

Gli sviluppatori R possono iniziare a usare alcuni semplici esempi e apprendere le nozioni di base del funzionamento di R con SQL Server. Per il passaggio successivo, vedere i collegamenti seguenti:

+ [Esercitazione: Esecuzione di R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Esercitazione: In-database analitica per gli sviluppatori R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Gli sviluppatori di Python possono imparare a usare Python con SQL Server seguendo queste esercitazioni:

+ [Esercitazione: Esecuzione di Python in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Esercitazione: In-database analitica per sviluppatori Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Per visualizzare esempi di machine learning basato su scenari reali, vedere [Machine learning esercitazioni](../tutorials/machine-learning-services-tutorials.md).
