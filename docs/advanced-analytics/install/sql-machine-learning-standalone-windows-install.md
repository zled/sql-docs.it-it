---
title: Installare R Server o Machine Learning Server (Standalone) utilizzando il programma di installazione di SQL Server | Microsoft Docs
description: Configurare un server di apprendimento automatico non dipendenti dall'istanza autonoma per lo sviluppo di R e Python con RevoScaleR, revoscalepy, MicrosoftML e altri pacchetti.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/28/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 7cf5cf2d78900c5bbd7607666afecc64aa98267f
ms.sourcegitcommit: e4e9f02b5c14f3bb66e19dec98f38c012275b92c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2018
ms.locfileid: "43118549"
---
# <a name="install-machine-learning-server-standalone-or-r-server-standalone-using-sql-server-setup"></a>Installare R Server (Standalone) con il programma di installazione di SQL Server o Machine Learning Server (Standalone)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Installazione di SQL Server include un **funzionalità condivisa** opzione per l'installazione di un non specifici dell'istanza, server di formazione machine autonomo eseguito all'esterno di SQL Server. In SQL Server 2016, questa funzionalità è detta **R Server (Standalone)**. In SQL Server 2017, bensì **Machine Learning Server (Standalone)** e include R e Python. 

Un server autonomo come installato dal programma di installazione di SQL Server è funzionalmente equivalente alle versioni non SQL personalizzata di [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), lo stesso supporto di casi d'uso e scenari, tra cui l'esecuzione remota, servizi web e l'operazionalizzazione e la raccolta completa di funzioni RevoScaleR e revoscalepy.

Come server indipendenti disaccoppiati da SQL Server, viene configurato l'ambiente R e Python, protetto e a cui si accede usando il sistema operativo sottostante e gli strumenti forniti nel server autonomo, non SQL Server.

A complemento di SQL Server, un server autonomo è utile se è necessario sviluppare ad alte prestazioni machine learning soluzioni che possono usare remote contesti di calcolo, il passaggio in modo intercambiabile tra il server locale e remoto Machine Learning Server in Spark cluster o in un altro Server SQL dell'istanza.
  

## <a name="bkmk_prereqs"> </a> Elenco di controllo pre-installazione

Se è installata una versione precedente, ad esempio SQL Server 2016 R Server (Standalone) o Microsoft R Server, disinstallare l'installazione esistente prima di continuare.

Come regola generale, è consigliabile che si considera server autonomo e motore specifici dell'istanza installazioni del database come reciprocamente esclusive per evitare conflitti di risorse, ma se si dispone di risorse sufficienti, non vi è alcun divieto di installazione di entrambe le di stesso computer fisico.

Può avere solo un server autonomo nel computer: SQL Server 2017 Machine Learning Server o SQL Server 2016 R Server (Standalone). Prima di installare una versione diversa, è necessario disinstallare manualmente una versione.

::: moniker range="=sql-server-2016"
 ###  <a name="bkmk_ga_instalpatch"></a> Requisito di installazione patch 

Per SQL Server 2016 solo: Microsoft ha identificato un problema con la versione specifica di file binari di Microsoft VC + + 2013 Runtime installati come prerequisito da SQL Server. Se l'aggiornamento dei file binari di VC++ Runtime non viene installato, potrebbero verificarsi problemi di stabilità di SQL Server in determinati scenari. Prima di installare SQL Server, seguire le istruzioni in [Note sulla versione di SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) per vedere se il computer richiede una patch per i file binari di VC++ Runtime.  
::: moniker-end

## <a name="get-the-installation-media"></a>Ottenere il supporto di installazione

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="run-setup"></a>Esecuzione del programma di installazione

Per le installazioni locali è necessario eseguire il programma di installazione come amministratore. Se si installa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio con autorizzazioni di lettura ed esecuzione relative a tale condivisione.

1. Avviare l'installazione guidata.

2. Scegliere il **installazione** scheda e selezionare **installazione nuova Machine Learning Server (Standalone)**.
    
     ![Installazione di Machine Learning Server (Standalone)](media/2017setup-installation-page-mlsvr.png "avviare l'installazione di Machine Learning Server (Standalone)")

3. Al termine del controllo delle regole, accettare le condizioni di licenza di SQL Server e selezionare una nuova installazione.

4. Nel **Selezione funzionalità** pagina, le seguenti opzioni dovrebbero essere già selezionate:

    - Microsoft Machine Learning Server (Standalone)

    - R e Python sono entrambe selezionate per impostazione predefinita. È possibile deselezionare entrambi i linguaggi, ma è consigliabile installare almeno uno dei linguaggi supportati.

     ![Installazione di Machine Learning Server (Standalone)](media/2017setup-features-page-mlsvr-rpy.png "avviare l'installazione di Machine Learning Server (Standalone)")
    
    Tutte le altre opzioni devono essere ignorate. 
    
    > [!NOTE]
    > Evitare di installare il **Caratteristiche condivise** se il computer dispone già di servizi di Machine Learning per analitica nel database di SQL Server installato. Ciò consente di creare librerie duplicate.
    > 
    > Inoltre, mentre gli script R o Python in esecuzione in SQL Server vengono gestiti da SQL Server a come non in conflitto con la memoria utilizzata da altri servizi del motore di database, server autonomo machine learning senza tali vincoli e può interferire con altre operazioni di database . Infine, accesso remoto tramite una sessione RDP, che viene spesso usata per l'operazionalizzazione, in genere è bloccata dagli amministratori di database.
    > 
    > Per questi motivi, è generalmente consigliabile installare Machine Learning Server (Standalone) in un computer separato da servizi di SQL Server Machine Learning.

5.  Accettare le condizioni di licenza per il download e installazione di distribuzioni di lingua di base. Quando il pulsante **Accetto** non è più disponibile, è possibile fare clic su **Avanti**. 

     ![Contratto di licenza di Python](media/2017setup-python-license.png "contratto di licenza di Python")

6.  Nella pagina **Inizio installazione** verificare le opzioni selezionate e fare clic su **Installa**.

Al termine dell'installazione, vedere [report personalizzati per SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md) per informazioni su eventuali errori o avvisi, vedere [aggiornamento e installazione domande frequenti: servizi di Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md).
::: moniker-end

::: moniker range="=sql-server-2016"
## <a name="run-setup"></a>Esecuzione del programma di installazione

Per le installazioni locali è necessario eseguire il programma di installazione come amministratore. Se si installa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio con autorizzazioni di lettura ed esecuzione relative a tale condivisione.

1. Avviare l'installazione guidata.

2. Nel **installazione** scheda, fare clic su **installazione nuovo R Server (Standalone)**.
    
     ![Avviare l'installazione di R Server Standalone](media/2016-setup-installation-rsvr.png "avviare l'installazione di R Server (Standalone)")

3. Al termine del controllo delle regole, accettare le condizioni di licenza di SQL Server e selezionare una nuova installazione.

4.  Nella pagina **Selezione funzionalità** dovrebbe essere già selezionata l'opzione seguente:
    
    **R Server (Standalone)**  
    
    ![Le selezioni per R Server (Standalone) di funzionalità](media/2016setup-rserver-features.png "funzionalità le selezioni per R Server (Standalone)")
    
    Tutte le altre opzioni possono essere ignorate. 
    
    > [!NOTE]
    > Evitare di installare il **Caratteristiche condivise** se si esegue il programma di installazione in un computer in cui è già installato R Services per analitica nel database di SQL Server. Ciò consente di creare librerie duplicate.
    > 
    > Mentre gli script R in esecuzione in SQL Server vengono gestiti da SQL Server a come non in conflitto con la memoria utilizzata da altri servizi del motore di database, la versione autonoma di R Server non dispone di alcun vincolo di questo tipo e può interferire con altre operazioni di database.
    > 
    > È in genere consiglia di installare R Server (Standalone) in un computer distinto da SQL Server R Services (In-Database).

5.  Accettare le condizioni di licenza per il download e installazione di distribuzioni di lingua di base. Quando il pulsante **Accetto** non è più disponibile, è possibile fare clic su **Avanti**. 

6.  Nella pagina **Inizio installazione** verificare le opzioni selezionate e fare clic su **Installa**.

Al termine dell'installazione, vedere [report personalizzati per SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md) per informazioni su eventuali errori o avvisi, vedere [aggiornamento e installazione domande frequenti: servizi di Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md).
::: moniker-end

### <a name="default-installation-folders"></a>Cartelle di installazione predefinito

Per lo sviluppo di R e Python, è comune disporre di più versioni nello stesso computer. Installato dal programma di installazione di SQL Server, la distribuzione di base viene installata in una cartella associata alla versione di SQL Server usata per il programma di installazione.

La tabella seguente elenca i percorsi per le distribuzioni R e Python create da programmi di installazione di Microsoft. Per motivi di completezza, la tabella include percorsi di navigazione generati dal programma di installazione di SQL Server, nonché il programma di installazione autonomo per Microsoft Machine Learning Server.

|Versione| Metodo di installazione | Cartella predefinita|
|----|----|----|
|Machine Learning Server (Standalone) di SQL Server 2017 |  Installazione guidata di SQL Server 2017 |`C:\Program Files\Microsoft SQL Server\140\R_SERVER` <br/>`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Microsoft Machine Learning Server (Standalone) |  Programma di installazione di Windows autonomo |`C:\Program Files\Microsoft\ML Server\R_SERVER`<br/>`C:\Program Files\Microsoft\ML Server\PYTHON_SERVER`|
|SQL Server 2017 Machine Learning Services (In-Database) |Installazione guidata di SQL Server 2017, con l'opzione di linguaggio R|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  <br/>`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |
|R Server (Standalone) di SQL Server 2016 |  Installazione guidata di SQL Server 2016 |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2016 R Services (In-Database) |Installazione guidata di SQL Server 2016|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|

## <a name="development-tools"></a>Strumenti di sviluppo

Un IDE di sviluppo non è installato come parte del programma di installazione. Per altre informazioni su come configurare un ambiente di sviluppo, vedere [configurare gli strumenti R](../r/set-up-a-data-science-client.md) e [configurare gli strumenti Python](../python/setup-python-client-tools-sql.md).

## <a name="next-steps"></a>Passaggi successivi

Gli sviluppatori di R possono iniziare a usare alcuni semplici esempi e informazioni di base del funzionamento di R con SQL Server. Per il passaggio successivo, vedere i collegamenti seguenti:

+ [Esercitazione: Eseguire R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Esercitazione: Nel database analitica per gli sviluppatori di R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Gli sviluppatori di Python è possono imparare a usare Python con SQL Server seguendo queste esercitazioni:

+ [Esercitazione: Eseguire Python in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Esercitazione: Nel database analitica per sviluppatori Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)
::: moniker-end

Per visualizzare esempi di machine learning basate su scenari reali, vedere [di Machine learning esercitazioni](../tutorials/machine-learning-services-tutorials.md).
