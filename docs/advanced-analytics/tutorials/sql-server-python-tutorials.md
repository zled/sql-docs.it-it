---
title: Esercitazioni di SQL Server Python | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 541675c22ddbe347f67119d8cba82f75955382e6
ms.sourcegitcommit: ce4b39bf88c9a423ff240a7e3ac840a532c6fcae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2018
ms.locfileid: "48877985"
---
# <a name="sql-server-python-tutorials"></a>Esercitazioni di SQL Server Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fornisce un elenco di esercitazioni ed esempi che illustrano l'uso di Python con SQL Server 2017. Tramite questi esempi e demo, si apprenderà:

+ Come eseguire Python da T-SQL
+ Che cosa sono i contesti di calcolo remoti e locali e come è possibile eseguire codice Python usando il computer SQL Server
+ Come eseguire il wrapping di codice Python in una stored procedure
+ Ottimizzazione del codice Python per un ambiente di produzione di SQL
+ Scenari reali per l'incorporamento nelle applicazioni di apprendimento automatico

Per informazioni sui requisiti e il programma di installazione, vedere [prerequisiti](#bkmk_Prerequisites).

## <a name="bkmk_pythontutorials"></a>Esercitazioni su Python

+ [Esecuzione di Python in T-SQL](run-python-using-t-sql.md)

   Informazioni di base di come chiamare Python in T-SQL, mediante il meccanismo di estendibilità introdotti in SQL Server 2016.

+ [Creare un modello di machine learning in Python usando revoscalepy](use-python-revoscalepy-to-create-model.md)

   In questa lezione viene illustrato come è possibile eseguire codice da un terminale Python remoto usando il contesto di calcolo di SQL Server. Verrà visualizzata una certa familiarità con gli ambienti e gli strumenti Python. Codice di esempio viene specificato che crea un modello utilizzando **rxLinMod**, dalla nuova **revoscalepy** libreria. 

+ [Analitica di Python nel Database per sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md)

    Questa procedura dettagliata end-to-end viene illustrato il processo di compilazione di una soluzione completa di Python tramite le procedure di T-SQL archiviate. Tutto il codice Python è incluso.


## <a name="python-samples"></a>Esempi di Python

Questi esempi e demo fornite dal team di sviluppo di SQL Server evidenziano che modo è possibile usare analitica incorporata in applicazioni reali.

+ [Creare un modello predittivo usando Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

  Informazioni su come un noleggio di sci potrebbe usare machine learning per prevedere i noleggi futuri, che consente al piano aziendale e personale per soddisfare la domanda futura.

  > [!TIP]
  > Include ora l'assegnazione dei punteggi nativa da modelli di Python.

+ [Clienti di eseguire il clustering con Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Informazioni su come usare l'algoritmo Kmeans per eseguire il clustering non supervisionato dei clienti.

## <a name="bkmk_Prerequisites"></a>Prerequisiti

Per usare queste esercitazioni, è necessario disporre di SQL Server 2017 ed è necessario installare in modo esplicito e quindi abilitare la funzionalità di Machine Learning Services (In-Database). 

SQL Server 2017 supporta i linguaggi R e Python, ma non è installato o abilitato per impostazione predefinita. Esecuzione di Python, è necessario che siano abilitati il framework di estendibilità e selezionare Python come lingua da installare. 

### <a name="post-installation-configuration-tips"></a>Suggerimenti relativi alla configurazione post-installazione

Dopo aver eseguito il programma di installazione di SQL Server, potrebbe essere necessario eseguire alcuni passaggi aggiuntivi per garantire che di comunicazione Python e SQL Server:

+ Abilitare la funzionalità di esecuzione di script esterni eseguendo `sp_configure 'external scripts enabled', 1`.
+ Riavviare il server. 
+ Aprire il **Services** pannello per verificare se Launchpad è stata avviata. 
+ Assicurarsi che il servizio che chiama il runtime esterno disponga delle autorizzazioni necessarie. Per altre informazioni, vedere [abilitare l'autenticazione implicita](../security/add-sqlrusergroup-to-database.md).
+ Aprire una porta nel firewall per SQL Server e abilitare protocolli di rete necessari.
+ Assicurarsi che l'account di accesso SQL o un account utente di Windows disponga delle autorizzazioni necessarie per connettersi al server, per leggere i dati e creare gli oggetti di database necessari dall'esempio.

Vedere questo articolo per alcuni problemi comuni: [risoluzione dei problemi di servizi di Machine Learning](../machine-learning-troubleshooting-faq.md)

### <a name="resource-management"></a>Gestione delle risorse

È possibile installare R e Python nello stesso computer, ma entrambi in esecuzione può richiedere notevoli risorse. Se si verificano errori di "memoria insufficiente" o se l'esecuzione di processi di machine learning è che il principale utilizzo previsto di server, è possibile ridurre la quantità di memoria allocata al motore di database. Per altre informazioni, vedere [Managing and monitoring di Python in SQL Server](../python/managing-and-monitoring-python-solutions.md).

## <a name="see-also"></a>Vedere anche

[Esercitazioni di R per SQL Server](sql-server-r-tutorials.md)
