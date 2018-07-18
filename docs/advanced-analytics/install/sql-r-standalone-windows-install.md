---
title: Installare SQL Server 2016 R Server (Standalone) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e5457698120536247ad1823b842bb1b8e52b484d
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979283"
---
# <a name="install-sql-server-2016-r-server-standalone"></a>Installare SQL Server 2016 R Server (Standalone)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo descrive come usare il programma di installazione di SQL Server 2016 per installare la versione autonoma di **SQL Server 2016 R Server**.

## <a name="bkmk_prereqs"> </a> Elenco di controllo pre-installazione

SQL Server 2016 è obbligatorio. Se si dispone di SQL Server 2017, installare [Machine Learning Server (Standalone) di SQL Server 2017](sql-machine-learning-standalone-windows-install.md) invece.

Se è installata una qualsiasi versione precedente degli strumenti Revolution Analitica o pacchetti, è necessario prima disinstallarla. 

## <a name="get-the-installation-media"></a>Ottenere il supporto di installazione

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

 ###  <a name="bkmk_ga_instalpatch"></a> Requisito di installazione patch 

Microsoft ha rilevato un problema con una versione specifica dei file binari di Microsoft VC++ 2013 Runtime installati come prerequisito da SQL Server. Se l'aggiornamento dei file binari di VC++ Runtime non viene installato, potrebbero verificarsi problemi di stabilità di SQL Server in determinati scenari. Prima di installare SQL Server, seguire le istruzioni in [Note sulla versione di SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) per vedere se il computer richiede una patch per i file binari di VC++ Runtime.  

## <a name="run-setup"></a>Esecuzione del programma di installazione

Per le installazioni locali è necessario eseguire il programma di installazione come amministratore. Se si installa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio con autorizzazioni di lettura ed esecuzione relative a tale condivisione.

1. Avviare l'installazione guidata di SQL Server 2016. Si consiglia di installare Service Pack 1 o versione successivo.

2. Nel **installazione** scheda, fare clic su **installazione nuovo R Server (Standalone)**.
    
     ![Avviare l'installazione di R Server Standalone](media/2016-setup-installation-rsvr.png "avviare l'installazione di R Server (Standalone)")
    
3.  Nella pagina **Selezione funzionalità** dovrebbe essere già selezionata l'opzione seguente:
    
    **R Server (Standalone)**  
    
    ![Le selezioni per R Server (Standalone) di funzionalità](media/2016setup-rserver-features.png "funzionalità le selezioni per R Server (Standalone)")
    
    Tutte le altre opzioni possono essere ignorate. 
    
    > [!NOTE]
    > Evitare di installare il **Caratteristiche condivise** se si esegue il programma di installazione in un computer in cui è già installato R Services per analitica nel database di SQL Server. Ciò consente di creare librerie duplicate.
    > 
    > Mentre gli script R in esecuzione in SQL Server vengono gestiti da SQL Server a come non in conflitto con la memoria utilizzata da altri servizi del motore di database, la versione autonoma di R Server non dispone di alcun vincolo di questo tipo e può interferire con altre operazioni di database.
    > 
    > È in genere consiglia di installare R Server (Standalone) in un computer distinto da SQL Server R Services (In-Database).

4.  Accettare le condizioni di licenza per il download e l'installazione di Microsoft R Open. Quando il pulsante **Accetto** non è più disponibile, è possibile fare clic su **Avanti**.
    
    Installazione di questi componenti e gli eventuali prerequisiti che potrebbero essere necessari, potrebbe richiedere qualche minuto.
    
5.  Nella pagina **Inizio installazione** verificare le opzioni selezionate e fare clic su **Installa**.

## <a name="default-installation-folders"></a>Cartelle di installazione predefinito

Quando si installa R Server con il programma di installazione di SQL Server, le librerie R vengono installate in una cartella associata alla versione di SQL Server usata per il programma di installazione. In questa cartella si trovano anche i dati di esempio, la documentazione per i pacchetti R di base e la documentazione di runtime e strumenti R.

Tuttavia, se è installato Microsoft R Server con il programma di installazione di Windows separato (non SQL programma di installazione) o se esegue l'aggiornamento usando il programma di installazione di Windows separato, le librerie R vengono installate in una cartella diversa.

Sebbene sia consigliabile contrastarla, se è installata anche un'istanza di SQL Server R Services (In-Database) nello stesso computer, una seconda copia di strumenti e librerie di R vengono installati in una cartella diversa.

La tabella seguente elenca i percorsi per ogni installazione.

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

Un IDE di sviluppo non è installato come parte del programma di installazione. Non sono necessari strumenti aggiuntivi, poiché tutti gli strumenti standard sono inclusi che verrebbe fornito con una distribuzione di R o Python.

Si consiglia di provare la nuova versione di [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] oppure [Python per Visual Studio](https://docs.microsoft.com/visualstudio/python/installing-python-support-in-visual-studio). Visual Studio supporta sia R e Python, nonché strumenti di sviluppo di database, la connettività con SQL Server e strumenti di Business Intelligence. Tuttavia, è possibile usare qualsiasi ambiente di sviluppo preferito, inclusi RStudio.
  
## <a name="get-help"></a>Supporto

Serve aiuto con l'installazione o aggiornamento? Per le risposte alle domande più frequenti e problemi noti, vedere l'articolo seguente:

* [Aggiornamento e installazione domande frequenti: servizi di Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Per controllare lo stato dell'installazione dell'istanza e risolvere problemi comuni, provare questi report personalizzati.

* [Report personalizzati per SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Passaggi successivi

Gli sviluppatori di R possono iniziare a usare alcuni semplici esempi e informazioni di base del funzionamento di R con SQL Server. Per il passaggio successivo, vedere i collegamenti seguenti:

+ [Esercitazione: Eseguire R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).
+ [Esercitazione: Nel database analitica per gli sviluppatori di R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Per visualizzare esempi di machine learning basate su scenari reali, vedere [di Machine learning esercitazioni](../tutorials/machine-learning-services-tutorials.md).

