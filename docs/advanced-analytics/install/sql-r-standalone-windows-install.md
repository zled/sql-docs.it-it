---
title: Installare SQL Server 2016 R Server (Standalone) | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e7e5b61cb8e41d818fc13d1cc97cd4d998256efc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32447165"
---
# <a name="install-sql-server-2016-r-server-standalone"></a>Installare SQL Server 2016 R Server (Standalone)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo viene descritto come utilizzare il programma di installazione di SQL Server 2016 per installare la versione autonoma di **Server di SQL Server 2016 R**.

## <a name="bkmk_prereqs"> </a> Elenco di controllo pre-installazione

SQL Server 2016 è obbligatorio. Se si dispone di SQL Server 2017, installare [Machine Learning Server (Standalone) di SQL Server 2017](sql-machine-learning-standalone-windows-install.md) invece.

Se è installata una qualsiasi versione precedente degli strumenti di Revolution Analitica o pacchetti, è necessario disinstallarle prima di tutto. 

## <a name="get-the-installation-media"></a>Ottenere il supporto di installazione

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

 ###  <a name="bkmk_ga_instalpatch"></a> Requisito di installazione patch 

Microsoft ha rilevato un problema con una versione specifica dei file binari di Microsoft VC++ 2013 Runtime installati come prerequisito da SQL Server. Se l'aggiornamento dei file binari di VC++ Runtime non viene installato, potrebbero verificarsi problemi di stabilità di SQL Server in determinati scenari. Prima di installare SQL Server, seguire le istruzioni in [Note sulla versione di SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) per vedere se il computer richiede una patch per i file binari di VC++ Runtime.  

## <a name="run-setup"></a>Esecuzione del programma di installazione

Per le installazioni locali è necessario eseguire il programma di installazione come amministratore. Se si installa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio con autorizzazioni di lettura ed esecuzione relative a tale condivisione.

1. Avviare Installazione guidata di SQL Server 2016. Si consiglia di installare Service Pack 1 o versione successivo.

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
    > In genere si consiglia di installare R Server (Standalone) in un computer diverso da SQL Server R Services (In-Database).

4.  Accettare le condizioni di licenza per il download e l'installazione di Microsoft R Open. Quando il pulsante **Accetto** non è più disponibile, è possibile fare clic su **Avanti**.
    
    Installazione di questi componenti e gli eventuali prerequisiti che necessari, potrebbe richiedere qualche istante.
    
5.  Nella pagina **Inizio installazione** verificare le opzioni selezionate e fare clic su **Installa**.

## <a name="default-installation-folders"></a>Cartelle di installazione predefinito

Quando si installa R Server tramite l'installazione di SQL Server, le librerie di R vengono installate in una cartella associata alla versione di SQL Server utilizzato per l'installazione. In questa cartella, si trovano anche dati di esempio, alla documentazione per i pacchetti di base di R e documentazione di strumenti di R e runtime.

Tuttavia, se è installato Microsoft R Server utilizzando il programma di installazione di Windows separato (non l'installazione di SQL) o se si esegue l'aggiornamento utilizzando il programma di installazione di Windows separato, le librerie di R vengono installate in una cartella diversa.

Sebbene sia consigliabile su di essa, se è installato anche un'istanza di SQL Server con R Services (In-Database) nello stesso computer, una seconda copia di strumenti e librerie di R vengono installati in una cartella diversa.

Nella tabella seguente sono elencati i percorsi per ogni installazione.

|Versione| Metodo di installazione | Cartella predefinita|
|----|----|----|
|R Server (Standalone) |Installazione guidata di SQL Server 2016|`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|R Server (Standalone) |Programma di installazione di Windows autonomo|`C:\Program Files\Microsoft\R Server\R_SERVER`|
|Machine Learning Server (Standalone) |  Installazione guidata di SQL Server 2017, con l'opzione di linguaggio R |`C:\Program Files\Microsoft SQL Server\140\R_SERVER`|
|Machine Learning Server (Standalone) |  Installazione guidata di SQL Server 2017, con l'opzione di linguaggio Python |`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Machine Learning Server (Standalone) |  Programma di installazione di Windows autonomo |`C:\Program Files\Microsoft\R Server\R_SERVER`|
|R Services (In-Database) |Installazione guidata di SQL Server 2016|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|
|Machine Learning Services (In-Database) |Installazione guidata di SQL Server 2017, con l'opzione di linguaggio R|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  |
|Machine Learning Services (In-Database) |Installazione guidata di SQL Server 2017, con l'opzione di linguaggio Python| `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |

## <a name="development-tools"></a>Strumenti di sviluppo

Sviluppo IDE non è installato come parte del programma di installazione. Strumenti aggiuntivi non sono necessari, come tutti gli strumenti standard sono inclusi che sarebbero forniti con una distribuzione di R o Python.

È consigliabile provare la nuova versione di [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] oppure [Python per Visual Studio](https://docs.microsoft.com/en-us/visualstudio/python/installing-python-support-in-visual-studio). Visual Studio supporta sia R e Python, nonché strumenti di sviluppo di database, la connettività con SQL Server e strumenti di Business Intelligence. Tuttavia, è possibile utilizzare qualsiasi ambiente di sviluppo preferito tra RStudio.
  
## <a name="get-help"></a>Supporto

Assistenza sull'installazione o aggiornamento? Per le risposte alle domande più comuni e i problemi noti, vedere l'articolo seguente:

* [Aggiornamento e l'installazione domande frequenti - servizi di Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Per controllare lo stato di installazione dell'istanza e risolvere i problemi comuni, provare a questi report personalizzati.

* [Report personalizzati per SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Passaggi successivi

Gli sviluppatori R possono iniziare a usare alcuni semplici esempi e apprendere le nozioni di base del funzionamento di R con SQL Server. Per il passaggio successivo, vedere i collegamenti seguenti:

+ [Esercitazione: Esecuzione di R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).
+ [Esercitazione: In-database analitica per gli sviluppatori R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Per visualizzare esempi di machine learning basato su scenari reali, vedere [Machine learning esercitazioni](../tutorials/machine-learning-services-tutorials.md).

